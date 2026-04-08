# Earth Scanner 🌍📡
### Regime-Conditioned Cross-Asset Impulse Modeling & Expected Alpha
7th Dimension Markets — Version 3.0, March 2026

#  [🚀 Try Earth Scanner Free →](httpsearth-scanner-v2-xnxaxfjvvnarezf3h228mu.streamlit.app)  &nbsp;&nbsp; [Subscribe to Pro →](httpsbuy.stripe.com28E5kFdwn2kF7pY7v23cc00)  &nbsp;&nbsp; [Follow on X →](httpsx.com7thDimensionM)  &nbsp;&nbsp; [Substack →](https7thdimensionmarkets.substack.com)

---

Traditional correlation matrices fail to provide a tradable edge because they continuously measure everyday market noise. The Earth Scanner is a proprietary, quantitative Shock Engine designed to measure cross-asset reactions exclusively during statistically significant volatility events.

By executing a four-world analysis spanning Global Macro, Cryptocurrencies, US Equities, and Sector Rotation — 700+ assets tracked daily — the model abandons continuous correlation in favor of discrete impulse detection with walk-forward validated confidence scoring.

---

## 🧠 Core Methodology

The engine operates on a Regime-Conditioned Impulse framework

1. Baseline Calibration — Dynamically calculates a rolling mean and standard deviation for each asset to define normal market conditions. Baseline windows are adaptive per asset class 90 days for macro and equities, 15 days for crypto altcoins.

2. Shock Detection — Filters out standard market noise by isolating extreme volatility events (Z-score ≥ 1.5) in a primary Driver Asset.

3. Lead-Lag Event Study — Measures the subsequent directional drift (the Ripple) in a designated Reaction Asset over a forward-looking horizon (default T+5 days) to calculate Expected Alpha
   ```
   E[alpha] = (Sum of Reaction Asset Returns over Horizon)  N
   ```

4. Walk-Forward Stability — Partitions historical data into chronological folds to test directional consistency across different macroeconomic regimes, generating a strict Confidence Score (0–100)
   ```
   Confidence = 100 × (0.65 × SignRate + 0.35 × MagRetention) × FoldPenalty × SamplePenalty
   ```

5. Regime Detection — Classifies the current macro environment in real time (Risk-On, Risk-Off, USD Squeeze, Inflation Pulse, Gold Bid  Safety, Deflation  Growth Scare) using Z-score signals from regime proxy assets. The regime label updates every scan and provides the interpretive context for all shock signals.

6. Volume Confirmation — Intraday OHLCV data (1-hour bars, 30-day rolling window) is compared against the 10-day volume moving average. Above-average volume on a shock day signals institutional participation.

### Signal Quality Hierarchy
```
High Z-score  +  High Confidence Score  +  Above-Average Volume  =  Highest Conviction Setup
```

---

## ⚡ Key Features

### Four-World Coverage
 World  Universe  Assets  Baseline 
-----------------------------------
 World 1 Macro  USD, Commodities, FX, Global Indices  31  90 days 
 World 2 Alt-Crypto  150 altcoins, full OHLCV from 2020  150+  15 days 
 World 3 S&P 500  Full US equity universe  503  90 days 
 World 4 Sectors  GICS sector ETFs, 25 years of history  11  90 days 

### Analytical Toolkit

Advanced Mode — 6 Tabs
- ⚡ Shock — Live Z-score scanner with severity tiers (Mild  Moderate  Severe  Extreme) and regime classification
- 🌊 Cross-Asset Impulse Matrix — Heatmaps identifying leading indicators, sector amplification, and decoupling assets across any Driver × Reaction pair
- 📡 Signal Decay Radar — Plots the temporal decay curve of alpha to pinpoint the exact day a shockwave peaks before dissipating into noise
- 📊 Macro — OHLCV price charts with regime-band overlays, shock event markers, and hotcold intraday data source indicator
- 💼 Capital Efficiency Backtester v2 — Event-driven strategy simulator with trailing stop exits, multi-driver entry logic (ANY  ALL  MAJORITY), transaction cost modeling (0–55 bps), and Monte Carlo statistical validation
- 🔮 Forecast — Pre-shock Z-score warning, Expected Alpha fan charts with P10P25P75P90 confidence bands, outcome distribution histograms, and intraday volume confirmation
- ⚡ Conviction Leaderboard — Ranks all Reaction Assets by Walk-Forward Confidence Score for any Driver. Default drivers load instantly from the nightly pre-computed cache

Beginner Mode — 4 Tabs
For non-traders, a simplified layout translates Z-scores, regime labels, and shock data into plain-English market summaries. Markets are nervous today instead of Risk-Off regime, VXX Z=2.3.

---

## 🌙 Nightly Automation Pipeline

A fully automated GitHub Actions workflow runs at 400 AM UTC every day across all four worlds

1. Pre-flight freshness check — identifies stale worlds before fetching
2. Price data fetch — yfinance (Worlds 1, 3, 4) + Binance API (World 2)
3. Shock detection — adaptive Z-score engine per world; Z ≥ 3.0 triggers email alert
4. Conviction cache — walk-forward leaderboards pre-computed and written to Supabase
5. Distribution — daily X post with top 3 shocks + Substack report (Fridays + extreme shock days)

---

## 📈 Case Study Adobe → Nvidia Shockwave (2021–2026)

The central thesis of Earth Scanner is capital efficiency — not maximizing raw return at 100% market exposure, but extracting meaningful alpha while spending the majority of time in cash.

When Adobe (ADBE) experiences a Z-score shock (Z ≥ 1.5), capital has historically rotated aggressively into Nvidia (NVDA). Backtested over 5 years with a 16% trailing stop exit and real-world transaction costs (10 bps round-trip)

 Metric  Value 
---------------
 Strategy Return (Net, after costs)  +405.2% 
 Time in Market  37.0% — cash the other 63% 
 Efficiency Ratio  11.0x return per unit of market exposure 
 Sharpe Ratio (Net)  0.78 
 Max Drawdown  51.1% 
 Win Rate  53.3% 
 Total Trades  40 
 Avg Hold Period  19.1 days 
 Buy & Hold NVDA (100% exposure)  +3,251.5% 

The key number is 11.0x. The strategy generated 11 times more return per unit of market exposure than simply holding NVDA. For the 63% of the timeline when the strategy was in cash, that capital was protected from drawdowns and available for risk-free yield — a compounding advantage that raw return figures do not capture.

---

## 🏗️ Architecture

### Free vs. Pro

  Free  Pro 
---------
 Worlds  World 1 only  All 4 worlds (700+ assets) 
 Auth  None  Google OAuth 
 Access Gate  Terms of Service  Active Stripe subscription + TOS 
 Price  Free forever  $99mo 
 Founding Member Price  —  $79mo — first 50 members lock this in forever 

 🔒 Founding Member spots are limited. The first 50 subscribers lock in $79.99mo permanently. Regular price is $99.99mo. [Subscribe →](httpsbuy.stripe.com28E5kFdwn2kF7pY7v23cc00)

### Database (Supabase PostgreSQL)

 Table  Contents 
-----------------
 `prices_daily__{world}`  Full OHLCV history — primary read source for all analysis 
 `prices_intraday__{world}`  1-hour bars, 90-day rolling retention — volume confirmation 
 `conviction_cache`  Pre-computed walk-forward leaderboards, updated nightly 
 `subscribers`  Active Stripe subscriber emails — Pro access control 

---

## 🛠️ Tech Stack

 Layer  Technology 
-------------------
 Frontend  Streamlit (free app + Pro app) 
 Data Processing  Python, Pandas, NumPy, SciPy, scikit-learn 
 Visualization  Plotly, Matplotlib 
 Database  Supabase (PostgreSQL) 
 Price Data  yfinance, Binance API 
 Deployment  Streamlit Cloud 
 Automation  GitHub Actions (nightly, 4 AM UTC) 
 Payments  Stripe + Vercel serverless webhook 
 Auth  Google OAuth via Streamlit 
 Alerts  Tweepy (XTwitter), SendGrid (email), Substack 

---

## 📄 Documentation

For the complete mathematical framework, historical exhibits across all four worlds, the confidence scoring derivation, and full backtesting methodology, refer to The Ripple Effect v3.0 white paper included in this repository.

---

## ⚠️ Disclaimer

Earth Scanner is an analytical and research tool. Nothing in this platform or its associated documentation constitutes investment advice. All historical performance data is for informational purposes only. Past performance does not guarantee future results.
