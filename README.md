# Range Trader Strategy 📈

TradingView strategy for trend trading with MACD entries and ADX filtering. Based on a range detection indicator adapted into a full trading system.

## Overview

This strategy combines MACD momentum detection with ADX trend strength filtering to capture trending moves while avoiding choppy, ranging markets.

**Core concept:** Enter on MACD crossover when ADX confirms trending conditions, exit on multiple configurable conditions.

## Features

### Entry Logic
- **MACD Crossover** (12/26/9) — Momentum signal
- **ADX Filter** (threshold 25) — Trend strength confirmation
- Only enters when both conditions align

### Exit Options
1. **Opposite Sell** — Exit when opposite MACD signal appears
2. **MACD CrossDown** — Exit when MACD crosses below signal
3. **ADX Falls Below Threshold** — Exit when trend weakens
4. **None** — Manual exits only (use with caution)

### Risk Management
- **Stop Loss** — Percentage-based (customizable)
- **Take Profit** — Percentage-based (customizable)
- Optional: disable SL/TP for signal-only exits

### Visual Aids
- Buy/Sell labels on chart (toggle on/off)
- Screenshot in `screenshots/` showing typical setup

## Versions

### v1 (Basic)
**File:** `src/trend_trader_v1.pine`

- Simple MACD + ADX trend following
- Basic SL/TP
- 4 exit modes

### v4 (Advanced)
**File:** `src/trend_trader_v4.pine`

- Enhanced filters
- Improved exit logic
- Swing stop implementation
- Better ranging market avoidance

**Recommended:** Use v4 for live trading

## Parameters

### MACD
| Parameter | Default | Notes |
|-----------|---------|-------|
| Fast Length | 12 | Standard EMA fast |
| Slow Length | 26 | Standard EMA slow |
| Signal Smoothing | 9 | Signal line period |

### ADX
| Parameter | Default | Notes |
|-----------|---------|-------|
| ADX Length | 14 | Standard ADX period |
| DI Length | 14 | Directional Index |
| ADX Threshold | 25 | Min value for trend entry |

### Risk
| Parameter | Default | Notes |
|-----------|---------|-------|
| Stop Loss % | 0.0 | Set > 0 to enable |
| Take Profit % | 0.0 | Set > 0 to enable |

## Installation

1. Choose version (v1 or v4)
2. Copy code from `src/trend_trader_vX.pine`
3. Open TradingView Pine Editor
4. Paste and click "Add to chart"
5. Configure parameters in strategy settings

## Usage

### Recommended Timeframes
- **15m-1H:** Intraday trend catching
- **4H-Daily:** Swing trading
- **Weekly:** Position trading

### Best Markets
- Trending assets (crypto, forex, indices)
- Avoid highly choppy/ranging pairs
- Works well on BTC, ETH, major forex

### Parameter Optimization
- **Aggressive:** ADX threshold 20, tighter SL/TP
- **Conservative:** ADX threshold 30, wider SL/TP
- **Scalping:** Lower timeframes, quick exits

## Performance Tips

1. **Use v4** — more robust filtering
2. **Set realistic SL/TP** — 1-2% SL, 2-4% TP typical
3. **Backtest first** — validate on 6+ months
4. **Adjust ADX threshold** — higher = fewer trades, cleaner signals
5. **Combine with support/resistance** — manual confirmation

## Example Setup

See `screenshots/` for visual reference of:
- Chart layout
- Parameter settings
- Typical entry/exit patterns

## Known Limitations

- Performs poorly in strong ranging markets (even with ADX filter)
- MACD lag can miss fast reversals
- Fixed percentage SL/TP may not suit all volatility regimes

## Improvements (Planned)

- [ ] ATR-based dynamic SL/TP
- [ ] Trailing stop implementation
- [ ] Volume filter
- [ ] Session-based trading hours

## Technical

- **Pine Script:** v4
- **Type:** Strategy (overlay=true)
- **Capital:** 10,000 default
- **Position sizing:** 10% equity per trade

## License

MIT License

## Disclaimer

Educational purposes only. Backtest thoroughly before live trading. Past performance does not guarantee future results.

---

**Status:** Stable  
**Last Updated:** 2026-02-19
