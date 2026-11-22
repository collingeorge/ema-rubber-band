# EMA Rubber Band: Range, Commit & First Pullback

A TradingView indicator (Pine Script v6) built around the 200 EMA. **Status: under test. Not trading advice.**

## What it models

1. **Range**: price swings above and below a flat 200 EMA and snaps back. The "normal stretch" is a percentile (default 90th) of the asset's own recent distance from the EMA. It does not use ATR. Reaching the normal stretch marks a rubber-band extreme (**SNAP**).
2. **Commit**: after a range, price closes farther from the EMA than normal (default 1.5x the normal stretch). This starts a new direction (**COMMIT**).
3. **First pullback**: price comes back to the EMA without failing. This is the entry zone (**PB1**).
4. **Trend**: the direction holds until price starts crossing the EMA again (**RANGE**) or commits hard the other way (reversal). A close too far back through the EMA while waiting for the pullback marks **FAIL**.

The dashboard shows the bias of three higher timeframes: 15m/1H/4H in scalp mode, 4H/1D/1W in swing mode. It can optionally block fades against the highest timeframe. The mode is picked automatically from the chart timeframe: 15m and lower is scalp.

## Non-repainting

Higher-timeframe values come from closed bars, and signals fire on confirmed bars only. Set alerts to **Once Per Bar Close**.

## Install in TradingView

1. Open the Pine Editor on a chart.
2. Paste the contents of `EMA_Rubber_Band_Commit_Pullback.pine`.
3. Click **Save**, then **Add to chart**.

## Alerts

Commit up/down, First pullback long/short, Range snap long/short, Commit failed, Back to range.

## Files

| File | Contents |
|---|---|
| `EMA_Rubber_Band_Commit_Pullback.pine` | Indicator source (v3) |
