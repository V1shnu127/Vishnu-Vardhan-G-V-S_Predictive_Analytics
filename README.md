## ARIMA-Based Electricity Consumption Forecasting – Insights

This project applies an **ARIMA** model to forecast hourly electricity consumption using historical demand data.
---

### Data & Modeling Overview
- **Target Variable:** Electricity consumption (MWh)
- **Frequency:** Hourly time series
- **Train–Test Split:** 80% training, 20% testing
- **Model Used:** ARIMA
---

### Visual Analysis (Train–Test–Forecast Plot)

- The **training data (blue)** shows strong **cyclical and seasonal patterns**, likely daily and weekly demand cycles.
- The **test data (orange)** continues these oscillations with similar amplitude.
- The **ARIMA forecast (green)** is relatively **flat and mean-oriented**, indicating:
  - ARIMA captures the **overall level and trend** of electricity demand.
  - It does **not fully capture strong seasonal fluctuations**, which is expected since standard ARIMA does not model seasonality explicitly.

---

### Model Coefficient Interpretation

- **Significant parameters:**
  - `ar.L2 (p < 0.001)` → strong second-lag autoregressive dependency.
  - `ma.L1 (p < 0.001)` → immediate shock effects are important.
- **Non-significant parameters:**
  - `ar.L1` and `ma.L2` have higher p-values, contributing less to prediction strength.
- **Variance (σ²):**
  - High variance reflects large natural fluctuations in electricity demand.

---

### Model Diagnostics & Statistics

- **AIC / BIC:**  
  - Used for model comparison; values are acceptable for a large dataset.
- **Ljung–Box Test (p = 0.92):**
  - Residuals show **no significant autocorrelation** → good temporal fit.
- **Jarque–Bera Test (p ≈ 0):**
  - Residuals are **not normally distributed**, common in real-world energy data.
- **Heteroskedasticity Test (p ≈ 0):**
  - Variance of errors is not constant, indicating volatility clustering.
- **Skewness & Kurtosis:**
  - Slight right skew and heavy tails → occasional demand spikes.

---

### 🔢 Error Metrics Used

- **MAE (Mean Absolute Error)**  
- **RMSE (Root Mean Squared Error)**  
- **MAPE (Mean Absolute Percentage Error)**  

These metrics provide complementary perspectives on forecast accuracy.

---

### Interpretation of Error Metrics

#### 1. Mean Absolute Error (MAE)
- Measures the **average absolute deviation** between predicted and actual electricity consumption.
- Expressed in **MWh**, making it directly interpretable for energy systems.
- A moderate MAE indicates that:
  - The ARIMA model tracks the **overall demand level** well.
  - Errors are mainly due to **unmodeled seasonal peaks and troughs**.

---

#### 2. Root Mean Squared Error (RMSE)
- Penalizes **larger errors more strongly** than MAE.
- Higher RMSE relative to MAE suggests:
  - Occasional **large deviations**, typically during high-demand or low-demand periods.
  - ARIMA struggles to capture **sharp demand spikes**, which are common in hourly electricity data.

---

### Conclusion

ARIMA provides an interpretable and statistically sound baseline for energy consumption forecasting. While effective for trend estimation and short-term prediction, seasonal and nonlinear models are recommended for higher accuracy in real-world deployment.
