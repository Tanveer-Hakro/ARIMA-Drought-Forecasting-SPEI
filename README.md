# ARIMA Drought Forecasting Using SPEI

A practical time-series forecasting project using **ARIMA** to forecast monthly drought conditions for the Islamabad region, Pakistan, using the **Standardized Precipitation Evapotranspiration Index (SPEI-01)**.

## Project Objective

The objective is to apply ARIMA practically while understanding the complete forecasting workflow:

**SPEI Data → Stationarity → ACF/PACF → ARIMA Selection → Forecasting → Evaluation → Residual Diagnostics**

## Dataset

* Variable: **SPEI-01**
* Location: Islamabad region, Pakistan
* Selected grid: **33.5°N, 73.5°E**
* Period: **1950–2021**
* Observations: **859 monthly values**
* Missing values: **0**
* Format: NetCDF (`.nc`)

## Methodology

1. Extract SPEI data for one geographic location
2. Inspect and visualize the time series
3. Test stationarity using the ADF test
4. Analyze ACF and PACF
5. Split data chronologically into training and testing sets
6. Compare candidate ARIMA models
7. Perform rolling one-step-ahead forecasting
8. Evaluate using MAE and RMSE
9. Compare against a naïve persistence baseline
10. Perform residual diagnostics using the Ljung-Box test
11. Generate a 12-month future forecast

## Final Model

**ARIMA(1,0,0)**

* `p = 1` — one autoregressive lag
* `d = 0` — no differencing required
* `q = 0` — no moving-average term

## Results

| Model             |    MAE |   RMSE |
| ----------------- | -----: | -----: |
| ARIMA(1,0,0)      | 0.8814 | 1.0452 |
| Naïve Persistence | 1.2027 | 1.4655 |

ARIMA clearly outperformed the naïve persistence forecast.

The Ljung-Box test also showed no significant remaining residual autocorrelation at lags 12 and 24.

## Key Learning

The SPEI series was stationary, so differencing was not required. Temporal dependence was relatively weak, causing longer-term ARIMA forecasts to gradually approach the mean SPEI value.

ARIMA performed better for **short-term one-step-ahead forecasting** than for predicting individual drought extremes many months into the future.

## Technologies

* Python
* Pandas
* NumPy
* Xarray
* Matplotlib
* Statsmodels
* Scikit-learn
* Kaggle

## Notebook

The complete analysis is available in:

`arima-drought-forecasting-using-spei.ipynb`

## Author

**Tanveer Hakro**
