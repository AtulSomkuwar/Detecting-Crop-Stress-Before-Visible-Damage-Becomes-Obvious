## Detecting-Crop-Stress-Before-Visible-Damage-Becomes-Obvious

<img width="1441" height="811" alt="Screenshot 2026-10-25 235853" src="https://github.com/user-attachments/assets/8c4ec69a-a843-4009-a9c2-88dacc8b1cb5" />

# Early Crop Nutrient Stress Detection Using Deep Learning

## Project Overview

This project explores the use of deep learning and computer vision to classify crop health conditions from leaf images. The main objective is to investigate how different CNN architectures and color-space representations affect the classification of healthy leaves and leaves labelled with nitrogen or potassium deficiency.

Instead of relying on a single model or standard RGB images, the project compares multiple architectures and color representations to identify promising combinations for crop-health classification.

## Dataset

The dataset contains 2,700 images divided into three subsets:

- Training: 1,890 images
- Validation: 405 images
- Testing: 405 images

The classification task includes nine categories across three crops:

- Ash gourd: fresh, nitrogen deficiency, potassium deficiency
- Bitter gourd: fresh, nitrogen deficiency, potassium deficiency
- Snake gourd: fresh, nitrogen deficiency, potassium deficiency

Model inputs in the relevant experiments are resized to 312 × 312 pixels.

## Models Evaluated

Three CNN architectures are explored:

- MobileNetV2
- EfficientNetB0
- DenseNet121

## Color Representations

The experiments compare four color representations:

- RGB
- HSV
- CIELUV
- Nutrispace, a custom color transformation used in this project

The aim is to understand whether alternative color representations can help models learn useful visual patterns for crop-health classification.

## Training and Evaluation

The notebook includes dataset loading and preprocessing, transfer learning, fine-tuning, model regularization, learning-rate scheduling, checkpointing, and model evaluation. The evaluation workflow includes held-out testing and individual-image predictions.

Additional experiments use PCA and K-means clustering to explore the feature representations learned by selected models.

## Key Result

The strongest identified result in the recorded experiments was obtained using CIELUV with EfficientNetB0:

- Validation accuracy: 88.40%
- Test accuracy: 86.91%

This result suggests that the choice of color representation may influence crop-image classification performance. Further controlled experiments are required to isolate the effect of color space and validate the approach on independent field data.

## Complete accuracy comparison

Color space	Model	Best validation accuracy	Test accuracy	Macro F1
RGB	MobileNetV2	83.95%	79.26%	79.00%
RGB	EfficientNetB0	83.70%	80.25%	80.04%
RGB	DenseNet121	78.77%	80.49%	80.53%
HSV	MobileNetV2	78.52%	78.27%	78.26%
HSV	EfficientNetB0	80.49%	84.44%	84.36%
HSV	DenseNet121	71.36%	75.56%	75.57%
CIELUV	MobileNetV2	83.21%	80.74%	80.73%
CIELUV	EfficientNetB0	88.40%	86.91%	86.80%
CIELUV	DenseNet121	82.47%	78.27%	78.48%
Nutrispace	MobileNetV2	81.98%	82.47%	82.54%
Nutrispace	EfficientNetB0	74.32%	75.80%	75.55%
Nutrispace	DenseNet121	84.44%	83.95%	83.93%

## Technologies

Python, TensorFlow/Keras, OpenCV, NumPy, Matplotlib, scikit-learn, CNNs, transfer learning, PCA, and K-means clustering.

