# Netflix Customer Churn Prediction

## Project Overview

Customer churn is an important business problem for subscription-based services such as Netflix. Identifying customers who are likely to discontinue their subscriptions can help businesses understand customer behavior and develop effective retention strategies.

This project develops a machine learning classification model to predict whether a customer is likely to churn based on demographic, subscription, engagement, and customer activity information.

The project follows an end-to-end machine learning workflow, including data understanding, data quality assessment, exploratory data analysis, preprocessing, model development, and evaluation.

> Note: This project uses a customer churn dataset for machine learning practice and is not based on proprietary Netflix customer data.

---

## Objectives

- Understand customer churn patterns.
- Perform data quality assessment and exploratory data analysis.
- Analyze customer behavior and engagement.
- Prepare numerical and categorical features for machine learning.
- Build a Logistic Regression classification model.
- Evaluate the model using multiple classification metrics.
- Analyze the model's ability to distinguish between churned and non-churned customers.

---

## Dataset

The dataset contains **5,000 customer records** and **14 columns**.

### Main Features

- `age` – Customer age
- `gender` – Customer gender
- `subscription_type` – Customer subscription type
- `watch_hours` – Total customer watch hours
- `last_login_days` – Number of days since the customer's last login
- `region` – Customer region
- `device` – Device used by the customer
- `monthly_fee` – Monthly subscription fee
- `payment_method` – Customer payment method
- `number_of_profiles` – Number of profiles associated with the account
- `avg_watch_time_per_day` – Average daily watch time
- `favorite_genre` – Customer's favorite genre
- `churned` – Target variable indicating whether the customer churned

`customer_id` is excluded from model training because it is an identifier rather than a predictive feature.

---

## Data Quality Assessment

The dataset was checked for:

- Data types
- Missing values
- Duplicate records
- Numerical statistics
- Feature distributions
- Potentially unusual values

The dataset contains **no missing values** and **no duplicate rows**.

---

## Exploratory Data Analysis

The EDA focuses on understanding customer behavior and churn patterns.

The analysis includes:

- Customer churn distribution
- Watch-hours distribution
- Average daily watch time vs. total watch hours
- Churn comparison across:
  - Subscription type
  - Device
  - Region
  - Gender
  - Payment method
  - Favorite genre
- Watch hours by gender
- Customer distribution by gender
- Watch hours against age
- Watch hours against number of profiles
- Correlation analysis of numerical features

---

## Machine Learning Workflow

### 1. Feature and Target Selection

The `churned` column is used as the target variable.

`customer_id` is removed from the feature set because it is only an identifier.

### 2. Feature Preparation

Features are separated into:

- Numerical features
- Categorical features

### 3. Preprocessing

A Scikit-learn preprocessing pipeline is used.

#### Numerical Features

- Missing values are handled using median imputation.
- Features are standardized using `StandardScaler`.

#### Categorical Features

- Missing values are handled using most-frequent imputation.
- Categories are encoded using `OneHotEncoder`.
- `handle_unknown="ignore"` is used to handle unseen categories safely.

The preprocessing steps are combined using `ColumnTransformer`.

### 4. Train-Test Split

The dataset is divided into:

- 80% training data
- 20% testing data

A stratified split is used to preserve the class distribution between training and testing datasets.

### 5. Classification Model

**Logistic Regression** is used as the classification model.

The model uses:

- `max_iter=1000`
- `class_weight="balanced"`

The preprocessing and Logistic Regression model are combined into a single Scikit-learn `Pipeline`.

---

## Model Evaluation

The model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC-AUC
- ROC Curve

### Results

| Metric | Score |
|---|---:|
| Accuracy | 88.70% |
| Precision | 87.50% |
| Recall | 90.46% |
| F1-Score | 88.95% |
| ROC-AUC | 0.966 |

The model achieved a **ROC-AUC of 0.966**, indicating strong ability to distinguish between churned and non-churned customers.

The recall of **90.46%** indicates that the model correctly identifies a high proportion of customers who churned.

---

## ROC Curve

The ROC curve evaluates the model's ability to distinguish between churned and non-churned customers across different classification thresholds.

The ROC-AUC score of **0.966** indicates strong classification performance.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- Git
- GitHub

---

## Project Structure

```text
netflix-customer-churn-prediction/
│
├── data/
├── notebooks/
│   └── netflix_customer_churn_prediction.ipynb
├── src/
├── models/
├── reports/
├── images/
│
├── .gitignore
├── README.md
└── requirements.txt