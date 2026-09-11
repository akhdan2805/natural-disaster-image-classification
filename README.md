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

### **1. Configuration**
- **Dataset Path:** Google Drive
- **Classes:** Earthquake, Land_Slide, Urban_Fire, Water_Disaster
- **Image Size:** 224 × 224 pixels
- **Batch Size:** 32
- **Random Seed:** 42

### **2. Exploratory Data Analysis & Data Preprocessing**  
The dataset was cleaned by removing duplicate, corrupted, empty, and irrelevant images identified through the exploratory analysis. In addition, 19 irrelevant images were manually removed based on the RGB outlier analysis to improve data quality. The images were then prepared for standardized processing at a size of **224 × 224 pixels** while preserving their original aspect ratio through cropping.

### **3. Data Loading**
The cleaned images were loaded into Google Colab and converted into a TensorFlow dataset using an image size of **224 × 224 pixels** and a **batch size of 32**. To preserve the original proportions of the images, cropping was applied during the loading process using aspect ratio preservation. This ensured that the images were standardized without introducing significant visual distortion.

### **4. Data Splitting**
The dataset was divided into three subsets: **70% for training, 15% for validation, and 15% for testing**. The training set was used to learn visual patterns from the disaster images, while the validation set was used to monitor model performance during training. The remaining test set was reserved for final evaluation using images that had not been seen by the model during training. The training data was also reshuffled at each epoch to prevent the model from learning patterns based on the original sample order.

### **5. Data Augmentation**
The training images were normalized by rescaling pixel values from **0–255 to 0–1**. To increase data variability and improve model generalization, augmentation techniques were applied exclusively to the training set, including **horizontal flipping, rotation up to 10%, and zooming up to 10%**. No augmentation was applied to the validation and test sets to preserve the integrity of the evaluation data. TensorFlow `AUTOTUNE` and prefetching were also used to improve the efficiency of the data pipeline.
