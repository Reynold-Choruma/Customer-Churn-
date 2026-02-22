
# Telco Customer Churn Prediction
Predictive Modelling for Retention Strategy

Author: Reynold Takura Choruma
Project Type: Data Analytics / Machine Learning
Year: 2025

# Project Overview
A major telecom provider was experiencing a churn rate of around 26–27%, with the highest attrition among high‑value fibre‑optic subscribers. This threatened recurring revenue and increased customer acquisition costs.

This project develops a predictive churn model to identify at‑risk customers early, enabling proactive retention strategies and more efficient allocation of business resources.

# Key Outcomes
Identified 69% of churn‑risk customers with the final model (Recall ≈ 0.69).

Reduced false retention alerts from 315 to 168 per cycle (‑147 alerts, ~47% reduction).

Improved churn detection precision from 0.49 to 0.61 (~24% relative improvement).

Increased PR‑AUC by roughly 14% versus the baseline model, improving how well the model ranks high‑risk customers.
​

# Business impact:
Retention teams can focus on genuinely at‑risk customers, reducing wasted effort and better protecting recurring revenue.

# Technical Approach
Data Preparation
Data cleaning

Validated and resolved 11 missing TotalCharges values using tenure consistency checks.

Assigned zero total charges to customers with 0‑month tenure (new customers without billable history).
​

# Feature engineering

Applied one‑hot encoding to categorical service and contract features.

Standardised numerical variables (e.g., MonthlyCharges, TotalCharges, tenure) using StandardScaler to stabilise model training.
​

Handling Class Imbalance
Dataset distribution:

~73% non‑churn

~27% churn
​

To address this imbalance:

Implemented SMOTE (Synthetic Minority Oversampling Technique) on the training dataset only, preserving a realistic test set.
​

# Modelling Strategy
Evaluation Metrics
Because of class imbalance, accuracy was not used as a primary metric. Models were evaluated using:

PR‑AUC (Precision–Recall AUC) – how well the model ranks true churners ahead of non‑churners.
​

MCC (Matthews Correlation Coefficient) – balanced measure of overall prediction quality.
​

Precision, Recall, F1 score – to understand operational trade‑offs between catching more churners and limiting false alerts.
​

# Model Comparison
Model	Precision	Recall	F1	MCC	PR‑AUC
Logistic Regression (Vanilla)	0.49	0.82	0.61	~0.40	Baseline
Logistic Regression (SMOTE)	0.61	0.69	0.65	0.51	0.652
Random Forest	0.60	0.58	0.59	0.45	0.630
XGBoost	0.60	0.64	0.62	0.48	0.660
# Final Model Selected – Logistic Regression with SMOTE
Although XGBoost achieved the highest PR‑AUC (0.660), Logistic Regression with SMOTE delivered comparable performance with:

A strong balance across precision, recall, F1, PR‑AUC and MCC.

High interpretability, allowing direct linkage between coefficients and business drivers (e.g., contract type, tenure, charges).

More stable behaviour and easier deployment as an initial production model.

XGBoost is retained as a secondary, higher‑complexity model for potential future iterations.

# Key Business Insights
1️⃣ Contract Risk
Month‑to‑month customers show much higher churn risk compared with one‑ or two‑year contracts (in many telco datasets, often an order of magnitude higher).

👉 Recommendation: Incentivise migration to longer‑term contracts (discounts, bundled offers, loyalty rewards).

2️⃣ Price Sensitivity
Churned customers pay noticeably higher median monthly charges (around £15 more per month in this dataset).
​

👉 Recommendation: Review fibre pricing and perceived value; consider targeted discounts or plan optimisation for high‑charge, high‑risk segments.

3️⃣ Critical Risk Window
The first 12 months of tenure show the highest attrition, especially for month‑to‑month and fibre‑optic customers.

👉 Recommendation: Strengthen onboarding, early engagement campaigns, and proactive outreach in the 0–12 month window.

# Operational Impact
Metric	Baseline Model	Final Model (LogReg + SMOTE)
False Positives	315	168
Precision	0.49	0.61
Recall	0.82	0.69
MCC	~0.40	0.51
Retention teams now receive 147 fewer false alerts per scoring cycle, improving efficiency and targeting accuracy while still capturing the majority of true churners.

# Project Structure
text
├── 01_eda_telco_churn.ipynb        # EDA, churn patterns, data cleaning decisions
├── 02_modeling_telco_churn.ipynb   # Preprocessing, SMOTE, models, evaluation
├── WA_Fn-UseC_-Telco-Customer-Churn.csv
└── README.md
# How to Run
Clone the repository.

Place WA_Fn-UseC_-Telco-Customer-Churn.csv in the project root.
​

Open 01_eda_telco_churn.ipynb to explore the data and EDA.

Open 02_modeling_telco_churn.ipynb to reproduce preprocessing, modeling, and evaluation.

# Business Value
This project demonstrates how predictive analytics can:

Reduce customer attrition risk by prioritising high‑risk segments.

Improve retention team efficiency through better precision and fewer false alerts.

Enable proactive intervention strategies in high‑risk windows (e.g., early tenure).

Support data‑driven revenue protection and more informed pricing and contract decisions.

# Tools & Technologies
Python - Pandas - Scikit‑Learn - imbalanced‑learn (SMOTE) - XGBoost - Matplotlib - Seaborn - Jupyter Notebook


