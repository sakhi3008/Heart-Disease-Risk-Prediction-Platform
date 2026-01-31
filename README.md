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

### 📌 Architecture Diagram

[Medallion Architecture](Medallion Architecture.png)

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

[Bronze Layer](bronze_layer_table.png)
[Bronze Layer schema](bronze_schema.png)
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

[Silver Layer](silver_heart_disease_table.png)

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

[Gold Heart Disease](gold_heart_disease.png)

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

[Gold Heart Feature Details](gold_heart_feature_details.png)

---

### 🥇 Gold Table 3 – ML Feature Vectors

This table converts clinical features into **numerical vectors** suitable for machine learning.

### Process
- Selected clinically relevant features
- Encoded categorical variables
- Assembled features into a single vector column

### Output Table
- `gold_heart_features`

[Gold Heart Features](gold_heart_features.png)

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

[Logical Regression Model](logical_regression.png)
[Random Forest Model](random_forest.png)
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

[Feature Importance](Feature importance chart.png)

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

[Gold Heart Risk Prediction](gold_heart_risk_predictions.png)

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

[Final Dashboard](Final dashboards.png)

---

## 🧠 AI-Driven Insights

Based on model outputs and feature importance, AI-driven insights were generated such as:

- Blood pressure and vessel count as major risk drivers
- Higher risk concentration in specific age groups
- Combined effect of multiple clinical indicators

Due to dashboard constraints, these insights are **documented and visualized externally**, ensuring clarity without compromising dashboard stability.

[AI Insights 1](AI insights 1.png)
[AI Insights 2](AI insights 2.png)
[AI Insights 3](AI insights 3.png)
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
