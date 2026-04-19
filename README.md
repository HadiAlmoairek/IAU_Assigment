# Lab 6 – Linear Regression

**Course:** ARTI 308 – Machine Learning  
**Dataset:** Medical Insurance Cost (`insurance.csv`)  
**Target:** `charges` — Predict individual medical insurance cost (continuous)

---

## Learning Goals

- Build an end-to-end regression pipeline
- Encode categorical features for use in a linear model
- Split data into training and test sets
- Train a Linear Regression model using scikit-learn
- Evaluate model performance using MAE, MSE, and RMSE
- Interpret model coefficients

---

## Files

| File | Description |
|---|---|
| `lab6_linear_regression.ipynb` | Jupyter Notebook — full regression pipeline |
| `insurance.csv` | Medical Insurance Cost dataset (1,338 rows × 7 cols) |
| `README.md` | This file |

---

## Steps in the Notebook

| Step | Description |
|---|---|
| 1 | Load dataset with Pandas |
| 2 | Explore with `.head()`, `.info()`, `.describe()`, scatter plots |
| 3 | Clean data — check missing values, encode `sex`, `smoker`, `region` |
| 4 | Train/Test split (80% / 20%, `random_state=42`) |
| 5 | Train `LinearRegression` from `sklearn.linear_model` |
| 6 | Evaluate — MAE, MSE, RMSE |
| 7 | Plot: Actual vs Predicted, Residuals Distribution |

---

## Evaluation Metrics

| Metric | Formula | Meaning |
|---|---|---|
| MAE | mean(|y - ŷ|) | Average absolute error in dollars |
| MSE | mean((y - ŷ)²) | Penalises large errors more heavily |
| RMSE | √MSE | Same unit as target (USD) — most interpretable |

---

## Key Insight

`smoker_enc` carries the largest coefficient by far, confirming that smoking is the single biggest determinant of insurance cost. `age` and `bmi` also contribute positively.

---

## How to Run

```bash
jupyter notebook lab6_linear_regression.ipynb
```
