# 🍌 Automated Banana Ripeness Classification using Deep Learning

![Python](https://img.shields.io/badge/Python-3.10-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## Project Overview

In the food and agricultural supply chain, manual sorting of fruit is labor-intensive, slow, and prone to human error. This project automates the quality control process by using Computer Vision to classify the ripeness of bananas into four distinct categories: **Unripe, Ripe, Overripe, and Rotten**.

## Food Engineering Context

- **Waste Reduction:** Early detection of "Rotten" samples prevents the spread of spoilage to healthy batches during transit.
- **Supply Chain Optimization:** Identifying exact ripeness stages helps distributors decide which batches to ship to local supermarkets immediately and which to store or ship further away.

## Results

| Metric | Value |
|---|---|
| **Test Accuracy** | **96.26%** |
| Test Loss | 0.1534 |
| Epochs | 10 |

### Training Curves
![Training Curves](assets/training_curves.png)

### Confusion Matrix
![Confusion Matrix](assets/confusion_matrix.png)

### Sample Prediction
![Sample Prediction](assets/sample_prediction.png)

## Dataset & Preprocessing

- **Source:** [Banana Ripeness Classification Dataset (Kaggle)](https://www.kaggle.com/datasets/)
- The model was trained on an image dataset containing **11,783 training images**, **1,121 validation images**, and **561 test images**.
- Images were resized to `224x224` pixels and pixel values were normalized (rescaled by `1./255`).
- **Augmentation** (rotation, zoom, horizontal flip, shear) was applied to the training set to improve generalization.

**Expected folder structure after downloading the dataset:**
```
Banana Ripeness Classification Dataset/
├── train/
│   ├── overripe/
│   ├── ripe/
│   ├── rotten/
│   └── unripe/
├── valid/
└── test/
```

## Model Architecture

A custom Convolutional Neural Network (CNN) built with TensorFlow/Keras:

- **3 Convolutional Blocks:** (32, 64, and 128 filters) with ReLU activation and MaxPooling for feature extraction.
- **Fully Connected Layer:** A Dense layer of 512 units with a 50% Dropout rate to prevent overfitting.
- **Output Layer:** A Softmax layer categorizing the 4 ripeness classes.

## Repository Structure

```
Banana-Ripeness-Classification/
├── notebooks/
│   └── Banana_Ripeness_Classification.ipynb   # Training, evaluation, prediction
├── assets/
│   ├── training_curves.png
│   ├── confusion_matrix.png
│   └── sample_prediction.png
├── requirements.txt
├── LICENSE
└── README.md
```

## Usage

### 1. Clone the repo
```bash
git clone https://github.com/aia-Arif/Banana-Ripeness-Classification.git
cd Banana-Ripeness-Classification
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Download the dataset from Kaggle (link above) and place it in the project root, matching the folder structure shown.

### 4. Run the notebook
```bash
jupyter notebook notebooks/Banana_Ripeness_Classification.ipynb
```

### 5. Predict on a new image
```python
from tensorflow.keras.models import load_model
model = load_model('banana_ripeness_model.keras')
result = predict_banana('path/to/your/banana.jpg', model, CLASS_LABELS)
```

## Future Improvements

- Transfer learning (MobileNetV2 / EfficientNet) for higher accuracy with fewer epochs
- Learning rate scheduling and early stopping
- Grad-CAM visualizations to interpret which image regions drive predictions
- Deployment as a lightweight API or mobile app for real-time sorting

## License

This project is licensed under the [MIT License](LICENSE). The dataset belongs to its respective Kaggle author — please review the dataset's license before reuse.
