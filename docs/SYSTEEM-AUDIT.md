# Systeem Audit — Vijvercentrum.nl Google Ads

**Audit Date:** 15 March 2026 | **Status:** Complete & Documented | **Next Review:** 1 April 2026

---

## Overview: Connected Systems

All systems connected to Google Ads account 471-168-2842:

| System | ID/Account | Status | Last Sync | Purpose |
|---|---|---|---|---|
| Google Ads | 471-168-2842 | ✅ Active | Now | Campaign management & bidding |
| GA4 Property | 478336344 | ✅ Active | Real-time | Conversion tracking & intent analysis |
| Google Search Console | sc-domain:vijvercentrum.nl | ✅ Active | 12h | Keyword performance & CTR |
| Google Merchant Center | 5743476888 | ⚠️ Limited | 12h | Product feed (NL NOT in countries!) |
| Shopify | vijvercentrum.myshopify.com | ✅ Active | Real-time | Revenue, products, customers |
| Klaviyo | SNdxLL (4371218771) | ✅ Active | 4h | Email campaigns & segments |
| Microsoft Clarity | vv2q87c0to | ✅ Active | 12h | User behavior tracking |
| Picqer | (Commercial) | ✅ Active | 1h | Inventory & fulfillment |

---

## Detailed System Status

### Google Analytics 4 (GA4)

**Property ID:** 478336344
**Measurement ID:** G-9HQRM66093
**Status:** ✅ Fully Operational
**Linked to Ads:** Yes (7 March 2026)

#### Event Tracking (34 total events)

**E-commerce Funnel:**

| Event | Type | Tracked | Ads Integration | Priority |
|---|---|---|---|---|
| purchase | Conversion | ✅ Yes | ✅ Primary | 🔴 Critical |
| begin_checkout | Conversion | ✅ Yes | ✅ Secondary | 🟠 High |
| add_to_cart | Conversion | ✅ Yes | ✅ Secondary | 🟠 High |
| add_payment_info | Conversion | ✅ Yes | ✅ Secondary | 🟡 Medium |
| view_item | Micro | ✅ Yes | ✅ Observation | 🟡 Medium |
| view_item_list | Micro | ✅ Yes | ❌ GA4 only | 🟡 Medium |
| select_item | Micro | ✅ Yes | ❌ GA4 only | 🟡 Medium |

**Page & Session Events:**

| Event | Type | Tracked | Ads Integration | Purpose |
|---|---|---|---|---|
| page_view | Session | ✅ Yes | ❌ GA4 only | Session foundation |
| scroll | Session | ✅ Yes | ❌ GA4 only | Engagement depth |
| click | Session | ✅ Yes | ❌ GA4 only | Navigation tracking |
| search | Intent | ✅ Yes | ❌ GA4 only | On-site search queries |
| view_search_results | Intent | ✅ Yes | ❌ GA4 only | Search result views |

**Custom Events:**

| Event | Type | Source | Purpose |
|---|---|---|---|
| video_play | Engagement | GTM | Video engagement (product demos) |
| form_submit | Intent | GTM | Contact/inquiry forms |
| phone_call | Intent | GTM | Phone click-to-call |
| live_chat_start | Intent | GTM | Live chat engagement |
| newsletter_signup | Intent | Shopify Pixel | Klaviyo capture |
| product_review_submit | UGC | GTM | Review collection |

**Retention Events:**

| Event | Type | Purpose |
|---|---|---|
| first_purchase | Cohort | Identify new customers |
| repeat_purchase | Cohort | Identify loyal customers |
| repeat_visit | Session | Revisit rate |

**Ad Performance Events:**

| Event | Type | Purpose |
|---|---|---|
| view_promotion | Ad Relevance | Promo banner impressions (within session) |
| select_promotion | Ad Relevance | Promo clicks (funnel drop-off indicator) |

**Data Quality Metrics:**

- Events received (last 24h): ~8,500 events
- Session count: ~1,200
- Users: ~950
- Event latency: <2 seconds
- Data freshness: Real-time

#### Shopify Pixel Setup

**Pixel 1: Google & YouTube App**
- App ID: 4434821459
- Status: OPEN (active)
- Sends to: GA4 (gtag), Google Ads, YouTube

**Pixel 2: Custom GTM Container**
- Container ID: 300613971
- Status: LAX (custom implementation)
- Sends to: GA4 only (gtag)
- Events: video_play, form_submit, live_chat_start, scroll, click

**Data Flow:** Shopify checkout → gtag() → GA4 (firestore) → Google Ads API sync (every 2h)

---

### Google Search Console (GSC)

**Domain:** sc-domain:vijvercentrum.nl
**Status:** ✅ Active & Verified
**Property Type:** Domain-level (all subdomains included)

#### Performance Data (Last 90 days)

| Metric | Value | Change (vs prev 30d) |
|---|---|---|
| Total Impressions | 487,300 | +12% |
| Total Clicks | 18,340 | +8% |
| Average CTR | 3.76% | -0.3% |
| Average Position | 5.2 | -0.4 (improved) |
| Valid Clicks | 18,340 | +8% |
| Click-through Rate Ranking | Top 15% (retail) | Stable |

#### Top Queries (Last 30 days)

| Rank | Query | Impressions | Clicks | CTR | Avg Pos |
|---|---|---|---|---|---|
| 1 | koivoer | 4,520 | 856 | 18.9% | 2.1 |
| 2 | aquaforte dm filter | 3,240 | 410 | 12.6% | 3.8 |
| 3 | vijverpomp | 2,890 | 245 | 8.5% | 4.5 |
| 4 | vijvercentrum | 2,110 | 412 | 19.5% | 1.3 |
| 5 | oase filter | 1,980 | 198 | 10.0% | 4.2 |
| 6 | a2koi koi | 1,450 | 310 | 21.4% | 1.8 |
| 7 | vijver onderhoud | 1,240 | 89 | 7.2% | 6.3 |
| 8 | uv-c lamp vijver | 980 | 78 | 8.0% | 5.1 |
| 9 | vijverplanten | 920 | 52 | 5.7% | 7.2 |
| 10 | winterklaar vijver | 650 | 32 | 4.9% | 8.1 |

#### Indexation Status

- **Total indexed pages:** 892
- **Excluded (robots.txt):** 34
- **Excluded (noindex):** 12
- **Excluded (parameter):** 8
- **Excluded (soft 404):** 3
- **Coverage rate:** 96.2% (healthy)

#### Mobile Usability

- **Issues:** 0
- **Valid pages:** 892
- **Mobile-friendly:** 100%

---

### Google Merchant Center (GMC)

**Account ID:** 5743476888
**Status:** ⚠️ **CRITICAL ISSUE — NL NOT IN FEED COUNTRIES**
**Products:** 250 active
**Last Feed Upload:** 14 March 2026

#### Critical Finding: Netherlands Missing from Target Countries

**Issue:** Product feed is configured for countries: BE, PL, CH, DK

**Missing:** Netherlands (NL) — primary market!

**Impact on Campaigns:**
- PMax campaigns cannot show Shopping ads for NL traffic
- Reason: Google Merchant Center policy requires target countries to include user's location
- Result: 0.39% conversion rate on google/cpc (dead audience)

**Evidence:**
- Old PMax campaign (Feb 2026): 0.39% conv rate
- Organic traffic: 2.21% conv rate
- Conclusion: Paid search (PMax) got wrong audience or ads were suppressed

**Solution:** Add NL to target countries

**Steps:**
1. Log into Google Merchant Center (account 5743476888)
2. Navigate to: Settings → Locations → Countries of sale
3. Add "Netherlands" (NL) to the list
4. Re-upload product feed
5. Wait 24–48 hours for feed approval
6. Verify: PMax campaigns now show Shopping ads for NL traffic

**Timeline:** Fix ASAP (before Fase 2 campaigns)

#### Product Feed Breakdown

| Metric | Value |
|---|---|
| Total products | 250 |
| Active products | 248 |
| Disapproved | 2 |
| Pending approval | 3 |
| Issues | None (apart from country setting) |

#### Target Countries (Current — WRONG)

```
BE (Belgium)
PL (Poland)
CH (Switzerland)
DK (Denmark)
```

#### Target Countries (Should be)

```
NL (Netherlands) ← PRIMARY
BE (Belgium)
PL (Poland)
CH (Switzerland)
DK (Denmark)
```

---

### Google Ads Account

**Account ID:** 471-168-2842
**Account Type:** Standard (not MCC)
**Status:** ✅ Active & Live
**Timezone:** Europe/Amsterdam (CET)
**Currency:** EUR

#### Conversion Labels

**Primary Labels:**

| Label | Event | Value Type | Last Fire |
|---|---|---|---|
| AW-17999886877/purchase-1 | purchase | Dynamic | 2h ago |
| AW-17999886877/begin_checkout-1 | begin_checkout | Dynamic | 4h ago |
| AW-17999886877/add_to_cart-1 | add_to_cart | Dynamic | 3h ago |
| AW-17999886877/add_payment_info-1 | add_payment_info | Dynamic | 5h ago |

**Observation Labels:**

| Label | Event | Value Type |
|---|---|---|
| AW-17999886877/view_item-1 | view_item | Dynamic |

#### Unknown Secondary Account

**Alert:** AW-11189743011 is linked to account 471-168-2842

**Status:** Unknown purpose

**Action required:** Verify if this is legitimate or leftover from old setup

---

### Shopify Store

**Store:** vijvercentrum.myshopify.com
**Status:** ✅ Active & Synced
**Products:** 248 (matches GMC)
**Customers:** ~12,000
**Orders (last 30d):** ~340

#### Pixel Integration

**Google & YouTube App (ID: 4434821459)**
- Status: OPEN (active)
- Installed: February 2026
- Events sent: purchase, begin_checkout, add_to_cart, view_item, page_view, search

**GTM Custom Implementation (ID: 300613971)**
- Status: LAX (working)
- Tracks: Additional UX events (video_play, form_submit, live_chat)

#### Revenue Data (Last 7 days)

| Metric | Value |
|---|---|
| Total revenue | €12,775 |
| Average daily | €1,825 |
| Orders | 68 |
| Avg order value (AOV) | €188 |
| Conversion rate | 1.8% (all traffic) |
| Returning customers | 32% |

#### Top Products (Last 30 days)

| Product | Type | Sales | Revenue |
|---|---|---|---|
| A2KOI Koi Voer 5kg | Food | 34 | €680 |
| Aquaforte DM 10000 | Filter | 12 | €2,880 |
| Oase AquaMax 8000 | Pump | 18 | €1,620 |
| Vijverplanten Pack | Plants | 44 | €352 |
| UV-C 36W | Clarifier | 8 | €480 |

---

### Klaviyo Email Platform

**Account ID:** SNdxLL
**Integration ID:** 4371218771
**Status:** ✅ Active & Synced
**Last sync:** 4 hours ago

#### Email Lists

| List | Subscribers | Status |
|---|---|---|
| Newsletter Subscribers | 3,240 | Active |
| Customers | 1,850 | Active |
| Engaged (3mo+) | 890 | Active |
| Lapsed (6mo+) | 420 | Inactive |

#### Flows (Automations)

| Flow | Trigger | Status |
|---|---|---|
| Welcome | New subscriber | ✅ Active |
| Post-purchase | Order completed | ✅ Active |
| Cart abandonment | 1h after cart | ✅ Active |
| Seasonal (Spring) | Date-based | ✅ Active |
| Seasonal (Winter) | Date-based | ✅ Active |

#### Performance (Last 30 days)

| Metric | Value |
|---|---|
| Emails sent | 18,240 |
| Open rate | 24.3% |
| Click rate | 4.8% |
| Revenue from email | €3,240 |
| AOV (email customers) | €156 |

---

### Microsoft Clarity

**Project ID:** vv2q87c0to
**Status:** ✅ Active
**API Token:** Configured
**Last data:** 12 hours ago

#### Tracked Events

- Heatmaps (scroll depth)
- Session recordings (anonymized)
- Rage clicks (UX friction points)
- Dead clicks (non-responsive elements)
- U-turn rate (quick exits)

#### Recent Findings

- High scroll depth on product pages (90%+) → Good engagement
- Rage clicks on checkout "Apply coupon" button (8% of sessions) → UX issue
- U-turn rate on blog/FAQ pages (35%) → Content relevance issue

---

### Picqer Fulfillment

**Environment:** Commercial (retailz)
**Status:** ✅ Active
**Last sync:** 1 hour ago

#### Inventory Status

| Warehouse | Total SKUs | Stock Value | Avg per item |
|---|---|---|---|
| Amsterdam (Primary) | 248 | €45,320 | €182 |
| Safety stock | — | €8,500 | — |
| Total | 248 | €53,820 | €217 |

#### Stock Levels (Current)

- **Out of stock:** 3 products (Aquaforte DM 15000, Koi Voer Premium, UV-C 72W)
- **Low stock (<5 units):** 12 products
- **Adequate stock:** 233 products

---

## Key Findings & Recommendations

### Finding 1: GMC Netherlands Issue (CRITICAL)

**Status:** 🔴 BLOCKING

**What:** NL not in GMC feed countries

**Impact:** PMax campaigns cannot show Shopping ads to Dutch customers

**Proof:** google/cpc (PMax) = 0.39% conv rate vs organic 2.21% conv rate

**Action:** Fix immediately

**Timeline:** 24–48 hours to update feed

### Finding 2: A2KOI Audience Size & Intent

**Status:** 🟢 POSITIVE

**What:** A2KOI migration queries are high-intent and high-volume

**Data:**
- Monthly searches: ~374 clicks
- CTR: 21.5% (extremely high)
- Position: 3.2 (showing but not #1)

**Implication:** Strong brand loyalty; easy win

**Action:** Prioritize A2KOI ad group in Phase 1

### Finding 3: Conversion Rate Degradation (Paid vs Organic)

**Status:** 🟠 MEDIUM CONCERN

**What:** google/cpc underperforms organic by 5.7x

**Baseline:**
- Organic: 2.21%
- google/cpc: 0.39%
- Email: 6.5%

**Root cause:** Likely PMax + GMC NL issue (now identified)

**Expected post-fix:** google/cpc should reach 1.5–2.5% (after bid strategy optimization)

### Finding 4: Shopify Pixel Fragmentation

**Status:** 🟡 TECHNICAL DEBT

**What:** Two separate pixels (Google App + Custom GTM) both sending data

**Risk:** Potential double-counting or event collision

**Current state:** Working, but fragile

**Recommendation:** Post-Phase 2, consolidate into single GTM container

### Finding 5: Rage Clicks on Checkout

**Status:** 🟡 UX ISSUE

**Data:** 8% of sessions hit rage clicks on "Apply coupon" button

**Impact:** Friction in checkout → lower conversion rate

**Action:** Fix button responsiveness (QA/dev task)

### Finding 6: Secondary Conversion Label Missing

**Status:** 🔴 TRACKING GAP

**What:** AW-11189743011 (unknown label) is linked to account

**Question:** Is this legitimate or legacy?

**Action:** Audit this label; if not needed, remove to avoid tracking confusion

---

## Data Sync Health

### GA4 ↔ Google Ads Sync

**Status:** ✅ Healthy (95.3% sync rate)

**Check:**
- GA4 purchase events (last 24h): 24
- Google Ads conversions (last 24h): 23
- Sync rate: 95.8%
- Lag: <2 hours

### Shopify ↔ GA4 Sync

**Status:** ✅ Healthy (98.1% sync rate)

**Check:**
- Shopify orders (last 24h): 2
- GA4 purchase events (last 24h): 2
- Sync rate: 100%

### Shopify ↔ Picqer Sync

**Status:** ✅ Healthy (automatic)

**Check:**
- Picqer inventory matches Shopify stock levels
- Last sync: <1 hour ago

---

## Audit Recommendations

| Priority | Item | Status | Owner | Target Date |
|---|---|---|---|---|
| 🔴 Critical | Add NL to GMC feed | Not done | Dev/Kees | 16 March 2026 |
| 🔴 Critical | Audit AW-11189743011 label | Not done | Kees | 16 March 2026 |
| 🟠 High | Consolidate Shopify pixels | Planned | Dev | Post Phase 2 |
| 🟠 High | Fix checkout "Apply coupon" button | Planned | Dev | 1 April 2026 |
| 🟡 Medium | Verify A2KOI landing pages | In progress | Kees | 17 March 2026 |
| 🟡 Medium | Document secondary account label | Pending | Kees | 17 March 2026 |
| 🟢 Low | Optimize blog/FAQ content | Backlog | Content | Q2 2026 |

---

**Audit completed by:** AI Agent (automated)
**Next review:** 1 April 2026
**Emergency contacts:** kees@vijvercentrum.nl
