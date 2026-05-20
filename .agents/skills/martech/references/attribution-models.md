# Attribution Model Comparison and Selection Guide

## Model Overview

| Model | Credit Distribution | Touchpoints Considered | Best For |
|-------|-------------------|----------------------|---------|
| Last touch | 100% to last | Last only | Short sales cycles, direct response |
| First touch | 100% to first | First only | Awareness measurement, top-of-funnel |
| Linear | Equal % to all | All | Understanding full journey |
| Time decay | More to recent | All (weighted) | Long B2B sales cycles (60+ days) |
| W-shaped | 30% first, 30% lead creation, 40% close | Key milestones | B2B demand gen teams |
| Full path (U/W) | Weighted milestones | All + milestones | Complex enterprise sales |
| Data-driven | ML-weighted | All | High volume (>1k monthly conversions) |

## When to Use Each Model

### Last Touch
✅ Use when: Quick decision purchases, direct response campaigns, e-commerce with short research cycles
❌ Avoid when: Long sales cycles, multiple awareness channels, B2B

### First Touch
✅ Use when: Measuring brand awareness impact, understanding which channels introduce customers, top-of-funnel reporting
❌ Avoid when: You need to optimize conversion campaigns, short-cycle products

### Linear
✅ Use when: You have no strong prior on which touchpoints matter most, starting attribution for the first time
❌ Avoid when: You know certain touchpoints matter more

### W-Shaped (B2B recommended)
✅ Use when: B2B with defined funnel stages (MQL, SQL), multiple marketing-to-sales handoffs
❌ Avoid when: Simple e-commerce, no clear funnel milestones

### Data-Driven
✅ Use when: High conversion volume (GA4 requires ~1,000 conversions/month), trust ML models
❌ Avoid when: Low volume, black-box results are unacceptable

## Attribution Stack by Use Case

### E-commerce
1. **UTMs + GA4** — first-party web attribution
2. **Meta / Google native attribution** — optimization signals
3. **Triple Whale or Northbeam** — cross-channel MTA
4. **Geo holdout tests** — incrementality measurement

### B2B SaaS
1. **UTMs + GA4** — web attribution
2. **HubSpot multi-touch attribution** — pipeline attribution
3. **Rockerbox or Attribution** — cross-channel MTA
4. **Platform-native attribution** — channel optimization

### Mobile App
1. **Mobile Measurement Partner (MMP)** — AppsFlyer, Adjust, Branch
2. **SKAdNetwork** — iOS 14+ privacy-safe attribution
3. **Probabilistic matching** — supplemental for iOS

## Incrementality Testing

The gold standard. Measures the **causal** lift from a channel, not correlational.

### Geo holdout test
- Split geographic regions into test/control
- Run campaign in test regions only
- Measure conversion difference after statistical confidence

### Platform-native lift tests
- Meta Conversion Lift
- Google Brand Lift / Conversion Lift
- LinkedIn Conversion Lift

**When to run:** Any channel spending > $20k/month. Most companies over-attribute to retargeting; holdout tests reveal true incremental impact.

## Common Attribution Mistakes

| Mistake | Impact | Fix |
|---------|--------|-----|
| Trusting only platform-reported ROAS | Overcounting; each platform claims credit | Use third-party MTA tool |
| Inconsistent UTMs | Broken data, source = "direct" | UTM naming convention + UTM builder tool |
| Ignoring view-through attribution | Undercounting display/video | Apply conservative view-through window (1-day) |
| Single-model analysis | Distorted decisions | Compare multiple models |
| No holdout tests | Unknown true incrementality | Run geo holdout 1–2x per year per major channel |
