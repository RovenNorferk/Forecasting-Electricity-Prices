# Project Report: Forecasting Electricity Prices using Random Forest Regression

## 1. Introduction

Electricity price forecasting is a crucial task for energy market participants, helping in efficient planning and decision-making. This project aims to predict Austria's day-ahead electricity prices using historical price data and machine learning techniques. A Random Forest Regressor is implemented to achieve this objective.

## 2. Dataset Overview

The dataset used for this project is stored in `price.csv`, containing time-series electricity price data. The key feature in this dataset is:

- **AT_price_day_ahead_EUR_MW**: The day-ahead electricity price in Euros per Megawatt-hour (EUR/MW).
- **timestamp**: The time of recorded prices.

## 3. Data Preprocessing

To prepare the dataset for modeling, the following preprocessing steps were performed:

### Timestamp Handling
- The `timestamp` column was converted to datetime format and sorted in chronological order.

### Feature Engineering
Additional features were created to capture price trends and volatility:

- **price_lag_1**: The price value lagged by one time step.
- **price_lag_2**: The price value lagged by two time steps.
- **price_moving_avg_3**: The rolling mean of the past three time steps.
- **price_std_3**: The rolling standard deviation over three time steps.

### Handling Missing Values
- Lagging and rolling window operations introduced NaN values, which were dropped to ensure model stability.

## 4. Model Implementation

A Random Forest Regressor was used to predict future electricity prices. The dataset was split into training and testing sets using an 80-20 ratio.

- **Features (X)**: `['price_lag_1', 'price_lag_2', 'price_moving_avg_3', 'price_std_3']`
- **Target (y)**: `AT_price_day_ahead_EUR_MW`
- **Train-Test Split**: 80% training data, 20% testing data.
- **Model Used**: Random Forest Regressor with 100 estimators and a random seed of 42.

## 5. Model Performance Evaluation

After training the model, predictions were made on the test set, and the performance was evaluated using the R-squared (R²) score. The calculated R² score was:

- **R² Score**: `{r2}`

The R² score indicates how well the model explains the variance in electricity prices. A higher value suggests better model performance.

## 6. Conclusion and Future Improvements

The Random Forest Regressor demonstrated reasonable predictive accuracy for short-term electricity price forecasting. However, potential improvements include:

- **Feature Expansion**: Incorporating external factors such as weather data, demand patterns, and fuel prices.
- **Hyperparameter Tuning**: Optimizing model parameters using techniques like GridSearchCV.
- **Alternative Models**: Exploring deep learning techniques like LSTMs or hybrid models for better time-series predictions.

This project provides a solid foundation for electricity price forecasting and can be further enhanced for real-world applications.
