# 📈 Consumer Demand Forecasting & Operations Optimization
### Leveraging Time-Series Analysis to Mitigate Agency Burnout

## 📌 Project Overview
This project addresses a critical operational challenge for a marketing agency facing extreme workload volatility due to the cyclical nature of the beverage industry[cite: 5]. By utilizing **Google Trends** data as a proxy for consumer intent, I developed a predictive framework to forecast demand spikes, allowing for proactive resource allocation and staff management[cite: 5].

## 🏢 Business Case: The Skyrose Dilemma
*   **Problem:** High employee burnout during peak seasons due to reactive staffing and unpredictable client demands[cite: 5].
*   **Objective:** Transition to proactive operations by forecasting interest in core categories: **Whisky, White Wine, and Craft Beer**[cite: 5].
*   **Goal:** Enable leadership to smooth cyclical workloads and optimize project timelines for 2026[cite: 5, 6].

## 🛠️ Technical Workflow
### 1. Data Engineering & Decomposition
*   **Source:** 5 years of historical Google Trends (Relative Search Volume)[cite: 5].
*   **Stationarity:** Confirmed via **Augmented Dickey-Fuller (ADF) Test** ($p < 0.05$), validating data readiness for advanced modeling.
*   **Analysis:** Applied **Time-Series Decomposition** ($Y_t = T_t + S_t + R_t$) to isolate long-term market trends, base levels, and recurring seasonal cycles.

### 2. Modeling & Benchmarking
I benchmarked a diverse range of smoothing and autoregressive models against key error metrics (RMSE, MAE) to identify optimal category-specific algorithms:
*   **Smoothing Models:** Moving Averages, Single/Double/Triple Exponential Smoothing (TES).
*   **Autoregressive Models:** SARIMA (used to leverage seasonal lags and handle residual noise).

### 3. Model Performance & Selection
| Category | Best Model | MAPE (%) | Operational Rationale |
| :--- | :--- | :--- | :--- |
| **Whisky** | TES | **4.70%** | Captured the sharp Q4 holiday seasonality better than ARIMA. |
| **White Wine** | TES | **4.72%** | Effectively balanced growth trends with distinct summer peaks. |
| **Craft Beer** | SARIMA | **10.82%** | Best handled the higher residual noise in beer search interest. |

## 📊 Strategic Impact for 2026
*   **52-Week Demand Roadmap:** Delivered a comprehensive forecast for the 2026 fiscal year[cite: 6].
*   **Resource Allocation:** Identified "quiet periods" to schedule non-urgent tasks, effectively reducing peak-season pressure[cite: 5, 6].
*   **Peak Preparedness:** Forecasted major peaks for **Whisky (Dec 2026)** and **Craft Beer/Wine (May-Aug 2026)** for proactive staffing.

## 🚀 How to Run
1. Clone the repository.
2. Ensure the dataset `Sky_rose_Dataset.xlsx` is in the root directory[cite: 6].
3. Install dependencies:
   ```bash
   pip install numpy pandas matplotlib statsmodels pmdarima scikit-learn openpyxl
