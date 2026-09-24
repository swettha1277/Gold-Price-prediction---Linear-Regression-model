Gold Price Prediction

A regression project predicting the price of the SPDR Gold Shares ETF (GLD) using related market indicators, built while learning Python and machine learning fundamentals.

Dataset

Gold Price Prediction Dataset (Kaggle, by sid321axn) — 2,290 rows spanning 2008–2018.

Features used: S&P 500 index (SPX), oil ETF price (USO), silver ETF price (SLV), EUR/USD exchange rate, plus Year and Month extracted from the date column. Target: GLD (gold ETF closing price, in USD)

Approach
Loaded and explored the raw data
Cleaned mixed date formats (some rows used MM/DD/YYYY, others YYYY-MM-DD) using pd.to_datetime(..., format='mixed')
Extracted Year and Month as numeric features from the date, then dropped the original date column
Split into training (80%) and test (20%) sets
Trained a Linear Regression model
Evaluated with MAE, and examined the model's learned coefficients to interpret feature importance
Results
MAE: $5.15 — average prediction error, roughly 4.2% relative to the mean gold price (~$122.73)
Strongest coefficients: EUR/USD and Year, followed by SLV (silver price)
Predicted-vs-actual scatter plot shows tight clustering around the ideal prediction line, consistent with the low error
What I'd improve next
Feature coefficients are on different scales (e.g. EUR/USD ranges ~1.0–1.5, SPX ranges in the thousands), which makes raw coefficient comparison somewhat misleading — scaling features (e.g. with StandardScaler) would give a fairer comparison of true feature importance
Year likely reflects a general upward price trend specific to 2008–2018 rather than a fundamentally causal relationship — worth testing on more recent data to check if this holds
Try Random Forest Regressor to see if a non-linear model improves on Linear Regression's already-strong result
Tools

Python, pandas, scikit-learn, matplotlib, Google Colab
