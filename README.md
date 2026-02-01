# 🫀 Heart Disease Risk Prediction Platform  
### End-to-End Analytics & Machine Learning using Databricks Lakehouse

---

## 📌 Project Overview

Heart disease is one of the leading causes of death worldwide. Early identification of high-risk patients can help clinicians take preventive actions and improve patient outcomes.

This project builds an **end-to-end Heart Disease Risk Prediction Platform** using the **Databricks Lakehouse architecture**.  
The solution covers the complete lifecycle — from raw data ingestion to machine learning–based risk prediction and interactive analytics dashboards.

All components are implemented **entirely on Databricks**, showcasing how data engineering, analytics, and machine learning work together in a real-world healthcare use case.

---

## ❓ Problem Statement

Healthcare data is often available but not structured in a way that enables:

- Early identification of high-risk patients  
- Explainable machine learning predictions  
- Centralized analytics for clinical decision-making  

### 🎯 Objective

To design and implement a **scalable, explainable, and analytics-ready heart disease risk prediction system** that:

- Cleans and prepares clinical data  
- Engineers meaningful medical features  
- Trains and compares ML models  
- Predicts patient-level risk scores  
- Visualizes insights through dashboards  

---

## 📊 Dataset Description

- **Dataset Name:** Cleveland Heart Disease Dataset  
- **Source:** UCI Machine Learning Repository  
- **Records:** 297 patients  
- **Domain:** Healthcare & Life Sciences  

### Key Attributes

- Demographics: age, gender  
- Clinical metrics: blood pressure, cholesterol, heart rate  
- Diagnostic indicators: ECG results, chest pain type  
- Target variable: presence of heart disease  

### Why this dataset?

- Clinically interpretable features  
- Widely used in medical research  
- Ideal for explainable ML modeling  
- Suitable for an end-to-end Lakehouse pipeline  

---

## 🏗️ Solution Architecture

The project follows the **Databricks Medallion Architecture**, ensuring scalability, reliability, and clarity across data layers.

### 🔹 Architecture Layers

- **Bronze Layer:** Raw data ingestion  
- **Silver Layer:** Cleaned & standardized data  
- **Gold Layer:** ML-ready features, predictions & analytics  
- **ML Layer:** Model training, evaluation & explainability  
- **Analytics Layer:** SQL dashboards

<img width="1293" height="287" alt="Notebook order" src="https://github.com/user-attachments/assets/70c876a0-31ad-4336-8a54-198a277daaf7" />


### 📌 Architecture Diagram

<img width="1693" height="470" alt="Medallion Architecture" src="https://github.com/user-attachments/assets/a412a185-7973-43f8-87bf-6408d92a8911" />


## 🥉 Bronze Layer – Raw Data Ingestion

The Bronze layer represents the **raw source of truth** for the system.

### What happens here?
- The original heart disease dataset is ingested **as-is**
- No transformations are applied at this stage
- Data is stored in **Delta format** to enable ACID transactions and versioning

### Why this matters
- Preserves original data for auditing
- Enables replay and reprocessing
- Forms the foundation of the Lakehouse pipeline

### Output Table
- `bronze_heart_disease`

<img width="850" height="226" alt="bronze_layer_table" src="https://github.com/user-attachments/assets/9e30f24c-f112-4101-823c-370d25d1144d" />
<img width="847" height="417" alt="bronze_schema" src="https://github.com/user-attachments/assets/c5d28a4e-e54d-46b0-89b8-ec138fb9fea7" />

---

## 🥈 Silver Layer – Data Cleaning & Standardization

The Silver layer prepares data for analytics and machine learning by applying **cleaning and standardization logic**.

### Key transformations
- Corrected data types (numeric vs categorical)
- Renamed columns for clinical clarity
- Mapped encoded values to human-readable labels  
  (e.g., gender, chest pain type, ECG results)
- Handled missing or inconsistent values

### Why this matters
- Improves data quality
- Makes data understandable for clinicians and analysts
- Ensures consistent schema across downstream layers

### Output Table
- `silver_heart_disease`

<img width="1345" height="678" alt="silver_heart_disease_table" src="https://github.com/user-attachments/assets/2ba0015a-1b42-40fe-9372-4f47ce8d7f63" />

---

## 🥇 Gold Layer – Business & ML Ready Data

The Gold layer contains **curated, analytics-ready and ML-ready datasets**.

This layer is split into multiple purpose-driven tables.

---

### 🥇 Gold Table 1 – Clinical Dataset

This table represents the **final cleaned clinical view** of patient data.

### Contains
- Demographics (age, gender)
- Clinical measurements (BP, cholesterol, heart rate)
- Diagnostic indicators
- Final risk labels

### Output Table
- `gold_heart_disease`

<img width="1341" height="694" alt="gold_heart_disease" src="https://github.com/user-attachments/assets/5691b098-306e-4368-9eca-37b1421916bf" />

---

### 🥇 Gold Table 2 – Feature Engineering Details

Clinically meaningful features are engineered to enhance model performance and interpretability.

### Engineered features include
- Age groups (Young / Middle Age / Senior)
- Blood pressure risk levels
- Cholesterol risk levels
- Derived clinical risk indicators
- Patient identifier for traceability

### Why this matters
- Aligns ML features with real medical reasoning
- Improves explainability
- Enables downstream analytics

### Output Table
- `gold_heart_feature_details`

<img width="1324" height="572" alt="gold_heart_features_details 2" src="https://github.com/user-attachments/assets/b9e0e78b-f996-4006-9da4-643d59b4a8b2" />

---

### 🥇 Gold Table 3 – ML Feature Vectors

This table converts clinical features into **numerical vectors** suitable for machine learning.

### Process
- Selected clinically relevant features
- Encoded categorical variables
- Assembled features into a single vector column

### Output Table
- `gold_heart_features`

<img width="1221" height="553" alt="gold_heart_features" src="https://github.com/user-attachments/assets/0337b2b1-53d3-473f-8b7f-0604562b088b" />

---

## 🤖 Machine Learning Pipeline

### Models Trained
- Logistic Regression (baseline)
- Random Forest (advanced)

### Model Tracking
- MLflow used for:
  - Experiment tracking
  - Model comparison
  - Metric logging
  - Feature importance analysis

### Model Selection
- Random Forest selected as the **champion model**
- Achieved the highest AUC score

<img width="1499" height="523" alt="logical regression " src="https://github.com/user-attachments/assets/e5f17ae6-f40b-407a-b073-f2d21b174709" />
<img width="1502" height="604" alt="random_forest" src="https://github.com/user-attachments/assets/acc33139-8a94-495a-89da-15ebdf7c3c72" />

---

## 🔍 Feature Importance & Explainability

Feature importance analysis was performed to understand **clinical drivers of heart disease risk**.

### Key contributors identified
- Number of major vessels
- ST depression
- Blood pressure
- Maximum heart rate
- Age and gender
- Derived risk indices

### Why this matters
- Builds trust in ML predictions
- Supports clinical decision-making
- Enhances transparency

<img width="881" height="402" alt="Feature Importance chart" src="https://github.com/user-attachments/assets/11d1dd43-4e40-4f3a-b634-a6e4cce2f7da" />

---

## 🚦 Risk Prediction & Scoring

The champion model generates **patient-level risk predictions**.

### Outputs
- Risk probability score (0–1)
- Risk classification:
  - Low Risk
  - Medium Risk
  - High Risk

Predictions are stored as a governed Delta table for analytics and reporting.

### Output Table
- `gold_heart_risk_predictions`

<img width="1321" height="612" alt="gold_hear_risk_predictions" src="https://github.com/user-attachments/assets/8a4ecbf0-6ebf-4e8a-b5ef-570d5e00fb4b" />

---

## 📊 Analytics & SQL Dashboards

An interactive dashboard was built using **Databricks SQL**.

### Dashboard Insights
- Total patients analyzed
- High-risk patient count
- Average predicted heart disease risk (%)
- Risk distribution by age group
- Risk distribution by gender
- Clinical drivers of high risk

### Why this matters
- Enables fast clinical insights
- Supports data-driven healthcare decisions
- Provides an executive-level overview

<img width="1395" height="714" alt="Final dashboards" src="https://github.com/user-attachments/assets/23b9e757-85fc-4e67-8615-22c7421bb5e7" />

---
## 🔍 Key Insights from the Dashboard

👥 **Gender-wise Risk Pattern**  
The analysis shows that **male patients account for a higher proportion of high-risk cases**, whereas female patients are more concentrated in the low to medium risk categories. This indicates gender as a notable risk differentiator.

🎂 **Impact of Age on Heart Disease Risk**  
- **Middle-aged and senior patients** exhibit a significantly higher presence of **medium and high risk levels**.  
- **Younger individuals** are largely observed in the **low-risk group**, reinforcing age as a key contributing factor.

🩺 **Role of Blood Pressure**  
Patients with **high blood pressure** demonstrate a marked increase in heart disease risk compared to those with normal or elevated BP levels, emphasizing BP as a critical clinical indicator.

🫀 **Blocked Vessels vs Risk Trend**  
A clear upward trend is observed where the **average risk percentage increases with the number of blocked vessels**, confirming a strong positive relationship between vessel blockage severity and heart disease risk.

📈 **Risk Level Distribution**  
While **low-risk patients form the largest group**, a considerable share of the population falls under **medium and high risk**, indicating the need for early diagnosis and preventive care.

🧠 **Top Clinical Drivers of Risk**  
Feature importance analysis highlights the following as the **most influential factors** in heart disease risk prediction:
- Number of major vessels blocked  
- Maximum heart rate achieved  
- Age  
- Blood pressure levels  

### 📝 Key Takeaway

This analysis demonstrates that age, blood pressure, and vessel blockage play a dominant role in determining heart disease risk, with older and male patients showing higher vulnerability.

---

## 🧠 AI-Driven Insights

Based on model outputs and feature importance, AI-driven insights were generated such as:

- Blood pressure and vessel count as major risk drivers
- Higher risk concentration in specific age groups
- Combined effect of multiple clinical indicators

Due to dashboard constraints, these insights are **documented and visualized externally**, ensuring clarity without compromising dashboard stability.

<img width="974" height="371" alt="AI insights 1" src="https://github.com/user-attachments/assets/83ba37c2-1280-448b-a2e3-3c90366b364c" />
<img width="926" height="446" alt="AI insights 2" src="https://github.com/user-attachments/assets/e0f48f1d-c26d-4afe-b2ea-a00b9b54b7b3" />
<img width="917" height="382" alt="AI insights 3" src="https://github.com/user-attachments/assets/3cdd5fd5-a9b4-40a3-85f6-59303d587fc7" />
<img width="1596" height="458" alt="AI driven insights" src="https://github.com/user-attachments/assets/f26176c8-c9a7-485b-8f92-de3278b36ee8" />

---

## 🔮 How the Risk Prediction Works

The heart disease risk prediction is built using a **data-driven machine learning approach**:

- Patient clinical data such as **age, gender, blood pressure, cholesterol, heart rate, and number of blocked vessels** is used as input.
- The dataset is **cleaned, preprocessed, and transformed** to ensure consistency and accuracy.
- Important features influencing heart disease risk are identified through **feature importance analysis**.
- A **classification model** is trained to categorize patients into **Low, Medium, or High Risk** groups based on learned patterns.
- The predicted risk levels are then visualized using an **interactive analytics dashboard**, enabling easy interpretation of results.

This approach allows the system not only to **predict risk**, but also to **explain the contributing factors** behind each prediction.

---

## ✅ Final Outcome

This project demonstrates an **end-to-end healthcare analytics and machine learning platform** built entirely on Databricks, showcasing:

- Lakehouse architecture
- Production-grade data pipelines
- Explainable machine learning
- Business-ready analytics dashboards

The solution is **scalable, transparent, and clinically meaningful**, making it suitable for real-world healthcare applications.







Predicts patient-level risk scores

Visualizes insights through dashboards
