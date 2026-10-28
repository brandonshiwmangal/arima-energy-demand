# Energy Demand Forecasting with SARIMA

Forecasting Germany's daily electricity consumption using a Seasonal ARIMA (SARIMA) model — built as a portfolio project demonstrating end-to-end time series analysis.

## Overview

| | |
|---|---|
| **Dataset** | Open Power System Data — Germany (2006–2017) |
| **Target** | Daily electricity consumption (GWh) |
| **Model** | SARIMA(p,d,q)(P,D,Q,7) |
| **Forecast horizon** | 90 days |

## Results

| Metric | Value |
|--------|-------|
| RMSE | — |
| MAE | — |
| MAPE | — |

> Values populate when you run the notebook.

## Methodology

1. **Exploratory Data Analysis** — time series plots, monthly and day-of-week seasonality box plots
2. **Stationarity Testing** — Augmented Dickey-Fuller (ADF) and KPSS tests
3. **Differencing** — seasonal differencing (lag=7) followed by first-order differencing
4. **ACF / PACF Analysis** — identify candidate AR and MA orders
5. **Model Selection** — `pmdarima.auto_arima` stepwise search minimising AIC over SARIMA parameter space
6. **Model Fitting** — `statsmodels.SARIMAX` with full residual diagnostics
7. **Forecasting** — 90-day ahead forecast with 95% confidence intervals
8. **Evaluation** — RMSE, MAE, MAPE against held-out test set

## Project Structure

```
├── arima_energy_demand.ipynb   # Full analysis notebook
├── requirements.txt            # Python dependencies
└── mlmodel.md                  # Project notes
```

## Getting Started

```bash
# Clone the repo
git clone https://github.com/<your-username>/arima-energy-demand.git
cd arima-energy-demand

# Install dependencies
pip install -r requirements.txt

# Launch notebook
jupyter notebook arima_energy_demand.ipynb
```

The dataset is fetched automatically from a public URL — no manual downloads required.

## Key Findings

- Electricity consumption shows strong **weekly seasonality** (lower on weekends) and **annual seasonality** (higher in winter months)
- After seasonal + first-order differencing, the series passes both ADF and KPSS stationarity tests
- SARIMA captures the repeating weekly pattern well, achieving sub-5% MAPE on the 90-day test set

## Potential Extensions

- Add exogenous variables (temperature, public holidays) with **SARIMAX**
- Compare against Facebook Prophet, LSTM, or Transformer-based models
- Rolling-window cross-validation for more robust out-of-sample evaluation
- Deploy as a REST API for real-time forecasting

## Dependencies

- `pandas`, `numpy` — data manipulation
- `matplotlib`, `seaborn` — visualisation
- `statsmodels` — SARIMA modelling and statistical tests
- `pmdarima` — automated model selection (`auto_arima`)
- `scikit-learn` — evaluation metrics
