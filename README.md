# Data-Driven Pricing Model for Refurbished Smartphones

This project develops a data-driven pricing model to help ReCell set consistent and accurate resale prices for refurbished smartphones. The goal is to reduce revenue loss, improve pricing transparency, and support better inventory decisions.

## Project Overview

ReCell currently relies on manual pricing, which leads to inconsistent valuations across brands, conditions, and features. This project uses linear regression to predict normalized used prices based on key device characteristics and market variables.

## Dataset

- **Rows:** 3,454  
- **Columns:** 15  
- **Key Features:** brand_name, os, screen_size, main_camera_mp, selfie_camera_mp, int_memory, ram, battery, weight, release_year, days_used, normalized_new_price, normalized_used_price  
- **Missing Values:** Present in several numeric features, handled using median imputation  
- **Duplicates:** None  

## Workflow

### 1. Exploratory Data Analysis (EDA)
- Examined distribution of the target variable  
- Reviewed correlations among numeric variables  
- Analyzed categorical variables such as brand and network technology  

### 2. Data Preprocessing
- Median imputation for missing values  
- Dummy encoding with drop-first  
- Outlier detection performed but no removals  
- Created years_since_release from release_year  
- Removed multicollinearity using VIF > 10 threshold  
- Feature selection based on p-values  

### 3. Model Development
A linear regression model was fit using the cleaned dataset. The model was evaluated using a train–test split.

### 4. Model Performance

| Metric | Train | Test |
|--------|-------|-------|
| R² | 0.847 | 0.833 |
| Adjusted R² | 0.846 | 0.831 |
| RMSE | 0.23 | 0.24 |
| MAE | 0.18 | 0.19 |
| MAPE | 4.32% | 4.51% |

### 5. Diagnostic Checks
- Residuals mostly symmetric with some deviation from normality  
- Shapiro-Wilk test showed non-normal residuals  
- Homoscedasticity test indicated constant error variance  
- Multicollinearity addressed earlier during preprocessing  

## Key Insights

- normalized_new_price is the strongest positive predictor  
- RAM, screen_size, and camera specifications all increase used price  
- years_since_release negatively impacts price  
- Celkon brand decreases value, while Nokia and Xiaomi increase it  
- 4g has a positive effect; 5g shows a small negative effect due to limited sample size  

## Recommendations

- Use the model to support dynamic pricing for refurbished inventory  
- Apply feature insights to purchasing and valuation decisions  
- Explore nonlinear modeling techniques for improved performance  

- Project summary or presentation materials  

