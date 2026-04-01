# Statistical Arbitrage — Basket-Based Mean Reversion

**By Seán Herlihy, Jack Kingston and Patrick Ryan**

A quantitative finance strategy that identifies and exploits pricing inefficiencies among baskets of correlated stocks. This project extends the classic pairs trading framework to multi-asset baskets across several sectors, using a rigorous three-stage statistical testing pipeline to validate each basket before trading.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seanherlihy101/ISMF_Sharpe_Quants/blob/main/Sharpe_Quants_Stat_Arb.ipynb)

---

## Strategy Overview

Rather than trading a single pair of stocks, this strategy constructs spreads from small baskets (4–6 stocks) within the same sector. A basket is only considered tradeable if it passes all three of the following tests.

| Test | What it checks |
|---|---|
| Augmented Dickey-Fuller (ADF) | Stationarity of the spread (p < 0.05) |
| Half-Life | Speed of mean reversion (1 week – 1 year) |
| Hurst Exponent | Mean-reverting behaviour (H < 0.5) |

---

## Results

Backtested on sector-based baskets from 2020–2026:

| Sector | ADF p-value | Hurst | Half-Life | Result |
|---|---|---|---|---|
| **Healthcare** | 0.001 | 0.441 | 17 days | ✅ Very strong |
| Fast Food | 0.020 | 0.430 | 40 days | ✅ Strong |
| Oil Majors | 0.015 | 0.327 | 28 days | ✅ Strong |
| Soft Drinks | 0.593 | 0.219 | 28 days | ❌ Fail |

### Best performing basket — Healthcare

**Assets:** Abbott Laboratories (ABT), Thermo Fisher Scientific (TMO), Danaher Corporation (DHR), Becton Dickinson (BDX)

| Metric | Value |
|---|---|
| Cumulative return | 308.07% |
| Annualised return | 26.49% |
| Sharpe ratio | 1.05 |
| Max drawdown | -18.78% |
| Position changes | 281 |

---

## Installation

```bash
pip install numpy pandas statsmodels hurst matplotlib
```

---

---

