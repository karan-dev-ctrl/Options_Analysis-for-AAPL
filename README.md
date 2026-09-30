![Options Analysis](https://img.shields.io/badge/Options-Volatility_Analysis-blue?style=for-the-badge&logo=chartdotjs&logoColor=white)


<img src="https://cdn.simpleicons.org/googlefinance/4285F4" width="40" alt="finance icon">

# AAPL: Implied vs Historical Volatility

![Apple](https://dribbble.com/shots/13854667-Colorful-apple-logo-animation)

A from-scratch options pricing project comparing what AAPL's volatility 
**actually was** (historical volatility) against what the options market is 
**currently pricing in** (implied volatility) — the core judgment call behind 
options market making.

**Notebook:** [Options moving Predications.ipynb](./Options%20moving%20Predications.ipynb)

## What this does

- Pulls a year of AAPL daily prices and a live option chain (`yfinance`)
- Computes historical volatility from daily log returns (1-year and rolling 30-day)
- Implements the Black-Scholes pricing formula from scratch, including a 
  dividend-adjusted version
- Inverts Black-Scholes with a numerical root-finder (`scipy.optimize.brentq`) 
  to extract implied volatility directly from real market prices
- Validates the results against Yahoo Finance's own IV figures
- Builds the full implied volatility smile across strikes
- Visualizes the comparison and the skew

## Key findings

**1. Volatility risk premium.** ATM implied volatility (27.8%) sits about 5.7 
percentage points above 30-day realized volatility (22.1%) — the options market 
is currently pricing in more movement than AAPL has actually shown recently.

**2. Volatility skew.** Implied volatility is highest at low strikes (41.4%) 
and falls steadily toward high strikes (26.4%), reflecting the market pricing 
more protection against a sharp drop than a sharp rise.

## Tech stack

Python · pandas · NumPy · SciPy · Matplotlib · yfinance

## Notes

Built and run in a Kaggle notebook. Implied volatility is computed independently 
rather than read from a library, and checked against Yahoo's published IV as a 
validation step — the two show a small, explained gap due to simplifying 
assumptions (flat risk-free rate, European- vs American-style exercise).
