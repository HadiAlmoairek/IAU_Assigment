# Lab 11 – K-Means Clustering & Customer Segmentation

**Course:** ARTI 308 – Machine Learning  
**Academic Year:** 2025/2026 — 2nd Semester

---

## Learning Goals

- Understand the difference between supervised and unsupervised learning
- Apply **K-Means clustering** to discover hidden patterns in customer data
- Use the **Elbow Method** to evaluate inertia across different values of K
- Use the **Silhouette Score** to measure cluster separation quality
- Apply **feature scaling** with `StandardScaler` before distance-based algorithms
- Use **PCA** to visualise high-dimensional clusters in 2D
- Interpret cluster results and translate them into business insights

---

## Files

| File | Description |
|---|---|
| `01-Customer Segmentation with K-Means.ipynb` | Tutorial notebook — K-Means on the Mall Customers dataset |
| `02-Credit Card Customer Segmentation Assignment.ipynb` | Solved project notebook — K-Means on CC_GENERAL dataset |
| `mall_customers.csv` | Mall customer dataset (200 rows × 5 cols) |
| `CC_GENERAL.csv` | Credit card customer dataset (8,950 rows × 18 cols) |
| `README.md` | This file |

---

## Datasets

### mall_customers.csv
Simple customer dataset used in the tutorial to introduce K-Means visually.

| Column | Type | Description |
|---|---|---|
| CustomerID | int | Unique customer identifier |
| Gender | string | Male / Female |
| Age | int | Customer age |
| Annual Income (k$) | int | Annual income in thousands of USD |
| Spending Score (1-100) | int | Score assigned by the mall based on spending behaviour |

- 200 rows · No missing values
- Used features: **Annual Income** and **Spending Score**

---

### CC_GENERAL.csv
Credit card customer behavioural data from [Kaggle](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata/data).

| Column | Description |
|---|---|
| CUST_ID | Customer ID (dropped before clustering) |
| BALANCE | Balance remaining in account |
| BALANCE_FREQUENCY | How frequently balance is updated |
| PURCHASES | Total amount of purchases |
| ONEOFF_PURCHASES | Maximum purchase in one transaction |
| INSTALLMENTS_PURCHASES | Total installment purchases |
| CASH_ADVANCE | Cash advanced by the customer |
| PURCHASES_FREQUENCY | Frequency of purchases |
| ONEOFF_PURCHASES_FREQUENCY | Frequency of one-off purchases |
| PURCHASES_INSTALLMENTS_FREQUENCY | Frequency of installment purchases |
| CASH_ADVANCE_FREQUENCY | Frequency of cash advances |
| CASH_ADVANCE_TRX | Number of cash advance transactions |
| PURCHASES_TRX | Number of purchase transactions |
| CREDIT_LIMIT | Credit limit of the customer |
| PAYMENTS | Total payments made |
| MINIMUM_PAYMENTS | Minimum payments made |
| PRC_FULL_PAYMENT | Percentage of full payment months |
| TENURE | Tenure of credit card service in months |

- 8,950 rows · 18 columns
- Missing values: `CREDIT_LIMIT` (1), `MINIMUM_PAYMENTS` (313) → filled with column mean

---

## Key Concepts

### K-Means Clustering
K-Means partitions data into **K non-overlapping clusters** by:
1. Randomly initialising K centroids
2. Assigning each point to its nearest centroid
3. Recalculating centroids as the mean of assigned points
4. Repeating steps 2–3 until convergence

```
Result: Each point gets a cluster label (0, 1, 2, … K-1)
Centroids: The representative "average" customer in each cluster
```

### Choosing K

| Method | What it measures | How to use |
|---|---|---|
| **Elbow Method** | Inertia (sum of squared distances to centroid) | Plot inertia vs K; find where the curve bends |
| **Silhouette Score** | How similar a point is to its cluster vs other clusters | Higher = better; range [-1, 1] |
| **Visual inspection** | Natural groupings visible in scatter plot | Best starting point before metrics |

### Why Scaling Matters
K-Means uses **Euclidean distance**. Without scaling:
- `BALANCE` (range: 0–19,000) dominates over `PURCHASES_FREQUENCY` (range: 0–1)
- Result: clustering ignores low-range features entirely
- Fix: `StandardScaler` → mean = 0, std = 1 for every feature

### PCA for Visualisation
The CC dataset has 17 features — impossible to plot directly.  
PCA compresses them into 2 dimensions while preserving as much variance as possible.  
> PCA here is **only for plotting** — the actual K-Means ran on all 17 scaled features.

---

## Steps — Tutorial Notebook (Mall Customers)

| Step | Description |
|---|---|
| 1 | Load `mall_customers.csv`, explore with `head()`, `info()`, `describe()` |
| 2 | Histogram of numerical features |
| 3 | Scatter plot: Income vs Spending Score (before clustering) |
| 4 | Select 2 features → `StandardScaler` |
| 5 | K-Means with K=5, assign cluster labels |
| 6 | Inverse-transform centroids to original units |
| 7 | Scatter plot with clusters + centroids |
| 8 | **Visual method** — estimate K from scatter plot |
| 9 | **Compare K = 2 to 7** visually in a grid of subplots |
| 10 | **Elbow Method** — inertia plot for K = 1 to 10 |
| 11 | **Silhouette Score** — score table and plot for K = 2 to 10 |
| 12 | Final model (K=5) + cluster interpretation table |

---

## Steps — Project Notebook (Credit Card)

| Step | Description |
|---|---|
| 1 | Import libraries |
| 2 | Load `CC_GENERAL.csv` |
| 3 | `head()`, `shape`, `info()`, `describe()` |
| 4 | Drop `CUST_ID` |
| 5 | Check missing values |
| 6 | Fill missing with column mean |
| 7 | Verify missing values are gone |
| 8 | Histograms for all features |
| 9 | Correlation heatmap |
| 10 | Scatter: BALANCE vs PURCHASES |
| 11 | Scatter: BALANCE vs CASH_ADVANCE |
| 12 | `StandardScaler` → `X_scaled` |
| 13 | Elbow Method (K = 1 to 10) |
| 14 | Silhouette scores (K = 2 to 10) |
| 15 | Silhouette score table |
| 16 | Final model with **K = 4** |
| 17 | Add `Cluster` column to dataframe |
| 18 | `groupby` cluster summary table |
| 19 | Customer count per cluster (bar chart) |
| 20 | PCA 2D visualisation |
| 21 | Answer 10 final questions |

---

## Results Summary

### Mall Customers — Cluster Profiles (K=5)

| Cluster | Annual Income | Spending Score | Profile |
|---|---|---|---|
| 0 | Low | Low | Careful, low-income shoppers |
| 1 | High | High | Premium loyal customers |
| 2 | Medium | Medium | Average customers |
| 3 | Low | High | Young / promotion-sensitive |
| 4 | High | Low | High-income, cautious spenders |

### Credit Card — Cluster Profiles (K=4)

| Cluster | Profile | Key Behaviour |
|---|---|---|
| 0 | Low-Activity | Barely use the card |
| 1 | Cash Advance Users | Rely on cash withdrawals; carry high balance |
| 2 | Active Purchasers | Frequent purchases; engaged card users |
| 3 | Full Payers / Transactors | High credit limit; pay balance in full |

---

## How to Run

```bash
# Tutorial
jupyter notebook "01-Customer Segmentation with K-Means.ipynb"

# Project
jupyter notebook "02-Credit Card Customer Segmentation Assignment.ipynb"
```
