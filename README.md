# Lab 4 – Data Quality Assessment & Preprocessing

**Course:** ARTI 308 – Machine Learning  
**Dataset:** Medical Insurance Cost (`insurance.csv`)

---

## Learning Goals

- Identify data quality issues (missing values, outliers, skewness, duplicates)
- Choose and justify an appropriate missing value handling strategy
- Detect and remove outliers using the IQR method
- Normalise numerical features using Min-Max scaling and Z-score standardisation
- Apply PCA and interpret explained variance

---

## Files

| File | Description |
|---|---|
| `lab4_preprocessing.ipynb` | Jupyter Notebook — all 5 preprocessing tasks |
| `insurance.csv` | Medical Insurance Cost dataset (1,338 rows × 7 cols) |
| `README.md` | This file |

---

## Tasks

### Task 1 — Identify Data Quality Issues
Examine data types, missing values, duplicate rows, and distribution shapes.  
Key finding: `charges` is strongly right-skewed; `bmi` and `charges` contain outliers.

### Task 2 — Missing Value Handling
Inject synthetic missing values into `bmi` and `age`, then apply **median imputation**.  
**Why median?** Median is robust to the skewness and outliers present in both columns, unlike mean which would be pulled by extreme values.

### Task 3 — Outlier Detection and Removal (IQR)
Apply the IQR method to `bmi` and `charges`:
```
Lower bound = Q1 - 1.5 × IQR
Upper bound = Q3 + 1.5 × IQR
```
Rows outside these bounds are removed. Before/after box plots confirm the result.

### Task 4 — Normalise Numerical Features
Apply both scaling methods to `age`, `bmi`, `children`, `charges`:

| Method | Formula | Range | Best for |
|---|---|---|---|
| Min-Max | (x - min) / (max - min) | [0, 1] | When distribution shape must be preserved |
| Z-score | (x - mean) / std | ~[-3, 3] | When algorithm assumes normal distribution |

### Task 5 — PCA
Encode all features and apply PCA. Interpret which components capture the most variance and what they represent.

---

## How to Run

```bash
jupyter notebook lab4_preprocessing.ipynb
```
