# Automated Banana Ripeness Classification using Deep Learning

### Project Overview
In the food and agricultural supply chain, manual sorting of fruit is labor-intensive, slow, and prone to human error. This project automates the quality control process by using Computer Vision to classify the ripeness of bananas into four distinct categories: **Unripe, Ripe, Overripe, and Rotten**.

### Food Engineering Context
* **Waste Reduction:** Early detection of "Rotten" samples prevents the spread of spoilage to healthy batches during transit.
* **Supply Chain Optimization:** Identifying exact ripeness stages helps distributors decide which batches to ship to local supermarkets immediately and which to store or ship further away.

### Dataset & Preprocessing
* The model was trained on an image dataset containing **11,783 training images**, **1,121 validation images**, and **561 test images**.
* Images were resized to `224x224` pixels and pixel values were normalized (rescaled by `1./255`) to improve training convergence.

### Model Architecture
The project utilizes a custom Convolutional Neural Network (CNN) built with TensorFlow/Keras.
* **3 Convolutional Blocks:** (32, 64, and 128 filters) with ReLU activation and MaxPooling for feature extraction.
* **Fully Connected Layer:** A Dense layer of 512 units with a 50% Dropout rate to prevent overfitting.
* **Output Layer:** A Softmax layer categorizing the 4 ripeness classes.

### Results
After training for 10 epochs, the model was evaluated on completely unseen test data, achieving:
* **Final Test Accuracy:** 96.26%
* **Final Test Loss:** 0.1534