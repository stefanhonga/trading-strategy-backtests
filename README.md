# Trading Strategy Backtests ENG

Python-based backtesting models that test classic technical trading strategies against historical market data and compare their performance to a buy-and-hold benchmark.

## Strategies

### Single Moving Average (`MA_annotated.ipynb`)
Tests whether buying when price is above its moving average and selling when below produces better returns than holding. Includes a grid search across MA windows (10–500 days) to find the historically optimal lookback period.

### Dual Moving Average Crossover (`MA_Crossover_annotated.ipynb`)
Uses a fast/slow MA pair — goes long when the fast MA crosses above the slow MA (bullish momentum) and short when it crosses below (bearish). Includes a brute-force search across all fast/slow combinations to find the best-performing pair.

### RSI Mean Reversion (`RSI_v2_annotated.ipynb`)
A stateful RSI strategy that enters long when RSI drops below the oversold threshold and holds until RSI crosses above the overbought threshold (and vice versa for shorts). This models how a trader would actually use RSI — holding positions through the middle zone rather than flipping on every bar.

## How It Works

Each notebook follows the same structure:
1. **Download data** — historical prices via Yahoo Finance (`yfinance`)
2. **Calculate indicator** — SMA, dual SMA, or RSI
3. **Generate signals** — rule-based long/short/cash positions, shifted by 1 day to prevent look-ahead bias
4. **Compare returns** — cumulative strategy returns vs. buy-and-hold, plotted side by side

## Tech Stack

- Python 3
- `pandas` — data manipulation
- `numpy` — numerical operations
- `yfinance` — market data
- `matplotlib` — visualization

## Known Limitations

- No transaction costs or slippage modeled
- No risk-adjusted metrics (Sharpe ratio, max drawdown) — only cumulative return
- Grid search results are subject to overfitting — optimal historical parameters may not generalize forward
- Strategies tested on single assets; no portfolio-level analysis

## Author

Stefan Honga — Economics student at the University of Tartu.
