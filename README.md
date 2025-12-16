# Deep-Learning-Journey-Ep01

# 🧠 CIFAR-10 Image Classification: From Theory to Robust CNNs

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat&logo=tensorflow)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📖 Introduction
This project documents my journey into Deep Learning and Computer Vision. Using the **CIFAR-10** dataset, I built and optimized Convolutional Neural Networks (CNNs) from scratch.

The main goal of this notebook is not just to achieve the highest accuracy, but to understand the **mechanics of learning**, diagnose **overfitting**, and implement techniques like **Data Augmentation** and **Dropout** to build a generalized model.

## 💡 Inspiration & Theory
Before diving into the code, I focused on the mathematical foundations of Neural Networks using resources like **3Blue1Brown's Deep Learning series**.

Understanding concepts such as:
* **Backpropagation:** How the network learns from mistakes.
* **Gradient Descent:** Finding the local minimum of the loss function.
* **Hidden Layers:** Feature extraction (edges -> shapes -> objects).

This project is the practical application of these theoretical concepts.

## 📂 Dataset
The [CIFAR-10 dataset](https://www.cs.toronto.edu/~kriz/cifar.html) consists of 60,000 32x32 color images in 10 classes, with 6,000 images per class.
* **Training images:** 50,000
* **Test images:** 10,000
* **Classes:** Airplane, Automobile, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck.

## 🏗️ Methodology

### Phase 1: The Base Model
I started with a standard CNN architecture:
* 3 Convolutional Blocks (`Conv2D` + `MaxPooling2D`)
* `Flatten` layer
* Dense Output Layer (`Softmax`)

**Observation:** The model learned very quickly but fell into the **Overfitting Trap**.
* *Training Accuracy:* ~80%
* *Validation Accuracy:* ~69%
* *Verdict:* The model was memorizing the training data instead of learning features.

### Phase 2: The Robust Model (Improved)
To fight overfitting, I introduced two regularization techniques:

1.  **Data Augmentation:**
    * `RandomFlip("horizontal")`
    * `RandomRotation(0.1)`
    * `RandomZoom(0.1)`
    * *Purpose:* Artificially increases the diversity of the training set.

2.  **Dropout:**
    * `layers.Dropout(0.5)` added before the final Dense layer.
    * *Purpose:* Randomly disables 50% of neurons during training to prevent co-adaptation (forcing the network to learn more robust features).

## 📊 Results & Comparison

| Model | Training Accuracy | Validation Accuracy | Diagnosis |
| :--- | :--- | :--- | :--- |
| **Base Model** | **80.03%** | 69.27% | ❌ High Overfitting (Gap > 10%) |
| **Robust Model** | 61.03% | **64.62%** | ✅ Good Generalization (Val > Train) |

> **Note:** Although the *Robust Model* has lower training accuracy, it is a "better" model because the Validation Accuracy is higher than the Training Accuracy. This proves the model is actually learning patterns applicable to unseen data, rather than memorizing pixels.

## 🛠️ Technologies Used
* **Language:** Python
* **Framework:** TensorFlow / Keras
* **Visualization:** Matplotlib, NumPy

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone [https://github.com/ccemozclk/Deep-Learning-Journey-Ep01.git](https://github.com/ccemozclk/Deep-Learning-Journey-Ep01.git)
