# thermal-intelligence-hpc

# Thermal Intelligence: A Data-Driven Framework for Data Center Waste Heat Recovery

**Climatebase Fellowship | Sept-Dec 2026**  
**Lauren Chagaris | MS Data Science & AI, Boston University**

---

## Overview

This project applies causal inference, machine learning, and time series forecasting
to operational telemetry from the Frontier Supercomputer (Oak Ridge National Laboratory)
to quantify waste heat recovery potential and build a replicable assessment framework
for grid-powered data centers.

Frontier is the world's first exascale supercomputer (1.1 quintillion calculations/second)
and one of the most energy-efficient large-scale HPC facilities in the world (PUE: 1.055).
Despite its efficiency, 57,060 MWh of recoverable thermal energy went uncaptured in 2023.

**Dataset:** ORNL Frontier Facility Data, Nature Scientific Data (2024)  
49,869 observations at 10-minute resolution across 2023.

---

## Research Questions

1. What is the causal relationship between compute load and recoverable waste heat?
2. How much thermal energy is recoverable under real operating conditions?
3. What seasonal and operational patterns determine heat pump viability?
4. Can waste heat output be predicted from facility telemetry?
5. How does Frontier score on a generalizable thermal recovery assessment framework?

---

## Methods

| Section | Method |
|---|---|
| EDA | Correlation analysis, seasonality decomposition, subloop breakdown |
| Causal Analysis | OLS with controls, IV regression (2SLS), RDD at 30°C threshold, mediation analysis |
| Recovery Viability | MWh quantification, homes heated, CO2 avoided, economic value |
| Scorecard | Site Thermal Recovery Scorecard (6 technical dimensions) |
| Predictive Model | Linear baseline vs XGBoost with SHAP feature importance |
| Forecasting | Prophet time series (weekly seasonality) |

---

## Key Results

- **Causal estimate:** 0.75 MW of waste heat per MW of compute power (consistent across OLS, IV, mediation)
- **Annual recoverable energy:** 57,060 MWh (2023)
- **Community impact:** 5,434 homes heated, 10,271 tonnes CO2 avoided, $3.7M estimated value
- **Viability:** 69.7% of hours above 30°C heat pump threshold; February low of 28%
- **Best subloop:** Subloop 3 carries 60% of recoverable heat, viable nearly year-round
- **Model performance:** XGBoost R2=0.620, RMSE=1.391 MW vs linear baseline R2=0.378
- **Scorecard:** Frontier scores 2.7/5.0 -- strong thermal quality, weak site context

---

## Figures

| Figure | Description |
|---|---|
| 01_sanity_check_scatter | Compute power vs waste heat scatter |
| 02_full_year_timeseries | Full 2023 waste heat and PUE time series |
| 03_seasonality | Monthly waste heat and viability by month |
| 04_subloop_breakdown | Waste heat and return temp by subloop |
| 05_correlation_heatmap | Pearson correlation matrix |
| 06_hourly_patterns | Hourly waste heat and operating state distribution |
| 07_ols_coefficients | OLS regression coefficients with confidence intervals |
| 08_iv_comparison | OLS vs IV estimate of compute power effect |
| 09_rdd_threshold | Regression discontinuity at 30°C threshold |
| 10_mediation_analysis | Mediation analysis: return temperature as mediator |
| 11_recovery_mwh_monthly | Monthly recoverable energy above 30°C threshold |
| 12_business_case | Homes heated, CO2 avoided, estimated value |
| 13_scorecard_radar | Site Thermal Recovery Scorecard radar chart |
| 14_model_comparison | Linear baseline vs XGBoost R2 and RMSE |
| 15_shap_values | SHAP feature importance for XGBoost model |
| 16_prophet_forecast | Prophet forecast with Dec 2023 holdout |

---

## Repository Structure

```
thermal-intelligence-hpc/
├── data/
│   ├── thermal_intelligence.ipynb    # Main research notebook
│   ├── frontier_facility_data.xlsx   # Source dataset (ORNL)
│   └── figures/                      # All generated figures
├── README.md
```

---

## Part 2: HeatIQ (In Development)

HeatIQ is a full-stack web application that operationalizes this analysis framework
for any grid-powered data center with cooling loop instrumentation.

**Stack:** FastAPI + React + Docker + Azure  
**Status:** In development (Dec 2026)

---

## References

- ORNL Frontier Facility Dataset: Nature Scientific Data, 2024
- EIA Residential Energy Consumption Survey, 2020
- EPA Emissions Factors for Greenhouse Gas Inventories, 2023
- EnEfG (Germany): Energieeffizienzgesetz, 2023
- Equinix + Helen district heating, Helsinki, Finland
- Microsoft + Fortum district heating, Espoo, Finland