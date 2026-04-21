# liquidityRadar

A quantitative research pipeline that measures, visualizes, and forecasts equity market liquidity across two universes of U.S.-listed stocks using five years of daily price and volume data (April 2021 – April 2026).

## What it does

- Computes the Amihud illiquidity ratio for ten stocks across two universes
- Runs PCA to compress each universe's five illiquidity series into a single latent factor
- Fits an ARIMAX(0,1,1) model using VIX as an exogenous regressor to forecast each factor
- Compares model performance across mega-cap and small/mid-cap universes

## Universes

| Universe | Tickers |
|---|---|
| Mega-cap | AAPL, MSFT, NVDA, GOOGL, AMZN |
| Small/mid-cap | MARA, RIOT, SMCI, SOFI, RIVN |

## Repo structure

```
data_ingestion.ipynb   # Full pipeline: ingestion → EDA → PCA → ARIMAX
data/
  prices.csv           # Adjusted close prices (mega-cap + VIX)
  volume.csv           # Daily share volume (mega-cap)
  sc_prices.csv        # Adjusted close prices (small/mid-cap)
  sc_volume.csv        # Daily share volume (small/mid-cap)
```

## Running the notebook

All data is pre-downloaded in the `data/` folder — no API calls required. Open `data_ingestion.ipynb` and run all cells.

**Dependencies:** `yfinance`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `statsmodels`

```bash
pip install yfinance pandas numpy matplotlib seaborn scikit-learn statsmodels
```
