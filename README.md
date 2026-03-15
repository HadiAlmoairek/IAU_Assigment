# ✅ ARTI308 — Lab 5 (Feature Engineering)

**Student:** HADI ABDULQADIER ALI ALMOAIREK  
**ID:** 2240002278  
**Section:** 6ms1  
**Date:** 4/2/2026

## Overview
This lab focuses on **feature engineering** for a classification task:
Predict `Order_Status` using a Talabat-style orders dataset.

## What I did (Student Tasks)
- **Task 1:** Added an engineered feature `Price_per_Item = Total_Price / Quantity` and justified it.
- **Task 2:** Tested an alternative `is_peak_hour` definition and compared accuracy.
- **Task 3:** Tested different `top_k` values for `Item_Name_reduced` (10, 30, 50) and compared accuracy + top feature importances.
- **Task 4:** Ran feature selection (SelectFromModel) and discussed whether it helped.

## Files
- `ARTI308 Lab5 - Solved.ipynb` — final notebook submission
- `talabat_enhanced_orders.csv` — dataset used

## Run
```bash
pip install -r requirements.txt
jupyter notebook
```
Open the notebook and **Run All**.
