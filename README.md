# Lab 10 – Support Vector Machines (SVM)

**Course:** ARTI 308 – Machine Learning  
**Academic Year:** 2025/2026 — 2nd Semester

---

## Learning Goals

- Understand the intuition behind Support Vector Machines (SVMs)
- Know the role of the **decision boundary**, **support vectors**, and the **margin**
- Understand the effect of the hyperparameters **C** and **gamma** in an RBF kernel
- Train an SVM classifier using scikit-learn's `SVC`
- Evaluate performance with a confusion matrix and classification report
- Apply **GridSearchCV** to find optimal hyperparameters

---

## Files

| File | Description |
|---|---|
| `02-SVM Assignment.ipynb` | Solved assignment notebook — SVM on the Iris dataset |
| `README.md` | This file |

> **Dataset:** The Iris dataset is loaded directly from seaborn (`sns.load_dataset('iris')`) — no CSV file needed.

---

## Dataset: Iris Flower Dataset

Introduced by Sir Ronald Fisher in 1936. One of the most widely used datasets in machine learning.

| Column | Type | Description |
|---|---|---|
| sepal_length | float | Sepal length in cm |
| sepal_width | float | Sepal width in cm |
| petal_length | float | Petal length in cm |
| petal_width | float | Petal width in cm |
| species | string | **Target** — setosa / versicolor / virginica |

- **150 samples** total — 50 per species
- **No missing values**
- **Multi-class classification** (3 classes)

---

## Key Concepts

### Support Vector Machine (SVM)
An SVM finds the **hyperplane** that best separates classes by **maximising the margin** — the distance between the hyperplane and the nearest data points from each class (the support vectors).

```
Large margin  →  better generalisation
Small margin  →  more prone to overfitting
```

### Kernel Trick
SVMs can separate non-linearly separable data by mapping features into a higher-dimensional space using a **kernel function**.

| Kernel | Use case |
|---|---|
| `linear` | Data is linearly separable |
| `rbf` (Radial Basis Function) | Most common; works well on non-linear data |
| `poly` | Polynomial boundaries |

### Hyperparameters

| Parameter | Description | Effect |
|---|---|---|
| **C** | Regularisation — penalty for misclassification | High C → smaller margin, tries to classify all points correctly (risk of overfit) |
| **gamma** | Controls how far the influence of a single training point reaches | High gamma → tighter fit around each point (risk of overfit) |

---

## Steps in the Notebook

| Step | Description |
|---|---|
| 1 | Load and display the Iris dataset via `sns.load_dataset('iris')` |
| 2 | **EDA** — pairplot coloured by species, KDE plot for setosa |
| 3 | **Train/Test Split** — 70% train / 30% test, `random_state=101` |
| 4 | **Train SVC** — default `SVC()` (RBF kernel) |
| 5 | **Evaluate** — confusion matrix + classification report (98% accuracy) |
| 6 | **GridSearchCV** — tune `C` ∈ {0.1, 1, 10, 100} and `gamma` ∈ {1, 0.1, 0.01, 0.001} |
| 7 | **Re-evaluate** with best parameters from grid search |

---

## Results Summary

### Default SVC
```
              precision    recall  f1-score   support

      setosa       1.00      1.00      1.00        13
  versicolor       1.00      0.95      0.97        20
   virginica       0.92      1.00      0.96        12

    accuracy                           0.98        45
```

### After GridSearchCV
```
              precision    recall  f1-score   support

      setosa       1.00      1.00      1.00        13
  versicolor       1.00      0.95      0.97        20
   virginica       0.92      1.00      0.96        12

    accuracy                           0.98        45
```

**Observation:** The default SVC already achieved 98% accuracy on this clean, well-separated dataset. GridSearchCV confirmed these parameters are already near-optimal — there was no room for improvement with this particular data split.

---

## Why SVM Works Well on Iris

- **Iris setosa** is linearly separable from the other two species.
- **Versicolor and Virginica** slightly overlap — the RBF kernel handles this boundary effectively.
- The dataset is small (150 samples), well-balanced, and noise-free — ideal conditions for SVM.

---

## How to Run

```bash
jupyter notebook "02-SVM Assignment.ipynb"
```

> No additional dependencies beyond the standard course environment (`scikit-learn`, `seaborn`, `pandas`, `numpy`, `matplotlib`).
