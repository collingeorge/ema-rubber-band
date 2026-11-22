# EMA Rubber Band: Range, Commit & First Pullback

A TradingView indicator (Pine Script v6) built around the 200 EMA. **Status: under test. Not trading advice.**

## What it marks

| Mark | Meaning |
|---|---|
| **SNAP** | Range: price reached the normal stretch from a flat 200 EMA (rubber-band extreme). |
| **COMMIT** | After a range, price closed farther from the EMA than normal (default 1.5x). |
| **PB1** | First pullback to the EMA after a commit. |
| **TPB** | Trend pullback: EMA falling/rising, first two higher timeframes agree, price stretched beyond 1x normal, then pulled back to the red/green zone line (0.75x normal from the EMA). Needs an SMI dot within 3 bars (no dot = no mark). Hidden when an SNI mark fires on the same bar. One per 12 bars. |
| **SNI▼ / SNI▲** | Trend: SMI red/green alert dot while the 200 EMA slope is steeper than X (default 0.10), the market is not ranging, **and price touched the red (short) / green (long) zone line within the last 5 bars**. |
| **RNG▼ / RNG▲** | (v5) Range: SMI red dot within 5 bars of a touch of the upper normal-stretch band (short), or green dot after a touch of the lower band (long). One per 12 bars. |
| **FAIL / RANGE** | Commit failed / trend ended back in a range. |

**Ranging vs trending (v5).** For SMI marks the market counts as ranging when any of these hold: at least 3 EMA crosses in the last 96 bars on scalp charts (8 hours on 5m) or 120 bars on swing charts, the EMA slope is flatter than X, or price crossed the EMA in the last 48 bars. RNG fades are also blocked against a steep EMA (no RNG▲ while it falls steeply, no RNG▼ while it rises steeply). SNI marks have a 12-bar cooldown. Every short or long mark needs an SMI dot. In a trend the zone line (red below a falling EMA, green above a rising one) is drawn on the chart; a pullback that never reaches it does not count. While ranging, only RNG marks fire; SNI and TPB marks are off. While trending, SNI and TPB marks fire and RNG marks are off.

"Normal stretch" is a percentile (default 90th) of the asset's own recent distance from the EMA. No ATR.

## SMI link (needed for SNI and RNG marks)

Pine can read another indicator's outputs on the same chart. In this indicator's settings, under **SNI dot + EMA slope**:

- **SNI red dot (short) plot** → `SMI: [Alert 1] Crossing down shape`
- **SNI green dot (long) plot** → `SMI: [Alert 1] Crossing up shape`

TradingView resets these two to `Close` (off) whenever the script source is updated, so set them again after each update.

## Dashboard

Shows mode (Swing above 15m charts, Scalp at 15m and below), three higher-timeframe biases, 200 EMA slope, EMA crosses, current stretch, state, and the allowed play.

## Non-repainting

Higher-timeframe values come from closed bars; marks fire on confirmed bars. Set alerts to **Once Per Bar Close**.

## Install

Pine Editor → paste `EMA_Rubber_Band_Commit_Pullback.pine` → Add to chart.

## Alerts

Commit up/down, First pullback long/short, Trend pullback long/short, SNI dot + slope long/short, Range dot long/short, Range snap long/short, Commit failed, Back to range.
