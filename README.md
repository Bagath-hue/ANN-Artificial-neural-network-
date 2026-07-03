# ANN-Artificial-neural-network-
# 🧠 Aerodynamic Coefficient Prediction Using Artificial Neural Networks (ANN)

## 📖 Overview

Artificial Neural Networks (ANNs) have become a popular machine learning approach for nonlinear regression problems due to their ability to learn complex relationships from data. In aerodynamic analysis, ANNs can serve as surrogate models to approximate Computational Fluid Dynamics (CFD) results while significantly reducing computational cost.

This project develops a Multilayer Perceptron (MLP)-based Artificial Neural Network to predict the aerodynamic coefficients of NACA airfoils using geometric parameters and operating conditions. The trained model is evaluated on both a validation dataset and completely unseen airfoil geometries to assess its predictive capability and generalization performance.

---

# 🎯 Objectives

- Develop an ANN-based surrogate model for aerodynamic prediction.
- Predict Lift (CL), Drag (CD), and Moment (Cm) coefficients.
- Evaluate the ANN using standard regression metrics.
- Assess the model's ability to generalize to unseen airfoils.
- Analyze the limitations of ANN-based surrogate modeling.

---

# 📂 Dataset

The model was trained using aerodynamic data collected from **13 NACA airfoils**.

## Training Airfoils
- NACA 0009
- NACA 0012
- NACA 0015
- NACA 23012
- NACA 2412
- NACA 4412
- NACA 6409
- NACA 63-215
- S1223
- NACA 63-137
- MH32
- Clark Y
- E385

---

## Unseen Airfoils

The following airfoils were excluded from training and used only for testing the model's generalization capability.

- NACA 0024
- NACA 6412

---

# 📊 Features & Target Variables

## Input Features

- Angle of Attack (α)
- Maximum Camber
- Camber Position
- Thickness
- Reynolds Number

## Target Variables

- Lift Coefficient (CL)
- Drag Coefficient (CD)
- Moment Coefficient (Cm)

---

# ⚙️ Methodology

The project follows the workflow below:

1. Data preprocessing
2. Feature scaling using StandardScaler
3. Train-test split (80:20)
4. ANN model development
5. Model validation
6. Prediction on unseen airfoils
7. Performance analysis

---

# 🧠 Artificial Neural Network Architecture

The surrogate model was implemented using Scikit-learn's **MLPRegressor**.

### Network Configuration

- Hidden Layers: **64 → 128 → 64**
- Activation Function: **ReLU**
- Optimizer: **Adam**
- Maximum Iterations: **1000**

---

# 📏 Evaluation Metrics

The model performance was evaluated using:

- R² Score
- Mean Absolute Error (MAE)

for

- Lift Coefficient (CL)
- Drag Coefficient (CD)
- Moment Coefficient (Cm)

---

# 📈 Results

## 1. Validation on the Training Dataset

The ANN was trained using an 80:20 train-test split of the combined 13-airfoil dataset.

### Validation Performance

| Coefficient | R² Score | MAE |
|------------|---------:|----:|
| CL | **0.9941** | **0.0409** |
| CD | **0.9822** | **0.0037** |
| Cm | **0.9819** | **0.0059** |

### Validation Summary

The ANN achieved excellent prediction accuracy on the validation dataset, with R² values above **0.98** for all three aerodynamic coefficients. These results indicate that the network successfully learned the relationships present in the training data.

---

## 2. Generalization on Unseen Airfoils

The trained ANN was evaluated on two airfoils that were not included during training.

### NACA 0024

| Coefficient | R² Score | MAE |
|------------|---------:|----:|
| CL | -0.2242 | 0.7898 |
| CD | -1.5369 | 0.0565 |
| Cm | -163.6706 | 0.2420 |

---

### NACA 6412

| Coefficient | R² Score | MAE |
|------------|---------:|----:|
| CL | -0.0126 | 0.6541 |
| CD | -5.2564 | 0.0671 |
| Cm | -12.9050 | 0.1342 |

---

# 🔍 Why Did the ANN Fail on Unseen Airfoils?

Although the ANN achieved excellent validation accuracy, it failed to generalize to previously unseen airfoil geometries. This behavior can be attributed to several factors:

- The training dataset consisted of only **13 airfoil geometries**, which is relatively small for training a neural network.
- Neural networks generally require large and diverse datasets to learn robust physical relationships.
- The unseen airfoils possessed geometric characteristics that were not sufficiently represented in the training data.
- The ANN primarily learned patterns specific to the training dataset instead of capturing the underlying aerodynamic trends, leading to poor extrapolation performance.
- As a result, the model produced negative R² scores on unseen airfoils, indicating that its predictions were less accurate than simply predicting the mean of the observed data.

---

# 🏆 Key Findings

- The ANN achieved excellent validation accuracy on the 13-airfoil dataset.
- Validation R² scores exceeded **0.98** for all aerodynamic coefficients.
- Despite strong validation performance, the ANN failed to generalize to unseen airfoils.
- Negative R² scores on unseen geometries indicate poor extrapolation capability.
- The study highlights the importance of evaluating surrogate models on unseen datasets rather than relying solely on validation accuracy.
- Compared with the machine learning models developed in Project 1, the ANN demonstrated inferior generalization performance for unseen airfoil prediction.


├
# 🔮 Future Work

- Increase the size and diversity of the training dataset.
- Explore deeper ANN architectures with regularization techniques.
- Implement cross-validation and hyperparameter optimization.
- Compare ANN performance with advanced ensemble learning methods such as XGBoost and Random Forest.
- Investigate physics-informed neural networks (PINNs) for improved aerodynamic prediction.

---

# 👨‍💻 Author

Bagathsingh

Mini Project – *Aerodynamic Coefficient Prediction Using Artificial Neural Networks*
