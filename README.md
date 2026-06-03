# 🚪 Telco Customer Churn Prediction

> Predictive analytics to identify and retain high-risk customers, reducing churn and improving long-term profitability.

---

## 📖 Table of Contents

* [Project Overview](#project-overview)
* [Business Problem & Impact](#business-problem--impact)
* [Key Results](#key-results)
* [Data Understanding](#data-understanding)
* [Methodology](#methodology)
* [Model Performance & Interpretation](#model-performance--interpretation)
* [Business Recommendations](#business-recommendations)
* [Repository Structure](#repository-structure)
* [Installation & Usage](#installation--usage)
* [Future Improvements](#future-improvements)
* [Acknowledgements](#acknowledgements)

---

## Project Overview

Customer churn is a critical challenge for subscription-based businesses. This project analyzes the Telco Customer Churn dataset (7,043 customers) to identify key drivers of churn and build a predictive model for early intervention.

Using XGBoost with class imbalance handling techniques, the model achieves an ROC-AUC score of **0.81**, enabling retention teams to proactively identify at-risk customers and reduce customer attrition.

**This project was completed as part of the DecodeLabs Data Science Internship.**

---

## Business Problem & Impact

### The Cost of Churn

With a churn rate of approximately **26.5%**, telecom providers lose a significant portion of their customer base each year, leading to recurring revenue loss and increased acquisition costs.

### The Solution

A predictive churn scoring system that identifies high-risk customers before they leave, enabling targeted retention campaigns and personalized interventions.

The model helps answer:

* Which customers are most likely to churn?
* What factors drive churn behavior?
* Which customer segments require retention efforts?

---

## Key Results

| Metric              | Value              |
| ------------------- | ------------------ |
| Churn Rate          | 26.5%              |
| ROC-AUC             | 0.81               |
| Recall (Churn)      | 70%                |
| Precision           | 54%                |
| Top Retention Lever | Two-Year Contracts |

The model identifies approximately **70% of actual churners** while maintaining a precision of **54%**, providing a practical balance between customer coverage and retention effort.

---

## Data Understanding

Dataset Size:

* 7,043 customers
* 21 features

### Feature Categories

| Category            | Examples                                        |
| ------------------- | ----------------------------------------------- |
| Demographics        | Gender, SeniorCitizen, Partner, Dependents      |
| Account Information | Tenure, Contract, PaymentMethod, MonthlyCharges |
| Services            | InternetService, OnlineSecurity, TechSupport    |
| Target              | Churn                                           |

Source: IBM Telco Customer Churn Dataset (Kaggle)

---

## Methodology

### 1. Data Preprocessing

* Converted `TotalCharges` to numeric format
* Handled missing values
* One-hot encoded categorical variables
* Standardized numerical features
* Applied SMOTE to address class imbalance

### 2. Exploratory Data Analysis

Key findings:

* Month-to-month contracts show significantly higher churn
* Customers with shorter tenure are more likely to leave
* Fiber optic users exhibit higher churn rates
* Electronic check users show elevated churn behavior

### 3. Model Development

Algorithm:

```python
XGBClassifier()
```

Techniques:

* Stratified train-test split
* Hyperparameter tuning
* Class imbalance handling
* Performance threshold optimization

### 4. Model Interpretation

Feature importance and SHAP analysis were used to explain predictions and identify key churn drivers.

---

## Model Performance & Interpretation

### Classification Performance

| Class    | Precision | Recall | F1-Score |
| -------- | --------- | ------ | -------- |
| No Churn | 0.88      | 0.81   | 0.84     |
| Churn    | 0.54      | 0.70   | 0.61     |

### ROC-AUC

**ROC-AUC Score: 0.81**

The model demonstrates good discrimination between churning and non-churning customers.

### Top Predictive Features

1. Contract Type (Two-Year)
2. Internet Service (Fiber Optic)
3. Contract Type (One-Year)
4. Payment Method (Electronic Check)
5. Tenure

### SHAP Insights

SHAP analysis confirms:

* Longer contracts reduce churn risk
* Fiber optic service increases churn risk
* Electronic check payments correlate with churn
* Short customer tenure is a major risk factor

---

## Business Recommendations

### Promote Long-Term Contracts

* Offer discounts for annual contracts
* Provide loyalty incentives

### Improve New Customer Retention

* Implement onboarding programs
* Offer proactive support during the first 90 days

### Investigate Fiber Customer Experience

* Analyze service quality issues
* Improve customer support

### Encourage Automated Payments

* Incentivize bank transfer or credit card autopay

### Expand Value-Added Services

* Promote Online Security
* Promote Backup Services
* Promote Technical Support Packages

### Deploy Predictive Retention Campaigns

* Score customers weekly
* Automatically target high-risk customers with retention offers

For a detailed business‑focused analysis without code, see [`churn_analysis_business_story.md`](./churn_analysis_business_story.md).

---

## Repository Structure

```text
customer-churn-prediction-python/
│
├── data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
├── churn_analysis.ipynb
├── churn_analysis_business_story.md
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Installation & Usage

### Clone Repository

```bash
git clone https://github.com/MDX2002/customer-churn-prediction-python.git

cd customer-churn-prediction-python
```

### Create Virtual Environment

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn
```

### Run Notebook

```bash
jupyter notebook churn_analysis.ipynb
```

---

## Future Improvements

* Deploy using FastAPI and Docker
* Build an interactive Streamlit dashboard
* Incorporate customer support ticket data
* Integrate sentiment analysis
* Perform A/B testing of retention strategies

---

## Acknowledgements

* IBM Telco Customer Churn Dataset
* DecodeLabs Data Science Internship
* XGBoost
* Scikit-learn
* Pandas
* NumPy

Built with Python and Machine Learning to support customer retention through predictive analytics.
