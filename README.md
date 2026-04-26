# Lab 9 – Decision Trees and Random Forests

**Course:** ARTI 308 – Machine Learning  
**Academic Year:** 2025/2026 — 2nd Semester

---

## Learning Goals

- Understand how a Decision Tree splits data using Gini impurity / entropy
- Train and evaluate a single Decision Tree classifier
- Visualise a trained tree with `sklearn.tree.plot_tree`
- Explain how Random Forests improve on Decision Trees via bagging
- Train a Random Forest and compare it against a single tree
- Interpret feature importances from a Random Forest
- Recognise and handle class imbalance issues in evaluation

---

## Files

| File | Description |
|---|---|
| `01-Decision Trees and Random Forests.ipynb` | Tutorial notebook — concepts + implementation on Kyphosis dataset |
| `02-Decision Trees and Random Forest Project.ipynb` | Project notebook — LendingClub loan default prediction |
| `kyphosis.csv` | Kyphosis dataset (81 rows × 4 cols) |
| `loan_data.csv` | LendingClub lending data 2007–2010 (9578 rows × 14 cols) |
| `README.md` | This file |

---

## Datasets

### kyphosis.csv
Surgical outcomes data for children who had corrective spinal surgery.

| Column | Type | Description |
|---|---|---|
| Kyphosis | string | **Target** — absent / present (was deformity present after surgery?) |
| Age | int | Age of child in months |
| Number | int | Number of vertebrae involved |
| Start | int | Number of the first (topmost) vertebra operated on |

### loan_data.csv
LendingClub public lending data, cleaned of NA values.

| Column | Type | Description |
|---|---|---|
| credit.policy | int | 1 = meets underwriting criteria |
| purpose | string | Purpose of loan (6 categories) |
| int.rate | float | Interest rate of loan |
| installment | float | Monthly installment amount |
| log.annual.inc | float | Log of annual income |
| dti | float | Debt-to-income ratio |
| fico | int | FICO credit score |
| days.with.cr.line | float | Days with a credit line |
| revol.bal | int | Revolving balance |
| revol.util | float | Revolving utilization rate |
| inq.last.6mths | int | Credit inquiries in last 6 months |
| delinq.2yrs | int | Times 30+ days past due (2 years) |
| pub.rec | int | Derogatory public records |
| not.fully.paid | int | **Target** — 1 = defaulted, 0 = paid in full |

---

## Key Concepts

### Decision Tree
- Splits data recursively based on the feature that best separates classes (Gini / entropy)
- Fully interpretable — can be visualised as a flowchart
- Prone to **overfitting** on small/noisy datasets

### Random Forest
- Ensemble of N decision trees, each trained on a **random bootstrap sample**
- Each tree sees a **random subset of features** at each split (reduces correlation between trees)
- Final prediction = **majority vote** across all trees
- More robust than a single tree; reduces variance without increasing bias

### Evaluation on Imbalanced Data
The LendingClub dataset has ~16% positive class (`not.fully.paid = 1`). A model that always predicts 0 would achieve ~84% accuracy but zero recall for defaulters. Always check **precision, recall, and F1** alongside accuracy.

---

## Tasks

### Notebook 01 — Tutorial (Kyphosis)
1. Load `kyphosis.csv` and run a pairplot EDA
2. Split into train / test sets
3. Train a `DecisionTreeClassifier` and evaluate
4. Visualise the tree with `plot_tree`
5. Train a `RandomForestClassifier(n_estimators=100)` and compare
6. Plot feature importances

### Notebook 02 — Project (LendingClub)
1. Load `loan_data.csv` and explore with `info()`, `describe()`, `head()`
2. Create EDA plots: FICO histograms, countplot by purpose, jointplot, lmplot
3. Encode the `purpose` column with `pd.get_dummies`
4. Train/test split
5. Train `DecisionTreeClassifier` → classification report + confusion matrix
6. Train `RandomForestClassifier(n_estimators=600)` → classification report + confusion matrix
7. Compare both models and explain results

---

## How to Run

```bash
# Tutorial
jupyter notebook "01-Decision Trees and Random Forests.ipynb"

# Project
jupyter notebook "02-Decision Trees and Random Forest Project.ipynb"
```
