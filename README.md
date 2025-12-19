# Time Series Forecasting – Corporación Favorita (Kaggle)

This repository contains an end-to-end time series forecasting workflow for the **Corporación Favorita Grocery Sales Forecasting** Kaggle competition.  
The project progresses from exploratory data analysis to classical baselines, forecastability analysis, machine learning models, and finally **global forecasting models** suitable for competition submission.

---

## Notebook / HTML File Overview (in Sequence)

### 01DataViz.ipynb
**Exploratory Data Analysis (EDA)**  
- Loads raw sales data  
- Visualizes trends, seasonality, sparsity, and missingness  
- Builds intuition about store–family level demand patterns  

---

### 02BaseLine.ipynb
**Single-Series Baseline Models**  
- Implements simple benchmarks (Naive, Seasonal Naive, Moving Averages)  
- Evaluates basic accuracy metrics  
- Establishes a minimum performance benchmark  

---

### 03BaseLineAllStores.ipynb
**Baselines Across All Stores & Families**  
- Extends baseline models across multiple store–family time series  
- Aggregates performance metrics across entities  
- Highlights heterogeneity in predictability across series  

---

### 04Forecastability.ipynb
**Forecastability Analysis**  
- Computes forecastability metrics:
  - Coefficient of Variation  
  - Residual Variability  
  - Spectral Entropy  
  - Kaboudan Metric  
- Compares predictability across store–family series  
- Motivates the need for global forecasting models  

---

### 05MachineLearning.ipynb
**Local Machine Learning Models**  
- Feature engineering:
  - Lag features, rolling statistics, EWMAs  
  - Calendar features and Fourier terms  
- Trains per-series (local) ML models:
  - Linear and regularized regression  
  - Tree-based models  
- Evaluates performance using MASE, forecast bias, and runtime  

---

### 06A_GFM_Test.ipynb
**Initial Global Forecasting Model (GFM) Experiments**  
- First attempt at pooling multiple time series  
- Tests shared feature space across store–family combinations  
- Identifies challenges such as ID handling, leakage, and scaling  

---

### 06GlobalForecastingModel.ipynb
**Full Global Forecasting Model (GFM)**  
- Trains a single model across all store–family series  
- Uses:
  - Lagged target features  
  - Calendar and Fourier features  
  - Store and family identifiers  
- Demonstrates why GFMs scale better than local models  
- Kaggle Score: 3.97479

---

### 07MLForecastTest.ipynb
**Production-Grade Global Forecasting with MLForecast**  
- Reimplements the global model using `MLForecast`  
- Significantly reduces feature engineering boilerplate  
- Handles:
  - Recursive multi-step forecasting  
  - Proper inversion of target transformations  
  - On-promotion as an exogenous regressor  
- Produces predictions in Kaggle submission format  
- Kaggle Score: 1.18281

---

## Key Takeaways
- Forecastability varies widely across time series  
- Local models struggle to scale across thousands of series  
- Global Forecasting Models learn shared demand dynamics  
- `MLForecast` enables clean, efficient, and production-ready pipelines  

---

## Future Work
- Hyperparameter optimization for global models  
- Hierarchical reconciliation (store → family → total)  
- Model retraining and deployment strategies  
- Monitoring forecast bias and drift in production  

---