<img width="1351" height="703" alt="Screenshot 2026-09-21 101016" src="https://github.com/user-attachments/assets/392be1d5-3b61-4364-a032-3d334f610ecb" />
# Crypto Market Pulse

A single-page Power BI dashboard giving a live, at-a-glance snapshot of the top 10 cryptocurrencies by market capitalization — price movement, market cap distribution, and supply metrics in one view.
---

## Overview

**Crypto Market Pulse** pulls real-time market data (price, market cap, volume, supply, and 24-hour performance) for the top 10 coins by market cap and visualizes it as a single-screen dashboard, designed for quick scanning rather than deep historical analysis.

## Data Source

- **Table:** `Crypto_Market_Data`
- **Source type:** Live market data API (CoinGecko-style feed), refreshed on load
- **Grain:** One row per coin (10 rows), snapshot as of the last refresh — not a historical time series
- **Key fields:** `symbol`, `name`, `current_price`, `market_cap`, `market_cap_rank`, `total_volume`, `high_24h`, `low_24h`, `price_change_percentage_24h`, `circulating_supply`, `total_supply`, `last_updated`
- **Derived columns:** `24H Price Range`, `Price Change Status` (Gainer/Loser), `24H Volatility %`, `Market Cap Category` (Large/Mid/Small Cap), `Price Change Category` (High Growth/Moderate Growth/Decline)

## Dashboard Contents

**KPI cards**
| Card | Measure |
|---|---|
| Total 24H Price Change | Sum of `price_change_24h` across all 10 coins |
| Total Market Cap | Sum of `market_cap` (~2.53T) |
| Sum of 24H Price Range | Sum of `24H Price Range` |
| Total Trading Volume | Sum of `total_volume` (~153.19bn) |

**Visuals**
- **Coin Supply (clustered bar):** `Sum of total_supply` and `Sum of market_cap` grouped by `Price Change Category` (Moderate Growth / Decline / High Growth)
- **Total Market Cap and Count of Symbol (bar):** `market_cap` and coin count broken down by `Market Cap Category` (Large / Mid / Small Cap)
- **Crypto Count and Count of Year (donut):** distribution of the 10 coins by quarter

## Key Insights

- **BTC dominance:** Bitcoin alone accounts for ~64% of the tracked market cap
- **Market sentiment:** 9 of 10 coins were gainers in the last 24 hours, 1 loser
- **Market cap split:** 3 Large Cap, 4 Mid Cap, 3 Small Cap coins
- **Growth profile:** 2 coins in "High Growth," 7 "Moderate Growth," 1 "Decline"

## Tech Stack

- **Power BI Desktop** — report authoring, DAX measures, data modeling
- **Power Query** — API connection and transformation
- Custom dark-themed dashboard background (1920×1080)

## How to Use

1. Open `api.pbix` in Power BI Desktop
2. Refresh the data (Home → Refresh) to pull the latest market snapshot
3. Use the report page to review KPIs and chart breakdowns at a glance

## Notes / Limitations

- This is a **point-in-time snapshot**, not a time-series — trend/line charts are not meaningful unless refreshes are scheduled and history is retained
- Only the top 10 coins by market cap are tracked in the current model

## Author

**Astha Anand Pal**
[LinkedIn](https://linkedin.com/in/asthapaldata) · [GitHub](https://github.com/Tecpandas) · [Kaggle](https://kaggle.com/asthapal)
