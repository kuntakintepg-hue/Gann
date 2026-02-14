# Gann Master Indicator for TradingView

A comprehensive Pine Script v5 implementation of **W.D. Gann's** trading methods, modernized for today's markets. This indicator combines all major Gann concepts into a single, user-friendly tool with real-time confluence detection, smart alerts, and an interactive dashboard.

---

## Features

### 1. Gann Angles & Fan (`📐`)
Draws Gann's geometric angles from auto-detected pivot highs and lows.

- **Supported angles:** 1×8, 1×4, 1×3, 1×2, **1×1 (45°)**, 2×1, 3×1, 4×1, 8×1
- **Auto-scaling:** Uses ATR to calculate the correct price-per-bar ratio (or set manually)
- **Draw from:** Last major low (rising fan), last major high (falling fan), or both
- The **1×1 angle** is highlighted as the master trend line — price above = bullish, below = bearish

### 2. Square of 9 Levels (`🔢`)
Dynamic support and resistance derived from Gann's Square of 9 spiral calculator.

- Calculates levels using: `Level = (√Price ± n × rotation)²`
- **Cardinal Cross** (0°, 90°, 180°, 270°) — the strongest S/R levels, highlighted with stars
- **Ordinal Cross** (45°, 135°, 225°, 315°) — secondary levels
- Configurable rotation step: 45° through 720°
- Levels update in real-time based on current price

### 3. Time Cycles (`⏰`)
Gann's key time intervals projected from significant pivot points.

- **Available cycles:** 30, 36, 45, 49, 60, 72, 90, 120, 144, 180, 240, 270, 288, 360 bars
- Auto-detects cycle origin from the last major pivot, or set manually
- Major cycles (144, 180, 360) drawn with heavier weight
- Vertical markers show cycle number (e.g., `144(2×)` for second 144-bar cycle)

### 4. Gann Retracement — 1/8th Levels (`📊`)
Gann's division of the price range into eighths (predating Fibonacci).

| Level | Percentage | Significance |
|-------|-----------|--------------|
| 0/8   | 0%        | Period low |
| 1/8   | 12.5%     | Minor |
| 2/8   | 25%       | Key level |
| **3/8** | **37.5%** | **Strong support/resistance** |
| **4/8** | **50%**   | **Most important — the "balance point"** |
| **5/8** | **62.5%** | **Strong support/resistance** |
| 6/8   | 75%       | Key level |
| 7/8   | 87.5%     | Minor |
| 8/8   | 100%      | Period high |

- Toggle between showing all 8 levels or just the key ones (25%–75%)
- 50% level highlighted distinctly as Gann's primary retracement

### 5. Gann Swing Chart (`📈`)
Gann's trend identification method using swing highs and lows.

- Configurable reversal bars (Gann used 2-bar and 3-bar methods)
- Green lines for upswings, red lines for downswings
- Current (unconfirmed) swing leg drawn as a dotted line
- Bar coloring follows the swing trend direction
- Detects and signals swing reversals

### 6. Price-Time Squaring (`⬜`)
Detects when price movement equals time elapsed — Gann's signal for trend changes.

- Measures price units moved vs. bars elapsed from the last major pivot
- Normalizes price using the ATR-based scale factor
- Background highlights bars where Price ≈ Time (within configurable tolerance)
- Tolerance adjustable from 0.5% to 20%

### 7. Vibration / Harmonic Levels (`🔊`)
Gann's Law of Vibration: prices vibrate at frequencies related to musical harmonics.

- **Octave ratios:** ×2, ×4, ÷2, ÷4 (strongest harmonic levels)
- **Fifth ratios:** ×1.5, ÷1.5
- **Third ratios:** ×1.333, ÷1.333
- Base price options: current close, period high, period low, or custom value
- Only draws levels within the visible price range

### 8. Confluence Detection (`📋`)
The most powerful feature — finds zones where multiple Gann tools converge.

- Scans all active tools: Square of 9, Retracement, Price-Time Squaring, Time Cycles, Swing Reversals
- Marks confluence zones with a diamond marker and yellow background
- Configurable minimum tools threshold (default: 2)
- Dashboard shows which tools are converging
- **More tools converging = higher probability setup**

### 9. Smart Dashboard
Real-time information panel showing:

- Current trend direction (from swing chart)
- Nearest Square of 9 support and resistance
- Price-Time squaring status
- Time cycle status
- Confluence count and active tools
- Bars elapsed from last pivot

### 10. Alert System
Five configurable alerts for all Gann signals:

| Alert | Trigger |
|-------|---------|
| Sq9 Level Touch | Price within 0.3% of a Square of 9 level |
| Time Cycle Hit | Current bar lands on an active cycle |
| Price = Time | Price-Time squaring detected |
| Swing Reversal | Gann swing chart reversal |
| Confluence Zone | Multiple tools converging |

---

## Installation

1. Open **TradingView** and navigate to any chart
2. Click **Pine Editor** at the bottom of the screen
3. Delete any existing code and paste the contents of `GannMasterIndicator.pine`
4. Click **Add to Chart**
5. Open the indicator settings (gear icon) to customize

---

## Recommended Settings by Market

### Stocks / ETFs
| Setting | Value |
|---------|-------|
| Pivot Length | 10–20 |
| Auto-Scale | On |
| Sq9 Rotation | 0.25 (90°) |
| Swing Bars | 2 |
| Retracement Lookback | 100–200 |

### Forex
| Setting | Value |
|---------|-------|
| Pivot Length | 5–10 |
| Auto-Scale | On |
| Sq9 Rotation | 0.125 (45°) |
| Swing Bars | 2 |
| Time Cycles | 30, 60, 90, 144 |

### Crypto
| Setting | Value |
|---------|-------|
| Pivot Length | 10–15 |
| Auto-Scale | On |
| Sq9 Rotation | 0.25–0.5 |
| Swing Bars | 3 |
| Vibration Levels | Enabled (Octaves) |

### Futures / Commodities
| Setting | Value |
|---------|-------|
| Pivot Length | 10 |
| Manual Scale | Match Gann's original (e.g., 1¢/day for grains) |
| Sq9 Rotation | 0.25 |
| Time Cycles | 60, 90, 144, 180, 360 |

---

## How to Use — Quick Start

### Finding Support & Resistance
1. Enable **Square of 9** and **Retracement Levels**
2. Look for price zones where Sq9 and 1/8th levels cluster together
3. The **confluence detector** will automatically mark these zones

### Identifying Trend Direction
1. Enable the **Swing Chart**
2. Green bars = bullish swing, Red bars = bearish swing
3. The **1×1 Gann Angle** acts as a dynamic trend line — price above = bullish

### Timing Entries
1. Enable **Time Cycles** (start with 60, 90, 144, 180, 360)
2. Watch for cycle dates that align with support/resistance levels
3. **Price-Time Squaring** gives additional timing confirmation

### High-Probability Setups
Look for the **confluence diamond (C)** — this means 2+ Gann tools are signaling at the same price and time. The more tools that converge, the stronger the signal.

---

## Gann Theory Reference

### The 1×1 Angle
Gann considered the 1×1 (45°) angle the most important line on any chart. It represents perfect balance between price and time. When price is above the 1×1 rising from a low, the trend is bullish. When below, bearish.

### Square of 9
A spiral of numbers starting from 1 at the center. Each ring adds 8 numbers. The cardinal and ordinal crosses of this spiral produce powerful support/resistance levels when applied to price via the square root formula.

### Natural Cycles
Gann observed that markets move in natural cycles related to geometry and astronomy:
- **90 days** (one quarter/season)
- **144 days** (a Fibonacci number Gann used heavily)
- **180 days** (half year)
- **360 days** (full year/circle)

### Price-Time Squaring
When the price range from a pivot equals the time elapsed (in the proper scale), the market reaches a point of balance and is likely to reverse. This is one of Gann's most powerful timing tools.

### Law of Vibration
Gann believed that every stock or commodity vibrates at its own rate. By finding the fundamental vibration (frequency), you can predict future movements. This indicator implements this through harmonic ratios applied to price.

---

## Inputs Reference

| Group | Input | Default | Description |
|-------|-------|---------|-------------|
| General | Pivot Detection Length | 10 | Bars on each side for pivot confirmation |
| General | Auto-Scale Angles | On | ATR-based price/bar scaling |
| General | ATR Length | 14 | Period for ATR calculation |
| Angles | Enable Gann Angles | On | Master toggle for angle lines |
| Angles | Draw From | Both | Low, High, or Both pivots |
| Angles | Extend Lines | 100 | How far angles project forward |
| Sq9 | Enable Square of 9 | On | Master toggle for Sq9 levels |
| Sq9 | Levels Above & Below | 4 | Number of Sq9 levels each direction |
| Sq9 | Rotation Step | 0.25 | Angular increment (0.125=45° to 2.0=720°) |
| Cycles | Enable Time Cycles | On | Master toggle for cycle lines |
| Cycles | Cycle Origin | Auto | Auto-detect from pivot or manual |
| Retrace | Enable Retracement | On | Master toggle for 1/8th levels |
| Retrace | Lookback Period | 100 | Bars to find the price range |
| Swing | Enable Swing Chart | On | Master toggle for swing overlay |
| Swing | Reversal Bars | 2 | Consecutive bars for reversal |
| P=T | Enable Price=Time | On | Master toggle for squaring |
| P=T | Tolerance | 5% | How close P and T must be |
| Vibration | Enable Vibration | Off | Master toggle for harmonic levels |
| Dashboard | Show Dashboard | On | Information panel toggle |
| Confluence | Highlight Confluence | On | Zone highlighting |
| Confluence | Min Tools | 2 | Minimum tools for confluence signal |

---

## License

This Pine Script source code is subject to the terms of the [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/).
