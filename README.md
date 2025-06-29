# Crypto-Liquidation-Cascades
Strategy to capitalize on liquidation cascades.
## Strategy Overview
This project implements a statistical arbitrage strategy that exploits **forced selling events** in the crypto markets — known as **liquidation cascades**. These occur when rapid price drops trigger leveraged traders' stop-outs, creating temporary mispricings that often revert.

> **Core Idea**: Identify liquidation-driven crashes across multiple assets, enter during panic, and profit from the mean reversion.

---

## Methodology

### 1. **Event Detection**
- Multi-timeframe price drops (1h and 2h)
- Volume spikes (top 5% percentile)
- Cross-asset correlation: ≥ 3 assets crashing simultaneously

### 2. **Trade Entry**
- Long entries triggered during high-volume cascade drops
- Entry at close of crash candle (simulated with shift)

### 3. **Trade Exit**
- Simple hold for 1–2 hours post entry (forward return logic)
- No stop-loss; profit is driven by mean-reverting bounce

---

## Backtest Results (Sample time period: 2023-01-01 to 2024-01-31)

- **Total trades**: 98
- **Total return**: 60.4%
- **Mean return per trade**: ~0.62%  
- **Max Drawdown**: -18.67%  
- **Sharpe Ratio**: 2.11
  
- **Annualized Alpha**: 0.0049
---

## Further Backtest Result Examples

| Time Period        | Market Regime     | Sharpe | Avg Return | Trades | Alpha (Annualized)             |
|--------------------|-------------------|--------|------------|--------|--------------------------------|
| Mar–Apr 2020       | Bear (COVID)      | 60.72  | 2.88%      | 30     | 0.0764                         |
| May–Dec 2020       | Bullish Recovery  | 2.44   | 1.29%      | 47     | 0.0057                         |
| Jan–Dec 2021       | Bull              | 2.25   | 1.64%      | 148    | 0.0223                         |


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
Market crashes are sometimes **overreactions driven by leverage**. This strategy looks to profit from those overreactions causing temporary artifical crashes.

---

## Contact
Have feedback or want to collaborate? Contact kazanitish@gmail.com
