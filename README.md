# Linear Regression and Linear Classifiers

A Python-based machine learning project implementing and comparing multiple regression and classification algorithms on the [UCI Adult Income dataset](https://archive.ics.uci.edu/ml/datasets/adult). The goal is to predict whether an individual's annual income exceeds $50K based on census attributes.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Models Implemented](#models-implemented)
- [Repository Structure](#repository-structure)
- [Requirements](#requirements)
- [Setup & Usage](#setup--usage)
- [Evaluation Metrics](#evaluation-metrics)
- [Results](#results)

---

## Overview

This project explores the performance of several supervised learning algorithms — both regression-based and classification-based — on a binary income prediction task. Each model is evaluated using accuracy, Cohen's Kappa Score, Mean Squared Error (MSE), and ROC-AUC where applicable.

---

## Dataset

The project uses the **Adult Income Dataset** (also known as the "Census Income" dataset) from the UCI Machine Learning Repository.

| File | Description |
|------|-------------|
| `adult.data.xlsx` | Raw training data |
| `adult.test.xlsx` | Raw test data |
| `adult_data_df_final.csv` | Cleaned training data |
| `adult_test_df.csv` | Cleaned test data |
| `adult_data_df_one_hot_encoding.csv` | One-hot encoded training features |
| `adult_test_df_one_hot_encoding.csv` | One-hot encoded test features |

Categorical features are preprocessed using **One Hot Encoding** (see the `One Hot Encoding` script), and continuous features are converted to categories as needed (see `conversion_continuous_to_categories_1` and `conversion_continuous_to_categories_2`).

---

## Models Implemented

### 1. Linear Regression
Baseline model using ordinary least squares. Predictions are rounded to produce binary outputs.

### 2. Ridge Regression
L2-regularized linear regression. Tested across a range of alpha values:
```
[0.01, 0.05, 0.1, 0.5, 1, 5, 10, 50, 65, 100, 300, 500, 1000]
```

### 3. Lasso Regression
L1-regularized linear regression. Tested across the same alpha range as Ridge, encouraging sparsity in the coefficient vector.

### 4. Logistic Regression
Binary classifier with ROC curve and AUC score computation. A ROC curve plot is saved as `Logistic Regression Figure`.

### 5. Perceptron
A linear binary classifier trained for 40 epochs with a learning rate of 0.1. ROC curve is saved as `Perceptron Figure`.

### 6. Support Vector Machine (SVM)
Linear kernel SVM (`C=1E10`) trained on a subset of 100 training samples for performance. ROC curve is saved as `SVM Figure`.

---

## Repository Structure

```
├── Linear Regression and Linear Classifiers   # Main Python script
├── One Hot Encoding                            # Preprocessing: one-hot encoding
├── conversion_continuous_to_categories_1      # Preprocessing: binning continuous features (v1)
├── conversion_continuous_to_categories_2      # Preprocessing: binning continuous features (v2)
├── adult.data.xlsx                             # Raw training data
├── adult.test.xlsx                             # Raw test data
├── adult_data_df_final.csv                     # Processed training data
├── adult_test_df.csv                           # Processed test data
├── adult_data_df_one_hot_encoding.csv          # One-hot encoded training features
├── adult_test_df_one_hot_encoding.csv          # One-hot encoded test features
└── README.md
```

---

## Evaluation Metrics

| Metric | Used For |
|--------|----------|
| Mean Squared Error (MSE) | Linear, Ridge, Lasso Regression |
| Cohen's Kappa Score | Linear Regression |
| Accuracy Score | All models |
| Classification Report | Logistic Regression, Perceptron, SVM |
| ROC-AUC Score & Curve | Logistic Regression, Perceptron, SVM |

---

## Results

Each model outputs its accuracy and additional metrics to the console. ROC curves for Logistic Regression, Perceptron, and SVM are saved as image files in the working directory.

To compare Ridge and Lasso across alpha values, the lists `compRidgeAcc`, `compRidgeMean`, `lassoAcc`, and `lassoMean` are populated during training and can be plotted or inspected post-run.

---

