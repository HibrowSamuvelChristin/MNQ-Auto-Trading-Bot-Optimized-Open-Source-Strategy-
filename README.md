# MNQ Algorithmic Trading Bot (Optimized from Open Source)

This repository documents my process of debugging and improving an open-source PineScript trading bot designed for the **MNQ (Micro Nasdaq Futures)** market.  
The base code was publicly available, but I used **ChatGPT-assisted debugging and optimization** to make it profitable under realistic backtest conditions using **TradingView’s Strategy Tester**.

---

## ⚙️ Overview
- **Platform:** TradingView (PineScript v5)  
- **Symbol:** MNQ1!  
- **Testing Period:** Mar 2019 – Oct 2025  
- **Initial Deposit:** 10,000 USD  
- **Risk Per Trade:** 100 USD  
- **Type:** Intraday/Positional Futures Strategy  
- **Goal:** Fix logic errors & optimize entry/exit + risk filters

---

## 📈 Strategy Performance Summary
- **Total P&L:** +25,926.50 USD (+259.27%)  
- **Profit Factor:** 1.205  
- **Total Trades:** 1,219  
- **Profitable Trades:** 38.8%  
- **Max Equity Drawdown:** 6,423.00 USD (40.25%)  
- **Max Contracts Held:** 28  
- **Backtest Duration:** 6.5 years  

Screenshots of the full results are available in the `/media` folder.

---

## 🔍 What Was Fixed / Improved
- Corrected **stop-loss logic** that caused premature exits.  
- Removed redundant **“force trade stop”** parameter which prevented valid setups.  
- Adjusted **ATR length and multiplier** for MNQ volatility conditions.  
- Improved **volume filter** and trend confirmation logic.  
- Balanced **long/short** conditions to handle sideways market structure better.  
- Added **consistent position sizing** with a fixed 100 USD risk per trade.

---

## 🧠 Tools & Skills Used
- **TradingView PineScript (v5)** for strategy development and debugging  
- **Quantitative analysis** and trade performance evaluation  
- **Risk management** and fixed-dollar position sizing  
- **Strategy optimization** using TradingView Strategy Tester

---

## 🧩 Code Sample
A partial version of the optimized PineScript is shared in [`main_sample.pine`](./main_sample.pine).  
For intellectual-property reasons, the **core entry/exit logic** has been removed.

```pinescript
////@version=5
strategy("Modified TJR asia session sweep", "Modified Asia Sweep", overlay=true, max_lines_count=500, max_labels_count=500)

// Input settings
show_asian = input.bool(true, "Show Asian Session", group="Visual Settings")
show_london = input.bool(true, "Show London Session", group="Visual Settings")
show_swing_points = input.bool(true, "Show Asian Swing Points", group="Visual Settings")
show_market_structure = input.bool(true, "Show Market Structure", group="Visual Settings")
show_bos = input.bool(true, "Show Break of Structure", group="Visual Settings")


// Core strategy logic omitted for confidentiality

