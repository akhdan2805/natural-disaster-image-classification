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
The project consists of five main stages:

**1. Configuration**
- **Dataset Path:** Google Drive
- **Classes:** Earthquake, Land_Slide, Urban_Fire, Water_Disaster
- **Image Size:** 224 × 224 pixels
- **Batch Size:** 32
- **Random Seed:** 42

**1. Data Preprocessing**  
Images were cleaned, resized, normalized, and organized into four disaster categories: Earthquake, Urban Fire, Land Slide, and Water Disaster.

**2. Data Augmentation**  
Image augmentation was applied to the training data to increase image diversity and improve model generalization.

**3. Model Development**  
A CNN-based **EfficientNetB1** architecture was used to perform multi-class image classification.

**4. Model Training**  
The model was trained on the prepared dataset while monitoring training and validation performance.

**5. Model Evaluation**  
Model performance was evaluated using accuracy, precision, recall, F1-score, and confusion matrix.
