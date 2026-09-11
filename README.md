# 🌪️ Natural Disaster Image Classification using CNN (EfficientNetB1)

## Objective
This group project focuses on developing and evaluating a deep learning model for natural disaster image classification. Using EfficientNetB1, a CNN-based architecture, the project covers data preprocessing, model training, and evaluation using classification metrics to assess model performance.

## Table of Content
- [Dataset Used](#dataset-used)
- [Methodology](#methodology)

## Dataset Used
The dataset was sourced from the [Disaster Images Dataset](https://www.kaggle.com/datasets/varpit94/disaster-images-dataset) on Kaggle.

For this project, four disaster categories were selected:

| Category | Description | Data Amount |
|---|---|---|
| Earthquake | Images depicting earthquake-related scenes | 36 |
| Urban Fire | Images depicting fires in urban environments | 419 |
| Land Slide | Images depicting landslide events | 456 |
| Water Disaster | Images depicting water-related disasters | 1035 |

A total of **1,946 images** were used across these four categories for model training and evaluation.

## Methodology

### 1. Configuration
The dataset path, target classes, image size of **224 × 224 pixels**, batch size of **32**, and random seed of **42** were configured for consistent data processing.

### 2. Data Preparation
The dataset was explored and cleaned by removing duplicate, corrupted, empty, and irrelevant images. Images were loaded into a TensorFlow pipeline, cropped to preserve their aspect ratio, and split into **70% training, 15% validation, and 15% testing**.

### 3. Data Augmentation
Training images were normalized and augmented using horizontal flipping, rotation, and zooming to improve model generalization. Augmentation was applied only to the training set.

### 4. Model Development
Two approaches were developed and compared: a **CNN Scratch Model** and an **EfficientNetB1 Transfer Learning Model**. To address the severe class imbalance, both models were trained using **Class Weight** and **Oversampling** strategies.

### 5. Model Evaluation
The models were evaluated on the unseen test set using **Accuracy, Precision, Recall, F1-Score, and Confusion Matrix**, with **Macro F1-Score** emphasized due to the imbalanced class distribution.
