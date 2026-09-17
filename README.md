# 🌪️ Natural Disaster Image Classification using CNN (EfficientNetB1)

Full code with the output result: [Code with Output](https://drive.google.com/file/d/1-5p5aTV1Fdgu5xDm207eoS8GbDBxAe-G/view?usp=sharing).

## Objective
This group project focuses on developing and evaluating a deep learning model for natural disaster image classification. Using EfficientNetB1, a CNN-based architecture, the project covers data preprocessing, model training, and evaluation using classification metrics to assess model performance.

## Table of Content
- [Dataset Used](#dataset-used)
- [Methodology](#methodology)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [Technologies](#technologies)
- [Team](#team)

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




## Model Architecture

### CNN Scratch Model
The first approach was a CNN model built entirely from scratch to classify images into four natural disaster categories: `Earthquake`, `Land_Slide`, `Urban_Fire`, and `Water_Disaster`.

The architecture consists of four hidden layers with **32, 64, 128, and 64 neurons**, using **ReLU activation** to learn visual patterns from the input images. **Max Pooling** was applied to the first three layers to reduce feature dimensions while retaining important visual information. The extracted features were then flattened using a **Flatten layer** before being passed through the subsequent classification layers.

A **Dropout rate of 0.2** was applied to reduce the risk of overfitting. The final output layer consists of **4 neurons with Softmax activation**, producing the probability of each disaster category. The model contains approximately **5.63 million trainable parameters**.

For training, the model used the **Adam optimizer** with a learning rate of **0.001**, **Sparse Categorical Crossentropy** as the loss function, and **accuracy** as the training metric. Training was performed for a maximum of **50 epochs**, with `ReduceLROnPlateau` and `EarlyStopping` callbacks used to improve training stability and retain the best model weights.

### EfficientNetB1 Transfer Learning

The second approach used **EfficientNetB1** as a pretrained CNN backbone through transfer learning. The base model was pretrained on **ImageNet**, allowing it to leverage previously learned visual features instead of learning all image representations from scratch.

The pretrained EfficientNetB1 weights were **frozen** during training. Several classification layers were added on top of the backbone, starting with **Global Average Pooling** to summarize the extracted feature maps, followed by **Batch Normalization** to improve training stability. A fully connected layer with **128 neurons and ReLU activation** was then added to learn more task-specific representations.

To reduce overfitting, a **Dropout rate of 0.2** was applied before the final classification layer. The output layer contains **4 neurons with Softmax activation** to predict the four disaster categories.

The model was trained using **Adam** with a learning rate of **0.001**, **Sparse Categorical Crossentropy**, and **accuracy** as the metric. Training was limited to a maximum of **50 epochs** and utilized `ReduceLROnPlateau` and `EarlyStopping` to control the learning process and preserve the best-performing weights.




## Results
Four model configurations were evaluated by combining two CNN approaches with two class imbalance handling strategies: **CNN Scratch with Class Weight**, **CNN Scratch with Oversampling**, **EfficientNetB1 with Class Weight**, and **EfficientNetB1 with Oversampling**.

The evaluation focused on **Macro F1-Score** due to the significant class imbalance in the dataset. Among the evaluated approaches, **EfficientNetB1 with Class Weight achieved the best overall performance with a Macro F1-Score of 0.77**.

| Model | Imbalance Handling | Macro F1-Score |
|---|---|---:|
| CNN Scratch | Class Weight | 0.53 |
| CNN Scratch | Oversampling | 0.54 |
| EfficientNetB1 | Oversampling | 0.70 |
| **EfficientNetB1** | **Class Weight** | **0.77** |

The EfficientNetB1 model with Class Weight provided the most stable and balanced performance across the four disaster categories. The results indicate that transfer learning was more effective than training a CNN from scratch for this dataset, particularly under severe class imbalance.




## Technologies
- **Python**
- **TensorFlow / Keras** — CNN, EfficientNetB1, model training, and data pipeline
- **Scikit-learn** — class weight calculation and model evaluation
- **Pandas & NumPy** — data analysis and numerical processing
- **Matplotlib & Seaborn** — data visualization and performance analysis
- **Pillow (PIL)** — image processing and dataset inspection
- **Google Colab** — development and training environment
- **Google Drive** — dataset storage and access




## Team
This project was developed collaboratively by **Muhammad Akhdan Athallah** and **Muhammad Hylmi Razzan** as part of the **Deep Learning** course at Bina Nusantara University.
