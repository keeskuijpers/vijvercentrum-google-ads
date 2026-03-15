# Agent Instructies — Vijvercentrum Google Ads

**Versie:** 2.0 | **Datum:** 15 March 2026 | **Status:** Live

Dit document bevat complete instructies voor AI agents die werken op het Vijvercentrum Google Ads account via MCP tools.

---

## Account Details

| Property | Value |
|---|---|
| **Account ID** | 471-168-2842 |
| **MCC ID** | 994-144-9739 |
| **Company** | Vijvercentrum.nl |
| **Industry** | Pond/Koi Products E-commerce |
| **Timezone** | Europe/Amsterdam (UTC+1, CET) |
| **Currency** | EUR (€) |
| **Primary Email** | kees@vijvercentrum.nl (account owner) |
| **Budget per day** | €91 (5% of 7-day rolling avg revenue) |
| **Time Zone for Reporting** | 23:59 CET (reports close at midnight Amsterdam time) |

---

## Available MCP Tools

### Google Ads Integration

**Status:** ❌ **Google Ads API is BLOCKED** (financial account limitation)

**Workaround:** Use Chrome automation tool to interact with Google Ads UI

```python
# Chrome automation available:
- mcp__Claude_in_Chrome__computer       # Click, type, navigate
- mcp__Claude_in_Chrome__read_page      # Read DOM elements
- mcp__Claude_in_Chrome__find           # Find elements by text
- mcp__Claude_in_Chrome__javascript_tool # Execute JS
```

**When to use Chrome:** Campaign activation, bid strategy changes, budget updates, creative edits, keyword pausing/adding

### Google Analytics 4 (GA4)

✅ **Full API access**

```
- mcp__retailz__ga4_report              # Custom reports (metrics, dimensions, filters)
- mcp__retailz__ga4_realtime            # Real-time data (active users)
- mcp__retailz__ga4_top_pages           # Top pages by views/sessions
- mcp__retailz__ga4_ecommerce           # Revenue, transactions, products
```

**Property ID:** G-9HQRM66093 (Property 478336344)

**Key events:** 34 total (purchase, begin_checkout, add_to_cart, add_payment_info, view_item, page_view, search, etc.)

### Google Search Console (GSC)

✅ **Full API access**

```
- mcp__retailz__gsc_performance         # Search performance (clicks, impressions, CTR, position)
- mcp__retailz__gsc_index_status        # URL indexation status
- mcp__retailz__gsc_sitemaps            # Sitemap status
```

**Domain:** sc-domain:vijvercentrum.nl

### Google Merchant Center (GMC)

⚠️ **Limited access** (read-only)

```
- mcp__retailz__gmc_products            # Product feed (250 items)
- mcp__retailz__gmc_status              # Product status & approvals
```

**Account ID:** 5743476888

**CRITICAL FINDING:** NL is NOT in GMC feed target countries. Feed has: BE, PL, CH, DK. This caused PMax campaign to show 0.39% conversion rate (no Shopping ads for NL).

### Google Ads API (GADS)

✅ **Read-only API access**

```
- mcp__retailz__gads_campaigns          # Campaign performance data
- mcp__retailz__gads_keywords           # Keyword performance
```

### Shopify Integration

✅ **Full API access**

```
- mcp__retailz__shopify_shop_info       # Store metadata
- mcp__retailz__shopify_products        # Search products
- mcp__retailz__shopify_product         # Product detail + variants
- mcp__retailz__shopify_product_update  # Update product metadata
- mcp__retailz__shopify_orders          # Retrieve orders (financial/status)
- mcp__retailz__shopify_order           # Order detail (items, customer, shipping)
- mcp__retailz__shopify_customers       # Search customers
- mcp__retailz__shopify_customer        # Customer detail (addresses, order history)
- mcp__retailz__shopify_inventory       # Stock levels
- mcp__retailz__shopify_collections     # Collection management
```

**Store:** vijvercentrum.myshopify.com

### Klaviyo Integration

✅ **Full API access**

```
- mcp__retailz__klaviyo_account         # Account info
- mcp__retailz__klaviyo_lists           # Email lists
- mcp__retailz__klaviyo_list_profiles   # Subscribers in list
- mcp__retailz__klaviyo_segments        # Audience segments
- mcp__retailz__klaviyo_campaigns       # Email campaign performance
- mcp__retailz__klaviyo_flows           # Automation flows
- mcp__retailz__klaviyo_profiles        # Customer profiles
- mcp__retailz__klaviyo_metrics         # Events & metrics tracked
- mcp__retailz__klaviyo_events          # Customer event history
- mcp__retailz__klaviyo_templates       # Email templates
```

**Account ID:** SNdxLL (4371218771)

### Picqer Integration

✅ **Full API access** (inventory & fulfillment)

```
- mcp__retailz__picqer_products         # Search products by SKU/name
- mcp__retailz__picqer_stock            # Stock per product/warehouse
- mcp__retailz__picqer_orders           # Order management
- mcp__retailz__picqer_customers        # Customer data
- mcp__retailz__picqer_picklists        # Picking lists
- mcp__retailz__picqer_suppliers        # Supplier list
- mcp__retailz__picqer_tags             # Picqer tags
```

**Environment:** retailz (commercial) or cenfil (fulfillment)

### Chrome Automation

✅ **Full browser control**

```
- mcp__Claude_in_Chrome__tabs_context_mcp   # Tab management
- mcp__Claude_in_Chrome__computer           # Click, type, scroll, screenshot
- mcp__Claude_in_Chrome__navigate           # Navigate to URL
- mcp__Claude_in_Chrome__read_page          # Read DOM
- mcp__Claude_in_Chrome__find               # Find elements by text
- mcp__Claude_in_Chrome__form_input         # Set form values
- mcp__Claude_in_Chrome__javascript_tool    # Execute JS on page
```

### Gmail Integration

✅ **Read & compose**

```
- mcp__377507d8-d61e-43b1-8160-5876f8a053b0__gmail_search_messages
- mcp__377507d8-d61e-43b1-8160-5876f8a053b0__gmail_read_message
- mcp__377507d8-d61e-43b1-8160-5876f8a053b0__gmail_create_draft
- mcp__377507d8-d61e-43b1-8160-5876f8a053b0__gmail_list_drafts
```

### Search & Indexing

✅ **Full-text search**

```
- mcp__retailz__search              # Search all docs & config
- mcp__retailz__semantic_search     # Semantic search (meaning-based)
- mcp__retailz__reindex             # Reindex documentation
- mcp__retailz__index_stats         # Index statistics
```

---

## Campaign Naming Convention

All campaigns follow this pattern:

```
[Vijvercentrum] XX - Campaign Name
```

| Campaign ID | Name | Budget | Bid Strategy | Status |
|---|---|---|---|---|
| 01 | A2KOI Migratie | €18/dag | Maximize Clicks (→ Conv) | Phase 1 |
| 02 | Brand Search | €14/dag | Maximize Clicks (→ Conv) | Phase 1 |
| 03 | Non-Brand Producten | €25/dag | Maximize Conversions | Phase 2 |
| 04 | Seizoen Marieke | €16/dag | Maximize Conversions | Phase 2 |

**Important:** Campaign names are LOCKED. Do not rename via UI.

---

## Budget Rules

### Daily Budget Formula

```
Daily Budget = (7-day rolling average daily revenue) × 5%
Minimum floor: €15/dag
Maximum cap: €200/dag (Q1 2026)
```

### How to Calculate

1. Get last 7 days revenue from GA4 ecommerce data
2. Calculate daily average
3. Multiply by 0.05
4. Apply floor/cap
5. Distribute across 4 campaigns per allocation percentages

### Current Allocation (as of 15 March 2026)

- **7-day avg revenue:** €1,825/dag
- **5% of revenue:** €91/dag

**Distribution:**

| Campaign | % of budget | Amount |
|---|---|---|
| A2KOI Migratie | 20% | €18 |
| Brand Search | 15% | €14 |
| Non-Brand Producten | 28% | €25 |
| Seizoen Marieke | 18% | €16 |
| Reserved (Fase 2) | 19% | €18 |

### Budget Check Task

**Frequency:** Daily at 09:00 CET

```
1. Get GA4 ecommerce data (last 7 days)
2. Calculate new daily budget per formula
3. If change > 10% from current: notify human
4. Update campaign budgets via Chrome automation if approved
```

---

## Bid Strategy Roadmap

Phases are DEPENDENT on performance thresholds. Do not skip phases.

### Phase 1: Maximize Clicks (Week 1–2)

**Campaigns:** A2KOI Migratie, Brand Search

**Objective:** Volume + data collection for conversion modeling

**Active from:** 15 March 2026

**Exit criteria:**
- Minimum 500 conversions (any type)
- ROAS ≥ 1.5x (break-even)
- Conversion rate ≥ 1.5%

**Timeline:** 7–14 days typically

### Phase 2: Maximize Conversions (Week 3–4)

**Campaigns:** All 4 (migrate A2KOI + Brand to this phase)

**Objective:** Optimize for purchase volume using conversion data

**Active from:** 29 March 2026 (target)

**Exit criteria:**
- Minimum 100 daily conversions (purchase events)
- ROAS ≥ 2.5x
- Conversion rate ≥ 2.5%
- 2 weeks of stable performance

**Timeline:** 10–14 days typically

### Phase 3: Target CPA (Week 5–8)

**Campaigns:** All 4

**Objective:** Set efficient cost per acquisition target

**Target CPA:** €18–22 per purchase (depending on ROAS trend)

**Active from:** 12 April 2026 (target)

**Exit criteria:**
- CPA consistently ≤ target (3 days running avg)
- ROAS ≥ 3.0x
- Budget utilization ≥ 85%

**Timeline:** 15–21 days typically

### Phase 4: Target ROAS (Week 9+)

**Campaigns:** All 4

**Objective:** Maximize revenue per ad spend at target multiplier

**Target ROAS:** 3.5x (€1 spend = €3.50 revenue)

**Active from:** 9 May 2026 (target)

**Entry criteria:** Target CPA phase ≥ 2 weeks stable

**Timeline:** Long-term (ongoing)

---

## Conversion Hierarchy

Google Ads tracks multiple conversion types. Priority order for optimization:

### Primary Conversion (Macro)

**Event:** `purchase`
**Label:** `AW-17999886877/purchase-1`
**Value:** Dynamic (order total)
**Priority:** ✅ PRIMARY OPTIMIZATION
**In reports:** Yes
**Countable for bidding:** Yes

### Secondary Conversions (Intermediate)

**Event:** `begin_checkout`
**Label:** `AW-17999886877/begin_checkout-1`
**Value:** Average AOV (€45)
**Priority:** Supporting metric
**In reports:** Yes
**Countable for bidding:** No

**Event:** `add_to_cart`
**Label:** `AW-17999886877/add_to_cart-1`
**Value:** Product price (avg €35)
**Priority:** Supporting metric
**In reports:** Yes
**Countable for bidding:** No

**Event:** `add_payment_info`
**Label:** `AW-17999886877/add_payment_info-1`
**Value:** Average AOV (€45)
**Priority:** Supporting metric
**In reports:** Yes
**Countable for bidding:** No

### Observation Conversions (Micro)

**Event:** `view_item`
**Label:** `AW-17999886877/view_item-1`
**Value:** Product price (dynamic)
**Priority:** Observation only
**In reports:** No
**Countable for bidding:** No

**Event:** `page_view`
**Label:** Not tracked in Ads
**Value:** N/A
**Priority:** GA4 analysis only
**In reports:** No (GA4 only)
**Countable for bidding:** No

**Event:** `search`
**Label:** Not tracked in Ads
**Value:** N/A
**Priority:** GA4 analysis only
**In reports:** No (GA4 only)
**Countable for bidding:** No

---

## Tracking Setup

### Tracking Template

**Applied at:** Campaign level (all campaigns use same template)

```
{lpurl}?utm_source=google&utm_medium=cpc&utm_campaign={_campaign}&utm_content={creative}&utm_term={keyword}
```

**Parameters:**
- `utm_source=google` → Identifies Google Ads traffic
- `utm_medium=cpc` → Cost-per-click (paid search)
- `utm_campaign={_campaign}` → Dynamic campaign name
- `utm_content={creative}` → Which ad variant
- `utm_term={keyword}` → Triggered keyword

### GA4 Linkage

**Status:** ✅ Active (since 7 March 2026)

**Connection:** Google Ads account 471-168-2842 ↔ GA4 Property 478336344

**Benefits:**
- Conversion data flows from GA4 to Google Ads automatically
- Enhanced conversion tracking (via enhanced_conversions event)
- Customer lifetime value (CLV) modeling
- Bid strategy uses GA4 conversion data

**Test:** Run a search → confirm landing page receives utm_source=google → confirm conversion in GA4 Ads channel

### Auto-tagging

**Status:** ✅ Enabled

**Effect:** Google automatically appends `gclid` parameter to all ad URLs

**Why:** Tracks which ad click led to conversion (at session level)

**Do not disable.** It's required for conversion attribution.

---

## Negative Keyword Strategy

### Structure

Negative keywords are added at **Campaign level** to apply globally within each campaign.

### Lists

#### Competitors (6 keywords)

- intratuin
- hornbach
- gamma
- praxis
- koiplanet
- acqua

**Why:** These searches indicate customer is shopping competitors, not Vijvercentrum-specific.

#### Product Categories Out of Scope (8 keywords)

- aquarium
- zwembad
- vijvertuin
- terrarium
- kwekerij
- boomkwekerij
- tuincentrum
- dierenwinkel

**Why:** Vijvercentrum focuses on outdoor ponds, not indoor aquariums or unrelated categories.

#### Job/Service Searches (4 keywords)

- vacatures
- werkingen
- reparatie dienst
- installatie dienst

**Why:** Job seekers and service contractors, not customers.

#### Promotional/Noise (5 keywords)

- gratis
- korting code
- cashback
- review
- compare

**Why:** Price comparison and freebie seekers have low conversion rates.

**Total:** 27 negative keywords

### How to Add

1. Google Ads UI → Campaign → Keywords → Negative keywords
2. Click "+" → Add keyword
3. Select "Negative" and "Broad" (default)
4. Paste keyword
5. Repeat for all 27
6. Save

Or import via CSV during initial setup.

---

## Critical Findings

### Finding 1: GMC NL Not in Feed Countries

**Discovery date:** 14 March 2026

**Issue:** Google Merchant Center feed has target countries set to: BE, PL, CH, DK. **NL is missing.**

**Impact:** PMax campaigns cannot show Shopping ads for Netherlands traffic → 0.39% conversion rate (dead audience)

**Solution:** Add NL to GMC feed target countries

**Steps:**
1. Log into Google Merchant Center (account 5743476888)
2. Go to Settings → Countries of sale
3. Add "Netherlands" (NL)
4. Re-upload product feed
5. Wait 24–48 hours for approval
6. Relaunch PMax campaigns (Fase 2+)

**Priority:** 🔴 HIGH — Fix before Belgium expansion

### Finding 2: A2KOI Migration Data

**Source:** Picqer/Google Analytics (historic data)

**Metrics:**
- Monthly clicks (A2KOI searches): ~374
- Click-through rate: 21.5% (extremely high)
- Average position: 3.2
- Estimated monthly conversions: ~22

**Implication:** A2KOI brand loyalty is very strong. Campaign 01 should capture this audience immediately (Week 1).

**Action:** Prioritize A2KOI ad group keywords in Phase 1 launches.

### Finding 3: Google/CPC vs Organic Conversion Rate

**Old data (before GA4 linkage):**
- google/cpc: 0.39% conversion rate
- (organic): 2.21% conversion rate
- (email): 6.5% conversion rate

**Root cause:** PMax campaigns (caused by GMC NL issue)

**New baseline (post-GMC fix, post-GA4 linkage):** Expect google/cpc to rise to 1.5–2.5% (depending on bid strategy and keyword quality)

---

## Persona Targeting

### Persona 1: Henk (Technical Pond Owner, 55+)

**Profile:**
- Experienced pond owner
- Knows brands inside-out
- Searches: Specific brand + product combos
- Device: Desktop/laptop primary
- Time of day: Evening (after work) + weekend

**Campaigns:** A2KOI Migratie, Brand Search, Non-Brand Producten

**Keyword examples:**
- "aquaforte dm 10000 filter"
- "oase aquamax filter hose"
- "a2koi koi voer"
- "vijverpomp 5000 liter"

**Ad messaging:**
- Emphasize technical specs & reliability
- Mention brand partnerships
- Highlight product compatibility guides

**Landing pages:**
- Product detail pages (specs)
- Brand category pages
- How-to guides

### Persona 2: Marieke (New Pond Owner, 35–50)

**Profile:**
- Newer to pond ownership
- Seeks advice & solutions
- Searches: Seasonal needs + problem-solving
- Device: Mobile + desktop balanced
- Time of day: Varied (including weekdays)

**Campaigns:** Seizoen Marieke, Brand Search

**Keyword examples:**
- "vijver groen water oplossing"
- "vijver onderhoud voorjaar"
- "koi voer seizoen"
- "vijver wintertijd voorbereiding"

**Ad messaging:**
- Provide educational content
- Offer seasonal guides & checklists
- Emphasize customer support

**Landing pages:**
- Seasonal guides (blog)
- Product collections (beginner-friendly)
- FAQ & support
- Video tutorials

---

## Daily Automation Tasks

### Task 1: Budget Sync (Daily, 09:00 CET)

**Frequency:** Every day at 09:00 Amsterdam time

**Steps:**
1. Query GA4 ecommerce data for last 7 days
2. Calculate daily revenue average
3. Apply formula: avg_revenue × 0.05 (floor €15, cap €200)
4. Compare to current campaign budgets
5. If delta > 10%: Create human approval task
6. If approved: Update via Chrome automation

**Tools:**
```
- mcp__retailz__ga4_ecommerce (get revenue data)
- mcp__Claude_in_Chrome__computer (update budgets)
```

### Task 2: Keyword Performance Review (Daily, 14:00 CET)

**Frequency:** Every day at 14:00 Amsterdam time

**Steps:**
1. Query GADS keywords performance (all campaigns)
2. Identify top 10 keywords (by conversion) and bottom 10 (by spend, low ROAS)
3. Flag keywords with ROAS < 1.5x for potential pause
4. Create daily performance snapshot in agent memory

**Tools:**
```
- mcp__retailz__gads_keywords
- mcp__retailz__memory_write (store daily snapshot)
```

### Task 3: Conversion Tracking Validation (Daily, 18:00 CET)

**Frequency:** Every day at 18:00 Amsterdam time

**Steps:**
1. Query GA4 purchase events (last 24h)
2. Query Google Ads conversions (last 24h)
3. Calculate sync rate (GA4 purchases ÷ Ads conversions)
4. Alert if sync rate < 90% (indicates tracking issue)
5. Log sync rate to agent memory

**Tools:**
```
- mcp__retailz__ga4_ecommerce (purchases)
- mcp__retailz__gads_campaigns (conversions)
- mcp__retailz__memory_write (log)
```

### Task 4: Search Query Report (Weekly, Monday 09:00 CET)

**Frequency:** Every Monday at 09:00 Amsterdam time

**Steps:**
1. Query GSC performance data (last 7 days)
2. Extract top queries by clicks
3. Identify top converting queries (CTR > avg)
4. Flag queries that should be added as keywords
5. Flag queries with low CTR (potential negative keyword)

**Tools:**
```
- mcp__retailz__gsc_performance
- mcp__retailz__memory_write
```

---

## Weekly Human Sync Points

**Every Monday, 10:00 CET — Kees (account owner)**

Agenda:
1. Budget adjustment (if needed)
2. Bid strategy phase gate evaluation
3. Keyword quality & performance
4. Competitive analysis
5. Planning for next week

---

## Phase Gate Checklist

Before advancing to next bid strategy phase, verify:

**Phase 1 → Phase 2:**
- [ ] Minimum 500 conversions recorded
- [ ] ROAS ≥ 1.5x (all campaigns combined)
- [ ] Conversion rate ≥ 1.5%
- [ ] Tracking validation ≥ 95% sync
- [ ] No major tracking anomalies

**Phase 2 → Phase 3:**
- [ ] Minimum 100 daily conversions (purchase events)
- [ ] ROAS ≥ 2.5x (all campaigns)
- [ ] Conversion rate ≥ 2.5%
- [ ] 14 consecutive days of stable metrics
- [ ] CPA stable ± 10% (3-day rolling avg)

**Phase 3 → Phase 4:**
- [ ] CPA consistently ≤ target (3 days running avg)
- [ ] ROAS ≥ 3.0x
- [ ] Budget utilization ≥ 85%
- [ ] 21 consecutive days of stable metrics

---

## Error Handling

### Scenario 1: Conversion Data Not Syncing (Sync < 90%)

**Symptoms:** GA4 shows purchases but Google Ads shows no conversions

**Diagnosis steps:**
1. Check GA4 event configuration (purchase event live?)
2. Check Google Ads conversion labels (active?)
3. Check gtag() implementation in Shopify checkout
4. Verify Google Ads ↔ GA4 link is active
5. Check browser console for JS errors

**Resolution:**
1. Contact Kees if sync remains < 90% for 2 hours
2. Pause campaigns (freeze spend) until resolved
3. Investigate Shopify pixel tracking
4. Re-verify GA4 ↔ Ads linkage in UI

### Scenario 2: Campaign Not Spending Budget

**Symptoms:** Campaign has budget but daily spend = €0

**Diagnosis:**
1. Check campaign status (Active? Paused?)
2. Check ad group status (Active? Paused?)
3. Check keywords status (Active? Paused?)
4. Check ads (Approved? Under review?)
5. Check targeting (Geo, device, audience)

**Resolution:**
1. Via Chrome automation: Verify status of campaign, ad groups, keywords, ads
2. If paused: Unpause if phase gates met
3. If under review: Wait 4–24 hours
4. If targeting too narrow: Expand targeting

### Scenario 3: Anomalously High Spend (>20% budget increase)

**Symptoms:** Daily spend suddenly +20% or more

**Causes:**
- Bid strategy increased CPC
- Impression share expanded
- Seasonal spike in search volume
- Budget was increased manually

**Action:**
1. Pause campaign temporarily (stop bleed)
2. Investigate root cause
3. Review GA4 conversion data (are conversions proportional?)
4. If ROAS remains > 2.0x: Allow higher spend
5. If ROAS drops < 1.5x: Reduce bid strategy or budget cap

---

## Promo Credit Usage

**Available:** €1,200 (spend €2,400 by 6 May 2026 to claim)

**Tracking:**
- Each €1 spent = €0.50 credit earned (up to €1,200)
- Expires: 6 May 2026

**Strategy:**
- Use during Phase 3 & 4 (when ROAS is highest)
- Do not use during Phase 1 (uncertain ROAS)
- Optimal timing: Late April (when stable at ROAS ≥ 3.0x)

---

## Linked Systems Reference

**Do not attempt to change these manually without human approval.**

- GA4 Property: 478336344
- GA4 Measurement ID: G-9HQRM66093
- Google Ads Conversion Label: AW-17999886877
- Shopify Google App: 4434821459 (status: OPEN)
- Shopify Custom GTM: 300613971 (status: LAX)

---

## Quick Reference

| Need | Tool | Command |
|---|---|---|
| Budget calc | GA4 | `ga4_ecommerce` (7d avg) |
| Keyword performance | GADS | `gads_keywords` |
| Conversion data | GA4 | `ga4_ecommerce` (last 24h) |
| Search queries | GSC | `gsc_performance` |
| Campaign status | Chrome | Open ads.google.com, login |
| Product data | Shopify | `shopify_products` |
| Customer data | Shopify | `shopify_customers` |
| Revenue data | GA4 | `ga4_ecommerce` |

---

**Questions? Contact:** kees@vijvercentrum.nl
**Last updated:** 15 March 2026
**Version:** 2.0
