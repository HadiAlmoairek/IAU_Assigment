# Lab 4 — Data Quality Assessment & Preprocessing

**Course:** CYS 313: Computer Data Security and Privacy  
**Student:** HADI ABDULQADIER ALI ALMOAIREK  
**ID:** 2240002278  
**Section:** 6ms1  
**Date:** 4/2/2026

## What’s included
This repo contains the final notebook for Lab 4 with Tasks 1–5:

1. Identify data quality issues  
2. Missing value strategy (artificial missingness + median imputation)  
3. Outlier detection/handling (IQR + capping)  
4. Normalization (Min-Max and Z-score)  
5. PCA + explained variance interpretation  

## Files
- `Lab4_DataQuality_Preprocessing.ipynb` — main submission
- `Chocolate_Sales.csv` — original dataset
- `data_cleaned.csv` — cleaned types (Date parsed, Amount numeric)
- `data_imputed.csv` — missing values introduced + imputed
- `data_processed_with_pca.csv` — outliers handled + scaling + PCA columns

## Run locally
```bash
pip install -r requirements.txt
jupyter notebook
```
Open the notebook and **Run All**.
