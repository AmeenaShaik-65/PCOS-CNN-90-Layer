# PCOS Detection Using 90-Layer CNN

## Overview

This project presents a deep learning-based approach for detecting Polycystic Ovary Syndrome (PCOS) from ovarian ultrasound images using a custom **90-layer Convolutional Neural Network (CNN)**.

The proposed model uses a **pre-trained ResNet50 architecture as the deep CNN backbone**, with an additional convolutional layer and classification layers added to perform binary classification between **PCOS** and **Non-PCOS** images.

The project also compares the proposed model with several transfer-learning architectures, including **ResNet50, MobileNet, VGG, and InceptionV3**.

## Objectives

* Develop a deep learning model for PCOS image classification.
* Build a 90-layer CNN-based architecture using ResNet50 as the backbone.
* Apply image preprocessing and augmentation to improve model generalization.
* Compare the proposed model with established CNN architectures.
* Evaluate model performance using accuracy, precision, recall, and F1-score.
* Save and test the trained model on new ultrasound images.

## Dataset

The dataset contains two image classes:

| Class     | Number of Images |
| --------- | ---------------: |
| PCOS      |              781 |
| Non-PCOS  |            1,142 |
| **Total** |        **1,923** |

The dataset was divided into training, validation, and testing subsets using a **70% / 15% / 15% split**.

### Dataset Split

| Class    | Training | Validation | Testing |
| -------- | -------: | ---------: | ------: |
| PCOS     |      546 |        117 |     118 |
| Non-PCOS |      799 |        171 |     172 |

The original image dataset is not included in this repository.

## Data Preprocessing

Images are resized to **224 × 224 pixels** and normalized by scaling pixel values to the range 0–1.

Training images are augmented using:

* Rotation
* Zoom
* Width shifting
* Height shifting
* Shearing
* Horizontal flipping

Validation images are only normalized without augmentation.

## Proposed 90-Layer CNN

The proposed architecture is built using **ResNet50 with ImageNet pre-trained weights** as the backbone.

The ResNet50 base layers are frozen, and additional layers are added for PCOS classification:

* ResNet50 deep CNN backbone
* Additional Conv2D layer with 64 filters
* Batch Normalization
* Global Average Pooling
* Dense layer with 128 neurons
* Dropout (0.6)
* Sigmoid output layer for binary classification

The model is compiled using the **Adam optimizer** with a learning rate of `1e-4` and **binary cross-entropy loss**.

## Model Training

The proposed model was trained for **5 epochs** using:

* Image size: 224 × 224
* Batch size: 2
* Optimizer: Adam
* Learning rate: 0.0001
* Loss function: Binary Cross-Entropy
* Evaluation metric: Accuracy

The model achieved a maximum validation accuracy of **100% during training**, while the final validation evaluation reported an accuracy of approximately **98.26%**.

## Model Comparison

The project experiments with multiple CNN architectures:

* Proposed 90-Layer CNN
* ResNet50
* MobileNet
* VGG
* InceptionV3

These models are evaluated on the validation dataset to compare their classification performance.

## Prediction

The trained 90-layer CNN can be used to classify a new ultrasound image.

The prediction pipeline:

1. Upload an image.
2. Resize the image to 224 × 224.
3. Normalize pixel values.
4. Pass the image through the trained CNN.
5. Generate a probability using the sigmoid output.
6. Classify the image as **PCOS Detected** or **NOT PCOS** based on the prediction threshold.

## Model Output

The trained model is saved in Keras format:

```text
models/pcos_cnn_90.keras
```

A TensorFlow SavedModel version is also exported for serving/inference.

## Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* Google Colab
* ResNet50
* MobileNet
* VGG
* InceptionV3

## Evaluation Metrics

The project includes evaluation using:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

These metrics are used to analyze the classification performance of the proposed CNN model.

## Repository Structure

```text
PCOS-CNN-90-Layer/
│
├── PCOS_CNN_90_Layer.ipynb
├── README.md
│
├── models/
│   └── pcos_cnn_90.keras
│
└── results/
    └── evaluation_results
```

> The dataset is not included in the repository due to its size. The notebook contains the dataset loading, preprocessing, splitting, training, evaluation, and prediction workflow.

## Disclaimer

This project is intended for **research and educational purposes only**. The model output should not be considered a medical diagnosis or a substitute for professional medical evaluation.
