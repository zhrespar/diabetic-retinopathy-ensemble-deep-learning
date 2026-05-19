# Diabetic Retinopathy Stage Classification using Deep Learning Ensemble

## Overview

This project presents an automated diabetic retinopathy (DR) staging system based on retinal fundus images using deep learning and ensemble learning techniques.

The system combines multiple state-of-the-art architectures including:

- ConvNeXt-Small
- EfficientNetV2-S
- EfficientNet-B3
- Swin Transformer Tiny

to classify diabetic retinopathy into five severity levels:

| Class | Description |
|---------|------------|
| 0 | No DR |
| 1 | Mild DR |
| 2 | Moderate DR |
| 3 | Severe DR |
| 4 | Proliferative DR |

The project was developed within the scope of the TÜBİTAK 2209-A Undergraduate Research Project Program.

---

## Project Goal

Diabetic Retinopathy is one of the leading causes of preventable blindness worldwide.

The primary objective of this project is to develop a reliable computer-aided diagnosis system capable of automatically detecting and staging diabetic retinopathy from retinal fundus images.

---

## Dataset

Dataset used:

- EyePACS Diabetic Retinopathy Detection Dataset
- Source: Kaggle

Approximately:

- 35,000 retinal fundus images
- 5 disease severity classes

Dataset distribution:

| Split | Images |
|---------|---------|
| Train | 28,100 |
| Validation | 7,026 |
| Total | 35,126 |

---

## Data Preprocessing

The following preprocessing techniques were applied:

- RGB conversion
- Image resizing (224×224 and 384×384)
- ImageNet normalization
- Stratified train-validation split

### Data Augmentation

To improve model generalization:

- Random Horizontal Flip
- Random Rotation
- Color Jitter
- CLAHE
- Random Gamma
- Random Resized Crop
- Gaussian Noise

---

## Handling Class Imbalance

The EyePACS dataset contains severe class imbalance.

The following techniques were used:

- Class-Balanced Focal Loss
- Weighted Random Sampling
- Mixup Augmentation (α = 0.2)

---

## Model Development Process

### Stage 1 — Baseline CNN Models

- ResNet50
- DenseNet121
- DenseNet169
- InceptionV3
- Xception

Performance:

- Accuracy ≈ 0.78
- QWK ≈ 0.60–0.68

---

### Stage 2 — Modern Architectures

- Swin Transformer Tiny
- EfficientNet-B3

Performance:

- QWK ≈ 0.70

Initial Ensemble:

- QWK ≈ 0.72

---

### Stage 3 — Advanced Pipeline

Advanced training strategy:

- AdamW Optimizer
- Cosine Annealing Scheduler
- Early Stopping
- Advanced Augmentation
- Class-Balanced Learning

Models:

- ConvNeXt-Small
- EfficientNetV2-S
- EfficientNet-B3
- Swin-Tiny

---

## Ensemble Strategy

Weighted softmax fusion:

| Model | Weight |
|---------|---------|
| ConvNeXt-Small | 50% |
| EfficientNetV2-S | 30% |
| EfficientNet-B3 | 15% |
| Swin-Tiny | 5% |

Final prediction:

1. Weighted softmax averaging
2. Expected value computation
3. Ordinal threshold optimization

---

## Final Results

| Metric | Score |
|----------|---------|
| Accuracy | 0.90 |
| Balanced Accuracy | 0.78 |
| Macro F1 Score | 0.76 |
| Weighted F1 Score | 0.88 |
| Precision (Macro) | 0.77 |
| Recall (Macro) | 0.75 |
| Quadratic Weighted Kappa (QWK) | **0.93** |

---

## Project Structure

```bash
├── notebooks/
│   ├── train.ipynb
│   ├── evaluation.ipynb
│   └── ensemble.ipynb
│
├── src/
│   ├── dataset.py
│   ├── train.py
│   ├── evaluate.py
│   ├── ensemble.py
│   └── utils.py
│
├── figures/
│   ├── confusion_matrix.png
│   ├── roc_curve.png
│   ├── pr_curve.png
│   └── training_curves.png
│
├── models/
│   └── pretrained_weights/
│
├── requirements.txt
└── README.md
```

## Installation

```bash
git clone https://github.com/USERNAME/diabetic-retinopathy-ensemble-deep-learning.git

cd diabetic-retinopathy-ensemble-deep-learning

pip install -r requirements.txt
```

---

## Training

```bash
python src/train.py
```

---

## Evaluation

```bash
python src/evaluate.py
```

---

## Technologies Used

- Python
- PyTorch
- OpenCV
- NumPy
- Pandas
- Scikit-Learn
- Google Colab
- Jupyter Notebook

---

## Applications

Potential applications include:

- Clinical Decision Support Systems
- Automated DR Screening
- Telemedicine Platforms
- Medical AI Research

---

## Authors

**Zahra Esparghami**

Computer Engineering Department

Biruni University

---

## Supervisor

**Prof. Dr. Özgür Koray Şahingöz**

Biruni University

---

## License

This project is developed for academic and research purposes.
