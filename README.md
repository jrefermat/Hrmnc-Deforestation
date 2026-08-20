# Hrmnc-Deforestation
Harmonic time series decomposition model in Google Earth Engine using Sentinel-2 imagery and OLS regression to isolate seasonal NDVI cycles and automatically flag canopy disturbances (>2.5 std residual threshold).
# Real-Time Harmonic Deforestation Monitoring via Google Earth Engine

[Launch Live Interactive Web App](https://natural-night-506114-p9.projects.earthengine.app/view/harmonic-deforestation)

## Project Overview
This project applies harmonic time-series decomposition to Sentinel-2 surface reflectance data in Google Earth Engine (GEE) to isolate baseline seasonal vegetation cycles from anthropogenic deforestation anomalies.

## Mathematical Formulation
The temporal behavior of the Normalized Difference Vegetation Index ($NDVI$) is modeled using Ordinary Least Squares (OLS) with $n=2$ harmonic frequencies:

$$y(t) = \beta_0 + \beta_1 t + \sum_{k=1}^{2} \left( \alpha_k \cos\left(\frac{2\pi k t}{T}\right) + \gamma_k \sin\left(\frac{2\pi k t}{T}\right) \right) + \epsilon(t)$$

* **Baseline Fitting:** Fitted using a 5-year historical baseline (2018–2022).
* **Anomaly Flagging:** Residuals during the monitoring period ($2023+$) exceeding a threshold of $e(t) < -2.5\sigma$ are flagged as canopy disturbances.

## How to Run
1. Open `harmonic_decomposition.js` in the [GEE Code Editor](https://code.earthengine.google.com).
2. Click **Run** to generate map layers and inspect the pixel-level time-series chart.
