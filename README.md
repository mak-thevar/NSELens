# 📡 NSELens

> A Claude skill that generates verified, multi-dimensional Indian stock research reports for the next trading day — with live prices, analyst targets, GTT setups, and confidence scoring.

Built for Indian retail investors who are tired of stock tips without data. NSELens does the research, verifies every price from named sources, and delivers a structured report you can act on.

---

## What it does

Give it a simple prompt like **"top 5 Indian stocks for tomorrow"** and NSELens will:

1. **Scan the macro environment** — Nifty level, VIX, crude oil, USD/INR, RBI stance
2. **Screen Nifty 100** for stocks that have declined 10%+ from recent highs with rebound potential
3. **Verify every price** from named sources (Dhan, Tickertape, Investing.com, NSE India, etc.) — no estimates, no memory, no hallucinated numbers
4. **Run deep research** per stock across 8 dimensions:
   - Live price + 52-week range
   - Fundamentals (PE, PB, margins, debt, promoter pledging)
   - Upcoming earnings date
   - Analyst targets (named brokerages only)
   - Relative strength vs Nifty
   - News + FII/DII activity
   - Retail sentiment
   - Technical levels (support, resistance, DMA, RSI)
5. **Score each stock** on a 4-dimension confidence model (Fundamentals / Technicals / Sentiment / Catalyst)
6. **Calculate Risk/Reward ratio** for every pick
7. **Build a GTT setup or Entry Zone** based on your investment horizon
8. **Render a clean, structured report** — full cards for top 3/5, table + compact cards for top 10

---

## Example prompts

```
top 5 Indian stocks for tomorrow
give me top 3 rebound picks for this week
top 10 NSE stocks with GTT setup
best Indian stocks to buy right now
```

NSELens will ask you one friendly question before starting:
> *"When are you hoping to see this profitable — 3 months, 6 months, a year, or longer?"*

Your answer changes the entire output format:

| Horizon | Format |
|---|---|
| 3 months / 6 months | GTT setup (trigger, target, stop loss, R:R) |
| 1 year / 2 years | Entry zone + price target + accumulation guidance |

---

## Sample output structure

```
Market Pulse · Nifty: 22,713 (▲0.15%) · VIX: 13.67 · Crude: $88/bbl · USD/INR: 84.2 · RBI: Neutral

① HDFC Bank · NSE: HDFCBANK · Private Banking · Large Cap
CMP: ₹750.90 (Dhan, Apr 4) | 52W: ₹726–₹1,020 | Down 26% from high
Confidence: Fundamentals ✓ | Technicals ✓ | Sentiment ✓ | Catalyst ✓ → 4/4 = HIGH

GTT Setup
Trigger: ₹745 → Target: ₹815 (+9.4%) → SL: ₹705 (-5.4%) | R:R: 1.9x
```

---

## Confidence scoring model

Every pick is scored across 4 dimensions:

| Dimension | What it checks |
|---|---|
| **Fundamentals** | Revenue growth, PE, margins, debt, promoter pledging <30% |
| **Technicals** | Near support, RSI <45, below 200 DMA |
| **Sentiment** | Analyst consensus Buy/Strong Buy, no negative news in 30 days |
| **Catalyst** | Upcoming earnings within 60 days, sector tailwind, corporate event |

- 4/4 → HIGH
- 3/4 → MEDIUM-HIGH
- 2/4 → MEDIUM
- 1/4 or below → Stock is discarded

---

## Hard rules built into the skill

- **No unverified prices** — every CMP must come from a named source with a date
- **No hallucinated targets** — analyst targets only from named brokerages found in search
- **Promoter pledging always shown** — flagged at >30%, warned at >50%
- **Minimum 8% upside** from trigger price required for inclusion
- **Nifty 100 universe only**
- **GTT format only for horizons up to 1 year** (matching NSE/BSE GTT validity)

---

## Installation

1. Download [`NSELens.skill`](./NSELens.skill) from this repo
2. Go to [claude.ai](https://claude.ai) → Settings → Skills
3. Upload the `.skill` file
4. Start a new conversation and try: **"top 5 Indian stocks for tomorrow"**

---

## Parameters

| Parameter | Options | Default |
|---|---|---|
| Number of picks | 3, 5, or 10 | 5 |
| Universe | Nifty 100 | Nifty 100 |
| Horizon | 3M / 6M / 1Y / 2Y | Asked interactively |
| Output format | Full cards (3/5) · Table + compact (10) | Auto |

---

## Disclaimer

> This skill is for informational and educational purposes only. It does not constitute financial advice. All investments in securities markets are subject to market risk. Please consult a SEBI-registered investment adviser before making investment decisions. GTT orders do not guarantee execution at exact prices.

---

## Built by

**Muthukumar Thevar (Mak)** — Senior Technical Lead & Solutions Architect  
[Portfolio](https://mak-thevar.dev) · [LinkedIn](https://linkedin.com/in/mak-thevar)
