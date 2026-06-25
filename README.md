# NSE DTDTF Swing Trader

Dual Trend Dual Timeframe (DTDTF) automated paper trading system for NSE equities.

## Strategy

**Entry:** Dual trend confluence on both Daily (15-bar) and Weekly (12-bar) timeframes.
- Weekly already green + Daily just turned green → enter
- Daily already green + Weekly just turned green → enter

**Exit:**
- Daily trend flips bearish AND price closes below daily lower line
- Stop loss hit (10% below entry)

**Universe:** Nifty 250 (230 symbols, healthcare excluded)

## Infrastructure

- DigitalOcean Functions (scheduled daily at 09:10 IST on weekdays)
- GitHub as state layer (positions + trade log CSVs)
- Gmail SMTP for daily HTML email reports

## Files

- `data/watchlist.csv` — Nifty 250 watchlist (Symbol, Industry, IsBanking)
- `data/positions_dtdtf.csv` — open paper positions
- `data/dtdtf_trade_log.csv` — completed trade history
- `functions/packages/nse_dtdtf/daily_run/__main__.py` — main pipeline
