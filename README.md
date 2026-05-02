# Consumer Demand Forecasting

An end-to-end time series analysis project exploring the sales dynamics of **Whisky**, **White Wine**, and **Craft Beer** in the Canadian market. This project utilizes statistical decomposition and advanced forecasting models (Exponential Smoothing and SARIMA) to understand market trends and seasonality.

## 📊 Project Overview
Using weekly sales data from 2020 to 2025, this analysis identifies how different alcohol categories respond to seasonal changes in Canada. The project transitions from basic descriptive statistics to complex predictive modeling, providing actionable insights for inventory management and demand forecasting.

## 🛠️ Tech Stack
* **Language:** Python 3.12
* **Modeling:** `statsmodels`, `pmdarima`
* **Data Science:** `pandas`, `numpy`, `scikit-learn`
* **Visualization:** `matplotlib`

## 📈 Technical Analysis

### 1. Seasonal Decomposition
We applied **Additive Seasonal Decomposition** ($Y_t = T_t + S_t + R_t$) with a 52-week period. 
* **Whisky:** Showed a clear winter seasonality, with massive spikes during the December holiday periods.
* **White Wine & Craft Beer:** Showed "Summer Seasonality," with peaks aligned with warmer months and troughs in the winter.
* **Trend:** All three categories exhibit a long-term upward trend, suggesting overall market growth.

### 2. Stationarity Testing
Before modeling, we performed the **Augmented Dickey-Fuller (ADF) Test**. 
* All series returned $p < 0.05$, allowing us to reject the null hypothesis of non-stationarity.
* The data was determined to be stationary, making it suitable for ARIMA-based modeling without further differencing ($d=0$).

### 3. Model Comparison & Performance
We evaluated models using **MAPE (Mean Absolute Percentage Error)** and **RMSE**. 

| Category   | Best Model | MAPE (%) | Why it won? |
|------------|------------|----------|-------------|
| **Whisky** | Triple Exponential Smoothing (TES) | **4.70%** | Captured the extreme holiday seasonality better than ARIMA. |
| **White Wine** | Triple Exponential Smoothing (TES) | **4.72%** | Effectively balanced the steady growth trend with summer peaks. |
| **Craft Beer** | SARIMA(1, 0, 1) | **10.82%** | Better handled the higher residual noise (unexplained variability) in beer sales. |

### 4. Forecasting Logic
* **Holt-Winters (TES):** Chosen for Whisky and Wine because it accounts for both the **Level**, **Trend**, and **Seasonality** components.
* **SARIMA:** Used for Craft Beer to leverage the auto-regressive properties ($p$) and moving averages ($q$) while accounting for the 52-week seasonal lag.

## 🚀 How to Run
1.  Clone the repository.
2.  Ensure you have the dataset `Sky_rose_Dataset_Canada.xlsx` in the root directory.
3.  Install dependencies:
    ```bash
    pip install numpy==1.26.4 pandas matplotlib statsmodels pmdarima scikit-learn openpyxl
    ```
4.  Run the Jupyter/Colab notebook to regenerate forecasts for the next 52 weeks.

## 🔮 Future Forecasts
The model predicts continued growth into 2026, with the next major peak for Whisky expected in December 2025, while Craft Beer and White Wine are projected to peak in July/August 2026.
