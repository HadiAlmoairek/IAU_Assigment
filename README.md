# Lab 3 – Exploratory Data Analysis (EDA)

**Course:** ARTI 308 – Machine Learning  
**Dataset:** Medical Insurance Cost (`insurance.csv`)

---

## Learning Goals

- Apply EDA techniques to understand a real-world dataset
- Check for missing values and data quality issues
- Visualise distributions of numerical and categorical features
- Identify correlations and patterns between variables
- Draw initial conclusions that guide preprocessing and modelling

---

## Files

| File | Description |
|---|---|
| `lab3_eda.ipynb` | Jupyter Notebook — full EDA on the insurance dataset |
| `insurance.csv` | Medical Insurance Cost dataset (1,338 rows × 7 cols) |
| `README.md` | This file |

---

## Tasks Completed in the Notebook

| # | Task | Tool |
|---|---|---|
| 1 | Load dataset, check shape and types | `pandas` |
| 2 | Descriptive statistics (mean, std, min, max) | `df.describe()` |
| 3 | Missing value check | `df.isnull().sum()` |
| 4 | Categorical value counts (sex, smoker, region) | `value_counts()` |
| 5 | Distribution histograms for all numerical features | `matplotlib` |
| 6 | Charges by smoker status (histogram + box plot) | `seaborn` |
| 7 | Charges by region and sex | `seaborn` |
| 8 | Scatter: BMI vs Charges coloured by smoker | `matplotlib` |
| 9 | Scatter: Age vs Charges coloured by smoker | `matplotlib` |
| 10 | Correlation heatmap (encoded features) | `seaborn` |
| 11 | Pair plot of key features | `seaborn.pairplot` |
| 12 | Key findings summary | markdown |

---

## Key Findings

- **Smoker status** is the dominant driver of insurance charges — smokers pay ~3–4× more.
- **BMI × Smoker interaction** creates a distinct high-cost cluster visible in scatter plots.
- **Age** has a moderate positive correlation with charges.
- **Charges are right-skewed** — log transformation may help regression models.
- No missing values detected.

---

## How to Run

```bash
jupyter notebook lab3_eda.ipynb
```
