# Solar Energy Production Prediction

Regression model that predicts the estimated annual energy production of solar installations, with SHAP used to explain the drivers. Built as part of a data science On Job Training program, using a public dataset.

**Shubham Adate** | [LinkedIn](https://www.linkedin.com/in/adate-shubham) | [GitHub](https://github.com/shubhamadatework-git)

## Problem
Predict annual solar production (kWh) for new installations from system size, developer, location, metering method and grid details, to support planning and financial modelling.

## Data
- Statewide distributed solar interconnection records
- Target: `Estimated Annual PV Energy Production (kWh)`
- Source: [Statewide Distributed Solar Projects (NY Open Data)](https://data.ny.gov/d/wgsj-jt5f). See `data/README.md`.

## Approach
1. Cleaning and exploratory analysis
2. Feature engineering (for example project age and interconnection year)
3. Compared Linear Regression with a Random Forest Regressor
4. Explained the Random Forest with SHAP values

## Results (Random Forest)
| Metric | Value |
|---|---|
| R² | 0.9906 |
| MAE | 244.91 kWh |
| RMSE | 32,486.88 kWh |

SHAP shows system size (kWdc and kWac) is the strongest driver, followed by project age or interconnection year, with location and developer contributing moderately.

## Limitations
- The target is an **estimated** production figure, not measured output. Estimates track system size closely, so the very high R² partly reflects that relationship. Predicting measured production would be a harder problem.
- The gap between MAE (about 245 kWh) and RMSE (about 32,500 kWh) shows that a few very large projects dominate the error

## Run it
```bash
pip install -r requirements.txt
jupyter notebook solar-energy-production-prediction.ipynb
```

**Tech:** Python, pandas, NumPy, scikit-learn, SHAP, seaborn, matplotlib
