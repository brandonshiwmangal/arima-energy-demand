# SARIMA Energy Demand Forecasting

**Dataset:** Open Power System Data — Germany Daily Electricity Consumption (2006–2017)  
**Model:** SARIMA(p,d,q)(P,D,Q,m=7)

## Project structure
- `arima_energy_demand.ipynb` — full analysis notebook
- `requirements.txt` — Python dependencies

## Methodology
1. Stationarity analysis: ADF + KPSS tests
2. Differencing: seasonal (lag=7) + first-order
3. ACF/PACF plots for parameter identification
4. Model selection: `pmdarima.auto_arima` stepwise AIC search
5. SARIMA fit via `statsmodels.SARIMAX`
6. Residual diagnostics
7. 90-day forecast with 95% confidence intervals
8. Evaluation: RMSE, MAE, MAPE

## Setup
```bash
pip install -r requirements.txt
jupyter notebook arima_energy_demand.ipynb
```
