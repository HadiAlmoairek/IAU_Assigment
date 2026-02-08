# Lab 2: Bank Customer Churn Prediction - Problem Definition

## 📊 Dataset Selection

**Dataset Name:** Bank Customer Churn Dataset  
**Source:** Kaggle - Bank Customer Churn Prediction  
**Format:** CSV (Churn_Modelling.csv)  
**Size:** 10,000 rows × 14 columns

### Dataset Description
This dataset contains information about bank customers including their demographics, account details, and banking behavior. The goal is to predict whether a customer will leave the bank (churn) or continue their relationship with the bank.

---

## 🎯 Problem Type: Binary Classification

This is a **supervised learning** problem, specifically **binary classification**, because:
- We have labeled historical data (customers who left vs. stayed)
- The target variable is categorical with two classes (0 or 1)
- We want to predict a discrete outcome (churn or not churn)

---

## 🔍 Target Variable

**Variable Name:** `Exited`

**Description:** Indicates whether the customer has left the bank or not
- **0:** Customer stayed with the bank
- **1:** Customer left the bank (churned)

This is the dependent variable that our machine learning model will predict.

---

## 📝 Problem Statement

**Objective:**  
Build a machine learning classification model to predict whether a bank customer will churn (leave the bank) based on their profile and banking behavior.

**Business Value:**  
- Identify at-risk customers before they leave
- Enable proactive retention strategies
- Reduce customer acquisition costs
- Improve customer satisfaction and loyalty

**Model Goal:**  
The model should learn patterns from customer attributes such as credit score, geography, gender, age, tenure, account balance, number of products, credit card status, active membership, and estimated salary to accurately predict the likelihood of customer churn.

---

## 📋 Features (Independent Variables)

1. **RowNumber:** Record identifier
2. **CustomerId:** Unique customer ID
3. **Surname:** Customer surname
4. **CreditScore:** Customer's credit score (numerical)
5. **Geography:** Customer's country (France, Spain, Germany)
6. **Gender:** Customer gender (Male, Female)
7. **Age:** Customer age (numerical)
8. **Tenure:** Number of years with the bank (numerical)
9. **Balance:** Account balance (numerical)
10. **NumOfProducts:** Number of bank products used (numerical)
11. **HasCrCard:** Has credit card (1) or not (0)
12. **IsActiveMember:** Active member (1) or not (0)
13. **EstimatedSalary:** Estimated annual salary (numerical)

---

## 🤖 Machine Learning Approach

**Algorithm Candidates:**
- Logistic Regression
- Decision Trees
- Random Forest
- Support Vector Machine (SVM)
- Neural Networks

**Evaluation Metrics:**
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC Score

---

## 📈 Expected Outcome

The model will output a prediction for each customer:
- **Class 0:** Customer will stay (low churn risk)
- **Class 1:** Customer will leave (high churn risk)

This allows the bank to implement targeted retention campaigns for high-risk customers.
