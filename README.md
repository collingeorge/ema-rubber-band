# EMA Rubber Band: Range, Commit & First Pullback

A TradingView indicator (Pine Script v6) built around the 200 EMA. **Status: under test. Not trading advice.**

## What it marks

| Mark | Meaning |
|---|---|
| **SNAP** | Range: price reached the normal stretch from a flat 200 EMA (rubber-band extreme). |
| **COMMIT** | After a range, price closed farther from the EMA than normal (default 1.5x). |
| **PB1** | First pullback to the EMA after a commit. |
| **TPB** | Trend pullback (v4): EMA falling/rising, first two higher timeframes agree, price stretched beyond 1x normal, then pulled back to within 0.75x of the EMA. No prior range needed. One per 12 bars. |
| **SNI▼ / SNI▲** | (v4) SMI red/green alert dot while the 200 EMA slope is steeper than X (default 0.10). |
| **FAIL / RANGE** | Commit failed / trend ended back in a range. |

"Normal stretch" is a percentile (default 90th) of the asset's own recent distance from the EMA. No ATR.

## SMI link (needed for SNI▼ / SNI▲)

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

Commit up/down, First pullback long/short, Trend pullback long/short, SNI dot + slope long/short, Range snap long/short, Commit failed, Back to range.
