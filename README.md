# Asset Pricing in the 21st Century: Traditional Models vs. Market Complexity

Group project for FBA1049 Asset Pricing, MSc Finance, Dublin City University (April 2026).

## Overview

An empirical evaluation of UnitedHealth Group (UNH) equity, testing whether Cochrane's (2009) traditional equilibrium asset pricing framework still holds against a "market complexity" view built on fat tails, non-linear dynamics, and regime shifts. Uses 20 years of daily data (2004–2024) benchmarked against the S&P 500 and NASDAQ.

## Methodology

The analysis is run through a single Python script that takes a ticker as input and produces the full pipeline below.

1. **Normality testing** — Jarque-Bera test, skewness/kurtosis, Q-Q plot against a normal distribution
2. **Market regression** — OLS regression of UNH returns against S&P 500 and NASDAQ, correlation, R², alpha, beta
3. **Random walk testing** — Augmented Dickey-Fuller test on log prices vs. returns, followed by Monte Carlo simulation (100 paths, 1-year horizon) of future price paths
4. **CAPM vs. OLS beta comparison** — CAPM-predicted beta against empirically estimated OLS beta, with Jensen's Alpha tested for statistical significance

## Key findings

- UNH daily returns show significant fat tails and positive skew (skewness 0.96, excess kurtosis 31.19; Jarque-Bera p ≈ 0.000), rejecting normality and challenging CAPM's Gaussian assumption
- UNH beta vs. S&P 500 = 0.90 (R² = 0.31), consistent with defensive healthcare-sector characteristics
- CAPM-predicted and empirically estimated OLS betas are effectively identical
- Jensen's Alpha is not statistically significant (p = 0.069 vs. S&P 500), meaning UNH earns no return in excess of what CAPM predicts
- Log prices follow a random walk (cannot reject unit root); returns are stationary, consistent with weak-form market efficiency
- **Conclusion**: a hybrid approach fits the evidence best — CAPM provides a robust equilibrium baseline for average returns, while Monte Carlo and tail-risk tools are needed to capture the fat-tail and regime-shift dynamics CAPM misses

## Tools

Python (`yfinance`, `pandas`, `numpy`, `scipy`, `statsmodels`, `matplotlib`)

## Files

- `asset_pricing_analysis.py` — full analysis pipeline (takes a ticker as input)
- `outputs/` — generated charts (return distribution, regression scatter, Monte Carlo simulation, CAPM vs. OLS beta comparison)
