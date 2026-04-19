# Lab 5 – Feature Engineering (Classification)

**Course:** ARTI 308 – Machine Learning  
**Dataset:** Medical Insurance Cost (`insurance.csv`)  
**Target:** `smoker` — Binary classification (yes = 1 / no = 0)

---

## Learning Goals

- Create new features that improve model performance
- Evaluate the impact of different feature engineering choices
- Vary encoding strategies and measure the effect on accuracy
- Apply feature selection to identify the most informative features

---

## Files

| File | Description |
|---|---|
| `lab5_feature_engineering.ipynb` | Jupyter Notebook — all 4 feature engineering tasks |
| `insurance.csv` | Medical Insurance Cost dataset (1,338 rows × 7 cols) |
| `README.md` | This file |

---

## Tasks

### Task 1 — Engineer a New Feature
**Feature:** `charges_per_bmi = charges / bmi`  
**Justification:** Smokers are in a completely different charge bracket regardless of BMI. Normalising charges by BMI amplifies the signal — a non-smoker with high BMI has a moderate ratio, while a smoker with high BMI has a very large one. This gives the classifier a sharper class boundary.

### Task 2 — Change the BMI Category Rule
- **Original rule:** Underweight / Normal / Overweight / Obese (4 bins at 18.5, 25, 30)
- **New rule:** Adds a 5th category — Obese I (30–34.9) vs Obese II (≥ 35)
- Compare accuracy and discuss whether finer granularity helps predict smoking status.

### Task 3 — Vary the Number of Age Groups
Test `age_bins` ∈ {2, 4, 6, 8, 10} and compare:
- Model accuracy for each setting
- Top 3 most important features for each

### Task 4 — Feature Selection (Optional)
Use `SelectFromModel` with a trained Random Forest to automatically drop low-importance features. Compare accuracy before and after selection and interpret the importance rankings.

---

## How to Run

```bash
jupyter notebook lab5_feature_engineering.ipynb
```
