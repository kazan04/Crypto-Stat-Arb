# Crypto-Liquidation-Cascades
Strategy to capitalize on liquidation cascades.
## Strategy Overview
This project implements a statistical arbitrage strategy that exploits forced selling events in the crypto markets — known as liquidation cascades. These occur when rapid price drops trigger leveraged traders' stop-outs, creating temporary mispricings that often revert.

> **Core Idea**: Identify liquidation-driven crashes across multiple assets, enter during panic, and profit from the mean reversion.

---

## Methodology

### 1. **Event Detection**
- Multi-timeframe price drops:
    5% drop in 1 hour OR 8% extreme drop in 1 hour
    Cascade pattern: 8% drop over 2 hours with <3% drop in most recent hour
- Volume spikes (top 5% percentile for strong/extreme drops; top 10% for cascades)
- Cross-asset correlation: ≥ 3 assets crashing simultaneously

### 2. **Trade Entry**
- Long entries triggered during high-volume cascade drops
- Entry at close of crash candle (simulated with shift)

### 3. **Trade Exit**
- If 1-hour forward return > 2%: Hold for 1 hour to capture quick gains
- Otherwise: Hold for 2 hours to allow for longer-term momentum

---

## Backtest Results (Sample time period: 2023-01-01 to 2024-01-31)

- **Total trades**: 98
- **Total return**: 50.71%
- **Mean return per trade**: ~0.52%  
- **Max Drawdown**: -20.45%  
- **Sharpe Ratio**: 1.81
  
- **Annualized Alpha**: 0.0049
---

## Further Backtest Result Examples (can edit st and et variables in code to test)

| Time Period        | Market Regime     | Sharpe | Avg Return | Trades | Alpha (Annualized)             |
|--------------------|-------------------|--------|------------|--------|--------------------------------|
| Mar–Apr 2020       | Bear (COVID)      | 5.927  | 2.18%      | 30     | 0.0764                         |
| May–Dec 2020       | Bullish Recovery  | 3.846  | 1.038%     | 47     | 0.0057                         |
| Jan–Dec 2021       | Bull              | 2.90   | 0.909%     | 148    | 0.0223                         |


## Libraries Used
- `pandas`, `numpy`, `matplotlib`
- `scipy.stats`
- `Binance API`

---

## Files
- `liquidation_strategy.ipynb`: Full strategy notebook
- `README.md`
---

## Key Takeaway
Market crashes are sometimes overreactions driven by leverage. This strategy looks to profit from those overreactions causing temporary artifical crashes.

---

## Contact
Have feedback or want to collaborate? Contact kazanitish@gmail.com
