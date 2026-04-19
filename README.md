# Lab 8 – K-Nearest Neighbors (KNN)

**Course:** ARTI 308 – Machine Learning  
**Dataset:** Medical Insurance Cost (`insurance.csv`)  
**Target:** `smoker` — Binary classification (yes = 1 / no = 0)

---

## Learning Goals

- Understand how the KNN algorithm classifies using distance
- Explain why feature standardisation is critical for KNN
- Use the Elbow Method to select the optimal K value
- Evaluate KNN with confusion matrix and classification report
- Compare performance at different K values

---

## Files

| File | Description |
|---|---|
| `02-K Nearest Neighbors Assignment.ipynb` | Jupyter Notebook — full KNN pipeline |
| `insurance.csv` | Medical Insurance Cost dataset (1,338 rows × 7 cols) |
| `README.md` | This file |

---

## Steps in the Notebook

| Step | Description |
|---|---|
| 1 | Load and explore data |
| 2 | Encode features (`sex_enc`, one-hot `region`) |
| 3 | Standardise features with `StandardScaler` |
| 4 | Train/Test split (70% / 30%, `random_state=42`, stratified) |
| 5 | Train initial KNN with K=1 and evaluate |
| 6 | Elbow Method — plot error rate for K = 1 to 40 |
| 7 | Retrain with best K — confusion matrix + classification report |
| 8 | Compare accuracy: K=1 vs best K |

---

## How KNN Works

1. For each test point, compute the **distance** to all training points.
2. Select the **K nearest neighbours**.
3. Assign the **majority class** among those K neighbours.

> **Why standardise?** KNN is distance-based. Without scaling, `charges` (values up to ~$50,000) would completely dominate over `age` (18–64) or `bmi` (15–55), making those features effectively invisible to the model.

---

## Elbow Method

Plot error rate vs K. The "elbow" — where the error stops dropping significantly — gives the optimal K that balances underfitting (high K) and overfitting (K=1).

---

## How to Run

```bash
jupyter notebook "02-K Nearest Neighbors Assignment.ipynb"
```
