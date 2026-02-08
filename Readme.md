# Synthetic-to-Real Transfer for Wafer Defect Classification

This repository explores wafer defect classification using convolutional neural networks (CNNs), with the main aim of understanding how synthetic data differs from real-world semiconductor inspection data.

The project studies the advantages and limitations of training models on synthetically generated wafer maps and demonstrates how fine-tuning on real data helps bridge the gap between idealized synthetic patterns and noisy real-world defects.

## Problem Overview

In semiconductor manufacturing, wafers often exhibit defects with strong geometric patterns that can be learned using machine learning. However, collecting large, labeled real-world datasets is expensive and often limited.

This project investigates:
- Whether synthetic wafer data can be used to pretrain defect classification models to reduce reliance on large real datasets
- How well models trained on synthetic data generalize to real wafer defect data
- How fine-tuning pretrained models with real data improves performance and corrects domain mismatch

## Dataset

### Real Data
- Public wafer defect dataset: **LSWMD (Large-Scale Wafer Map Dataset)**

### Synthetic Data
- Programmatically generated wafer maps with controllable defect geometries:
  - Center
  - Donut
  - Edge-Loc
  - Edge-Ring
  - Scratch
  - Random
  - Near-full
  - None

## Methodology

Three CNN-based models were trained and compared:

### 1. Real-only Model
- Trained and evaluated directly on the public wafer dataset

### 2. Synthetic-only Model
- Trained on synthetic wafer maps
- Evaluated on both synthetic validation data and real wafer data

### 3. Synthetic + Fine-Tuned Model
- Pretrained on synthetic data
- Fine-tuned on real wafer data to adapt to real-world variability

## How to Run

### 1. Dataset Setup
The dataset is not included in this repository due to size constraints.

- Download the **Large-Scale Wafer Map Dataset (LSWMD)** as a ZIP file
- Extract and place the dataset inside the `dataset/` directory
- Update dataset paths inside the notebooks if required

### 2. Notebooks Overview

- **`Real_data_defect_detector.ipynb`**  
  Trains and evaluates a CNN model directly on real wafer defect data.

- **`synthetic-wafer-detection.ipynb`**  
  Generates synthetic wafer maps, trains a CNN on synthetic data, and fine-tunes the model on real wafer data to study synthetic-to-real transfer.

### 3. Pretrained Models
Trained model checkpoints are available in the `models/` directory and can be loaded directly for evaluation without retraining.

## Key Observations

- Models trained only on synthetic data achieved high accuracy on synthetic validation data but performed poorly on real wafer data, revealing a clear gap between synthetic and real distributions caused by overly idealized synthetic patterns.
- Fine-tuning synthetic-pretrained models on real data significantly improved performance on real wafers, particularly for geometry-driven defect classes such as **Center** and **Donut**.
- The results highlight both the advantages (cheap, structured pretraining) and limitations (idealized patterns) of synthetic data generation for industrial inspection tasks.

## Future Work

- Improve synthetic data realism by incorporating noise and variability models
- Explore class-weighted loss functions for rare defect types

## Author

**Pranav Jigar Thakkar**  
Dual Major in Artificial Intelligence & Mechanical Engineering  
IIT Gandhinagar
