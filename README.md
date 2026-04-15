# Urban Rent Forecasting

Machine learning pipeline for predicting apartment rents in U.S. urban markets using feature engineering and ensemble models.

---

## Overview

This project builds an end-to-end data science pipeline to estimate apartment rental prices from real-world listing data.

The workflow addresses key challenges in real estate data:
- missing and noisy features
- skewed price distributions
- high-cardinality location variables
- heterogeneous structured + semi-structured inputs

The final solution balances **predictive performance** and **interpretability**, making it useful for understanding how rents are determined.

---

## Key Results

- Final model: **Random Forest Regressor**
- **MAE: $186.2 (cross-validation)**  
- **MAE: $181.6 (evaluation set)**  
- ~**23% improvement over baseline models**  
- Strong generalization across unseen data  

### Main Insights

- **Location (~38%)** is the dominant price driver  
- **Apartment size (~22%)** strongly influences rent  
- Amenities and room configuration contribute meaningful signal  

---

## Problem Statement

Given apartment listing features such as:

- square footage
- bedrooms and bathrooms
- amenities
- pet policies
- city and state

the goal is to **predict monthly rent** as accurately as possible.

This is formulated as a **supervised regression problem**, evaluated primarily using **Mean Absolute Error (MAE)**.

---

## Dataset

- ~99,000 U.S. apartment listings  
- Mix of:
  - numerical features
  - categorical variables
  - binary indicators
  - missing values
  - high-cardinality location data (thousands of cities)

Key challenge:
> Extract meaningful signals while avoiding overfitting on sparse location data.

---

## Methodology

### 1. Data Preprocessing

- removed irrelevant and non-predictive fields
- handled missing values with targeted strategies
- applied log transformation to reduce skewness
- clipped outliers to stabilize training
- normalized numerical features

---

### 2. Feature Engineering

- **Structural features**
  - room count
  - bedroom/bathroom ratio

- **Amenities processing**
  - amenity count
  - binary flags for key features

- **Geographic encoding**
  - Bayesian-smoothed encoding for city/state
  - prevents overfitting on rare locations

---

### 3. Model Comparison

Models evaluated:

- Lasso
- Ridge
- KNN
- Random Forest
- XGBoost

Tree-based models significantly outperformed linear baselines.

---

### 4. Model Selection

**Random Forest** selected due to:

- best predictive performance
- stable cross-validation results
- robustness to noise
- built-in interpretability (feature importance)

---

## Evaluation

Primary metric:

- **MAE (Mean Absolute Error)**

Additional metrics:

- RMSE
- R²