# Lab 7 – Logistic Regression

**Course:** ARTI 308 – Machine Learning  
**Dataset:** Medical Insurance Cost (`insurance.csv`)  
**Target:** `smoker` — Binary classification (yes = 1 / no = 0)

---

## Learning Goals

- Understand the difference between Linear and Logistic Regression
- Prepare features for a binary classification task
- Train a Logistic Regression model using scikit-learn
- Evaluate classification performance with precision, recall, F1-score
- Interpret the confusion matrix and model coefficients

---

## Files

| File | Description |
|---|---|
| `02-Logistic Regression Assignment.ipynb` | Jupyter Notebook — full classification pipeline |
| `insurance.csv` | Medical Insurance Cost dataset (1,338 rows × 7 cols) |
| `README.md` | This file |

---

## Steps in the Notebook

| Step | Description |
|---|---|
| 1 | Load and explore data (head, info, describe) |
| 2 | Visualise class differences: charges, BMI, age by smoker status |
| 3 | Encode features (`sex_enc`, one-hot `region`) |
| 4 | Train/Test split (67% / 33%, `random_state=42`, stratified) |
| 5 | Train `LogisticRegression` from `sklearn.linear_model` |
| 6 | Print classification report (precision, recall, F1, accuracy) |
| 7 | Plot confusion matrix and coefficient bar chart |

---

## Evaluation Metrics

| Metric | Description |
|---|---|
| **Precision** | Of all predicted smokers, how many actually are? |
| **Recall** | Of all actual smokers, how many did we catch? |
| **F1-Score** | Harmonic mean of precision and recall |
| **Accuracy** | Overall fraction of correct predictions |

---

## Key Insight

`charges` is by far the dominant predictor — smokers fall into a much higher cost bracket. The model achieves high accuracy because the charge distributions between classes are largely non-overlapping.

---

## How to Run

```bash
jupyter notebook "02-Logistic Regression Assignment.ipynb"
```
