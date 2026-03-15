# Budget & KPI Model — Vijvercentrum Google Ads

**Version:** 2.0 | **Last Updated:** 15 March 2026 | **Status:** Live

---

## Budget Formula

### Core Equation

```
Daily Budget = (7-day rolling average daily revenue) × 5%
Minimum floor: €15/dag
Maximum cap: €200/dag (Q1 2026)
```

### Rationale

- **5% of revenue:** Conservative spend (ROI target = 3:1 ROAS = 20% cost of revenue)
- **7-day rolling average:** Smooths daily fluctuations
- **Floor €15:** Ensures minimum media spend for bid strategy learning
- **Cap €200:** Prevents excessive spend during seasonal spikes

### Current Status (15 March 2026)

| Metric | Value |
|---|---|
| 7-day average daily revenue | €1,825 |
| 5% of revenue | €91.25 |
| Rounded daily budget | €91 |
| Minimum floor | €15 |
| Maximum cap | €200 |
| **Recommended daily budget** | **€91** |

---

## Daily Budget Calculation Steps

**Run daily at 09:00 CET**

1. Query GA4 ecommerce revenue (last 7 days)
2. Calculate daily average: (total revenue ÷ 7)
3. Apply formula: avg_daily × 0.05
4. Compare to minimum floor: if result < €15, use €15
5. Compare to maximum cap: if result > €200, use €200
6. Round to nearest €1
7. If delta from current budget > 10%: Create approval task for human
8. If approved: Update all campaign budgets proportionally

### Example Calculation

```
Last 7 days revenue: €12,775
Daily average: €12,775 ÷ 7 = €1,825
5% of average: €1,825 × 0.05 = €91.25
Check floor: €91.25 > €15 ✓
Check cap: €91.25 < €200 ✓
Final budget: €91/dag
```

---

## Campaign Budget Distribution

### Allocation Percentages

| Campaign | % of Budget | Daily (€91) | Weekly | Monthly |
|---|---|---|---|---|
| A2KOI Migratie | 20% | €18 | €126 | €540 |
| Brand Search | 15% | €14 | €98 | €420 |
| Non-Brand Producten | 28% | €25 | €175 | €750 |
| Seizoen Marieke | 18% | €16 | €112 | €480 |
| Reserved (Fase 2) | 19% | €18 | €126 | €540 |
| | | | | |
| **TOTAL** | **100%** | **€91** | **€637** | **€2,730** |

### Budget Adjustment Rules

**When to adjust distribution:**

- **Performance delta >50% vs target ROAS:** Rebalance toward winners
- **Campaign paused/disabled:** Redistribute budget to active campaigns
- **Seasonal spike:** Increase cap to €200 temporarily (notify Kees)
- **Revenue drop >20%:** Reduce floor to €10 (notify Kees)

**Rebalancing frequency:** Weekly (Monday)

---

## KPI Targets by Campaign

### Campaign 1: A2KOI Migratie

| KPI | Target | Rationale |
|---|---|---|
| **CTR** | 8–10% | High-intent A2KOI audience |
| **CPA** | €18–22 | AOV €188, target ROAS 3.5x |
| **ROAS** | 3.5x | High conversion audience |
| **Conversion Rate** | 4–5% | Existing A2KOI customers = high intent |
| **Impression Share** | >70% | Capture A2KOI migration |
| **Avg. CPC** | €2–3 | Expected for brand searches |
| **Quality Score** | 7+ | Targeted keywords, relevant ads |

**Success threshold:** ROAS ≥ 2.5x (phase 1 gate), ≥ 3.0x (stable)

### Campaign 2: Brand Search

| KPI | Target | Rationale |
|---|---|---|
| **CTR** | 12–15% | Brand searches = high click rate |
| **CPA** | €15–18 | Direct brand traffic, lowest CAC |
| **ROAS** | 4.0x | Strong conversion intent |
| **Conversion Rate** | 5–6% | Brand customers = high loyalty |
| **Impression Share** | >80% | Capture all branded searches |
| **Avg. CPC** | €1–2 | Brand keywords usually cheaper |
| **Quality Score** | 8+ | Branded ads = high relevance |

**Success threshold:** ROAS ≥ 3.0x (phase 1 gate), ≥ 3.5x (stable)

### Campaign 3: Non-Brand Producten

| KPI | Target | Rationale |
|---|---|---|
| **CTR** | 5–7% | Product searches = medium intent |
| **CPA** | €22–28 | Mixed audience (Henk primary) |
| **ROAS** | 3.0x | Broad product category |
| **Conversion Rate** | 3–4% | Product searches less specific than brand |
| **Impression Share** | >60% | Competitive market (many sellers) |
| **Avg. CPC** | €3–5 | Product keywords more expensive |
| **Quality Score** | 6–7 | Targeted keywords, competitive ads |

**Success threshold:** ROAS ≥ 2.0x (phase 2 gate), ≥ 2.5x (stable)

### Campaign 4: Seizoen Marieke

| KPI | Target | Rationale |
|---|---|---|
| **CTR** | 4–6% | Seasonal = lower search volume |
| **CPA** | €25–32 | New owners = lower intent |
| **ROAS** | 2.8x | Educational audience |
| **Conversion Rate** | 2–3% | Informational searches mixed with transactional |
| **Impression Share** | >50% | Long-tail seasonal keywords |
| **Avg. CPC** | €2–4 | Mixed long-tail keywords |
| **Quality Score** | 6–7 | Seasonal, educational focus |

**Success threshold:** ROAS ≥ 1.8x (phase 2 gate), ≥ 2.0x (stable)

---

## Bid Strategy Roadmap

### Phase 1: Maximize Clicks (Week 1–2)

**Objective:** Collect conversion data for model training

**Campaigns:** A2KOI Migratie, Brand Search

**Active from:** 15 March 2026

**Bid settings:**
- Auto bid enabled
- Target average CPC: Not applicable (Maximize Clicks)
- Ad rotation: Optimize for conversions

**Why this phase:** Google Ads ML needs minimum data to train:
- Minimize Clicks phase learns CTR patterns
- System collects conversion signals
- Prepares for Maximize Conversions phase

**Expected metrics:**
- High CTR (system optimizes for clicks)
- Moderate conversion rate (mixed traffic)
- ROAS baseline 1.5–2.0x

**Exit criteria:**
- Minimum 500 conversions (all types)
- ROAS ≥ 1.5x
- Conversion rate ≥ 1.5%
- 7 consecutive days stable

### Phase 2: Maximize Conversions (Week 3–4)

**Objective:** Optimize for purchase volume using trained ML

**Campaigns:** All 4 (A2KOI, Brand, Non-Brand, Seizoen)

**Active from:** 29 March 2026 (target)

**Bid settings:**
- Auto bid enabled
- Maximize Conversions (no CPA target yet)
- Conversion goal: `purchase` event primary
- Ad rotation: Optimize for conversions

**Why this phase:** Conversion model is trained, now optimize volume:
- System shifts bids to high-conversion search combinations
- Spend increases as confidence grows
- ROAS should improve significantly

**Expected metrics:**
- Lower CTR (selective on high-conversion keywords)
- Higher conversion rate (3–4%)
- ROAS baseline 2.5–3.0x

**Conversion tracking hierarchy:**
```
Primary:    purchase (macroconversion)
Secondary:  begin_checkout, add_to_cart (micro signals)
Observation: view_item (funnel drop-off)
```

**Exit criteria:**
- Minimum 100 daily conversions (purchase events)
- ROAS ≥ 2.5x (all campaigns)
- Conversion rate ≥ 2.5%
- 14 consecutive days stable performance

### Phase 3: Target CPA (Week 5–8)

**Objective:** Efficient CAC at target price point

**Campaigns:** All 4

**Active from:** 12 April 2026 (target)

**Bid settings:**
- Target CPA: Campaign-specific (see below)
- Conversion goal: `purchase` event
- Ad rotation: Optimize for conversions

**Target CPA by campaign:**

| Campaign | Target CPA | Rationale |
|---|---|---|
| A2KOI Migratie | €20 | High AOV (€188), loyal audience |
| Brand Search | €17 | Direct traffic, high loyalty |
| Non-Brand Producten | €25 | Broad product category |
| Seizoen Marieke | €28 | Lower intent, educational audience |

**Why this phase:** System now has 4+ weeks conversion data:
- Can set specific CAC targets per campaign
- Maintains ROAS target (if ROAS ≥ 3.0x → CPA ≤ €30)
- Shifts from volume to efficiency

**Expected metrics:**
- Stable CPA (within target ±15%)
- ROAS 2.8–3.2x
- Conversion volume stable

**Exit criteria:**
- CPA consistently ≤ target (3-day rolling avg)
- ROAS ≥ 3.0x
- Budget utilization ≥ 85%
- 21 consecutive days stable

### Phase 4: Target ROAS (Week 9+)

**Objective:** Maximize revenue at target ROAS multiplier

**Campaigns:** All 4

**Active from:** 9 May 2026 (target)

**Bid settings:**
- Target ROAS: 3.5x (all campaigns)
- Conversion goal: `purchase` event
- Ad rotation: Optimize for conversions

**Why this phase:** Long-term optimization:
- System maximizes revenue per spend at specified ratio
- Adjusts spend dynamically based on ROAS
- Most efficient long-term strategy

**Entry criteria for this phase:**
- Target CPA phase ≥ 4 weeks stable
- ROAS consistently 3.0–3.5x
- No major seasonal changes forecast

**Expected metrics:**
- ROAS 3.3–3.7x (fluctuates ±0.2x)
- CPA varies as spend changes
- Conversion volume follows budget

---

## Anomaly Detection Rules

**Run daily at 14:00 CET**

### Alert Triggers

| Anomaly | Threshold | Action |
|---|---|---|
| **Spend >20% above budget** | >120% allocated | Pause cheapest campaigns, investigate |
| **ROAS drops >30% vs 7d avg** | <70% baseline | Pause campaigns, debug tracking |
| **Conversion rate drops >50%** | <50% baseline | Pause campaigns, verify conversion tracking |
| **CTR drops >40%** | <60% baseline | Pause, review ad creatives & keywords |
| **CPA increases >50%** | >150% target | Pause, increase bid strategy aggressiveness |
| **Conversion sync <90%** | GA4÷Ads<90% | Pause, debug GA4↔Ads link |
| **No conversions for 6h** | 0 conversions | Pause, manual investigation |

### Response Protocol

1. **Immediate:** Pause affected campaigns (prevent budget bleed)
2. **Investigate:** Check tracking, bid settings, creatives, keywords
3. **Document:** Log anomaly time, cause, resolution
4. **Notify:** Post to Slack #google-ads-alerts
5. **Resolve:** Apply fix (bid adjustment, keyword pause, tracking fix)
6. **Verify:** Wait 2–4 hours, confirm metrics normalize
7. **Resume:** Unpause campaigns if resolved

---

## Promo Credit Usage Strategy

**Available:** €1,200 credit (spend €2,400 by 6 May 2026 to claim)

### Spend Rate Required

```
Days until deadline: 52 (6 May - 15 March)
Required daily spend to claim: €2,400 ÷ 52 = €46.15/dag
Current budget: €91/dag (exceeds requirement ✓)
```

### Strategy: Use During Phase 3–4

**Don't use during Phase 1–2 (uncertain ROAS)**

**Optimal timing:** Late April (when ROAS ≥ 3.0x stable)

**Spend profile:**
- Phase 1–2 (Mar 15–Apr 11): Organic spend (€91/dag)
- Phase 3–4 (Apr 12–May 6): Credit-subsidized spend
  - Target: €46/day credit usage
  - Organic: €91/day
  - Total: €137/day
  - Duration: 25 days
  - Total credit used: €1,150 (exceeds €1,200 claim)

**Impact:**
- Effective budget increase 50% during peak optimization
- Improves ROAS due to increased bid capacity
- Maximizes credit claim (€1,150 used of €1,200 available)

---

## Weekly Budget Review Template

**Run every Monday, 10:00 CET (with Kees)**

```
WEEK OF: [DATE]

Revenue (last 7 days):
- Total: €____
- Daily avg: €____
- Calculated budget: €____ (5% × avg)
- Current allocation: €____
- Delta: +/-___%

Status:
□ Keep current budget
□ Increase to €____
□ Decrease to €____
□ Other: ____

Campaign Breakdown:
- A2KOI: €____ (target €18, variance __%)
- Brand: €____ (target €14, variance __%)
- Non-Brand: €____ (target €25, variance __%)
- Seizoen: €____ (target €16, variance __%)

Performance Highlights:
- Top campaign: ____ (ROAS ___x)
- Bottom campaign: ____ (ROAS ___x)
- Anomalies: None / [describe]

Next actions:
□ Maintain status quo
□ Adjust bids
□ Pause underperformer
□ Launch new initiative
□ Phase gate evaluation

Signature: _________ Date: _________
```

---

## Seasonal Budget Adjustments

### Q2 2026 (April–June) — Spring Peak

**Expected revenue increase:** +15% due to spring pond season

**Budget adjustment:**
- Current: €91/dag
- Expected: €104/dag (5% × €2,080 expected avg)
- Action: Increase cap to €150 (temporary, April–June only)

### Q3 2026 (July–September) — Summer Plateau

**Expected revenue:** Stable (summer maintenance = recurring spend)

**Budget adjustment:**
- Expected: €89/dag
- Action: Maintain €91/dag budget

### Q4 2026 (October–December) — Winter Prep Peak

**Expected revenue increase:** +25% due to winter prep season

**Budget adjustment:**
- Expected: €114/dag (5% × €2,280 expected avg)
- Action: Increase cap to €200 (autumn + winter prep peak)

---

## KPI Dashboard Targets

### Monthly Reporting (Sample)

| KPI | A2KOI | Brand | Non-Brand | Seizoen | All |
|---|---|---|---|---|---|
| **Revenue** | €€€€ | €€€€ | €€€€€ | €€€€ | €€€€€ |
| **Spend** | €486 | €378 | €675 | €432 | €1,971 |
| **ROAS** | 3.8x | 4.2x | 2.9x | 2.7x | 3.4x |
| **Conversions** | 24 | 22 | 31 | 14 | 91 |
| **CPA** | €20 | €17 | €22 | €31 | €21.65 |
| **CTR** | 9.2% | 13.8% | 5.4% | 4.9% | 8.3% |
| **Conv. Rate** | 4.8% | 5.2% | 3.2% | 2.5% | 3.9% |
| **Clicks** | 500 | 425 | 975 | 575 | 2,475 |

---

**Last updated:** 15 March 2026 | **Next review:** 22 March 2026 | **Phase gate check:** 29 March 2026
