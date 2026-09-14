# 🛒 SmartKart Customer Churn Prediction

## 📌 Project Overview

SmartKart is an online retail company facing customer retention challenges. Some customers are no longer purchasing, complaints are increasing, and the company needs to identify customers who may leave.

This project uses **Machine Learning** to predict which customers are likely to churn so that the retention team can take action before customers leave.

The project uses a **Logistic Regression** model because customer churn is a binary classification problem: **Churn (1)** or **No Churn (0)**.

---

## 🎯 Business Question

> **Which SmartKart customers have a higher possibility of leaving?**

### Business Goal

Identify customers who are at high risk of churn and provide a ranked list that the retention team can use for targeted retention actions.

---

## 📊 Dataset

The project uses:

**`SmartKart_dirty_100_rows.csv`**

The dataset contains **100 customer records** and intentionally includes real-world data-quality issues such as:

* Missing values
* Duplicate records
* Incorrect data types
* Invalid values
* Extreme outliers

The main columns are:

| Column          | Description                              |
| --------------- | ---------------------------------------- |
| `Customer_ID`   | Unique customer identifier               |
| `Age`           | Customer age                             |
| `Monthly_Spend` | Customer's monthly spending              |
| `Complaints`    | Number of customer complaints            |
| `Churn`         | Target variable: 1 = Churn, 0 = No Churn |

---

## 🔄 Machine Learning Pipeline

The project follows a complete **15-step ML pipeline**:

1. Data Collection
2. Data Understanding
3. Data Cleaning
4. Outlier Detection & Treatment
5. Feature Selection
6. Define Target Variable
7. Encode Target Variable
8. Train-Test Split
9. Feature Standardisation
10. Model Building
11. Model Training
12. Prediction
13. Model Evaluation
14. Model Interpretation
15. Final Business Output

---

## 🧹 Data Cleaning

The raw dataset contained several data-quality problems.

The cleaning process:

* Removed **5 duplicate rows**
* Corrected whitespace and data-type issues
* Converted Age into numeric format
* Corrected `"thirty"` to `30`
* Removed invalid age values
* Converted negative spending values into missing values
* Filled missing values using the **median**

After cleaning, the dataset contained **95 customer records** with no remaining missing values.

---

## 📈 Outlier Treatment

The **IQR (Interquartile Range)** method was used to detect extreme values.

Examples:

* `Monthly_Spend = 99999` was identified as an extreme outlier and capped.
* `Complaints = 50` was also identified as an outlier and capped.

Instead of deleting the affected customers, the values were capped so their other information could still be used.

---

## 🎯 Features Used

The model uses three business-relevant features:

* **Age**
* **Monthly Spend**
* **Complaints**

`Customer_ID` was excluded because it is only an identifier and does not provide meaningful predictive information.

### Target Variable

**`Churn`**

* `0` → No Churn
* `1` → Churn

The cleaned dataset contained approximately **54% churned customers and 46% non-churned customers**.

---

## 🧪 Train-Test Split

The dataset was divided into:

* **80% Training Data:** 76 customers
* **20% Testing Data:** 19 customers

Stratification was used to maintain a similar churn ratio in both datasets.

---

## ⚙️ Machine Learning Model

### Logistic Regression

Logistic Regression was selected because churn is a **binary classification problem**.

The model also provides **churn probabilities**, which can be used to rank customers according to their risk level.

Before training, the features were standardised using `StandardScaler`.

---

## 📊 Model Performance

The model achieved the following results on the test set:

| Metric    |       Score |
| --------- | ----------: |
| Accuracy  |  **89.47%** |
| Precision |  **83.33%** |
| Recall    | **100.00%** |
| F1-Score  |  **90.91%** |

Confusion Matrix:

```text
[[7, 2],
 [0, 10]]
```

The model correctly identified all actual churners in the test set, resulting in **100% recall for churn detection**.

---

## 🔍 Key Business Insights

The model identified important relationships between customer behaviour and churn.

### 1. Complaints Increase Churn Risk

`Complaints` has a positive coefficient, meaning that higher numbers of complaints are associated with increased churn risk.

### 2. Higher Monthly Spending Reduces Churn Risk

`Monthly_Spend` has a strong negative coefficient, indicating that customers with higher monthly spending have lower predicted churn risk.

### 3. Age Has a Smaller Impact

`Age` has a smaller positive coefficient compared with the other features.

Therefore, **complaint reduction and maintaining high-value customer relationships are important retention priorities**.

---

## 🚨 Top High-Risk Customers

The model generated a business-ready customer risk report and ranked customers according to their predicted churn probability.

The top five highest-risk customers were:

| Customer | Churn Probability | Risk            |
| -------- | ----------------: | --------------- |
| C037     |             99.7% | Likely to Churn |
| C018     |             99.7% | Likely to Churn |
| C011     |             99.7% | Likely to Churn |
| C002     |             99.0% | Likely to Churn |
| C095     |             98.1% | Likely to Churn |

---

## 💼 Business Recommendation

SmartKart can use the churn-risk report to:

* Contact high-risk customers
* Resolve customer complaints quickly
* Offer personalised retention incentives
* Prioritise high-value customers
* Monitor customers with increasing complaint levels
* Develop targeted marketing and retention campaigns

The final output is designed as an **actionable retention list**, rather than only a machine-learning prediction.

---

## 📁 Project Files

```text
smartkart-customer-churn-prediction/
│
├── SmartKart_Churn_Prediction_ML_Pipeline.ipynb
├── SmartKart_dirty_100_rows.csv
├── smartkart_churn_risk_report.csv
└── README.md
```

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Logistic Regression
* Google Colab
* Jupyter Notebook

---

## 📌 Project Outcome

This project demonstrates a complete machine-learning workflow, from **dirty customer data to a business-ready churn risk report**.

The final model achieved approximately **89.47% accuracy, 83.33% precision, 100% recall, and 90.91% F1-score** on the test dataset.

### Resume Highlight

> Built an end-to-end customer churn prediction pipeline involving data cleaning, outlier treatment, feature selection, standardisation and Logistic Regression, achieving 89.47% accuracy and 100% recall for churn detection, with a business-ready customer risk report.
