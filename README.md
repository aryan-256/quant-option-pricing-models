# Black-Scholes vs. Monte Carlo

A Jupyter notebook comparing analytical and numerical approaches to European option pricing, plus two extensions exploring implied volatility and portfolio risk.

## Contents

`group_project.ipynb` covers:

1. **Black-Scholes pricing** — closed-form European call price via the standard `d1`/`d2` formula.
2. **Monte Carlo pricing** — prices the same call by simulating terminal stock prices under geometric Brownian motion (risk-neutral GBM), averaging discounted payoffs.
3. **Convergence analysis** — plots the Monte Carlo price against simulation count (100 to 100,000 paths) to show convergence to the Black-Scholes price via the Law of Large Numbers.
4. **Extension 1: Implied volatility smile** — back-solves (via `scipy.optimize.brentq`) for the volatility implied by a mock option chain's market prices, reproducing the characteristic volatility "smile"/"smirk" that violates Black-Scholes' constant-volatility assumption.
5. **Extension 2: Value at Risk (VaR)** — Monte Carlo VaR for a sample portfolio (long stock, short calls) over a 10-day horizon at 95% confidence.
6. **Put-call parity check** — verifies `C - P = S - K·e^(-rT)` using Monte Carlo call/put prices, with a convergence plot showing the arbitrage error shrinking as simulation count grows.

`FM_report.pdf` is the accompanying written report.

## Requirements

```
numpy
scipy
matplotlib
jupyter
```

## Usage

```bash
jupyter notebook group_project.ipynb
```

Run all cells top to bottom; later sections (IV smile, VaR, put-call parity) depend on parameters and functions defined earlier in the notebook.

## Model parameters

Default option/market parameters used throughout: `S0=100`, `K=105`, `T=1.0` year, `r=5%`, `sigma=20%`.
