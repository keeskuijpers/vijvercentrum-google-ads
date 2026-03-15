# Conversie-Tracking Architectuur — Vijvercentrum

**Version:** 2.0 | **Last Updated:** 15 March 2026 | **Status:** ✅ Live & Validated

---

## High-Level Data Flow

```
Shopify Checkout
        ↓
    gtag()
    ↙        ↘
GA4 (Firestore)  Google Ads (via API)
    ↓            ↓
Conversion event  Conversion label
    ↓            ↓
  Analytics      Bidding engine
```

---

## Shopify Pixel Configuration

### Pixel 1: Google & YouTube App

**App ID:** 4434821459
**Status:** OPEN (active)
**Installed:** February 2026
**Events tracked:** purchase, begin_checkout, add_to_cart, view_item, page_view, search

**Events sent automatically by Shopify:**

| Event | Trigger | Sent to |
|---|---|---|
| `page_view` | Page load | GA4, Google Ads, YouTube |
| `view_item` | Product page visited | GA4, Google Ads |
| `view_item_list` | Category/collection page | GA4, Google Ads |
| `select_item` | Product clicked from list | GA4, Google Ads |
| `add_to_cart` | "Add to cart" button | GA4, Google Ads |
| `view_cart` | Cart page viewed | GA4, Google Ads |
| `begin_checkout` | "Proceed to checkout" clicked | GA4, Google Ads |
| `add_payment_info` | Payment method entered | GA4, Google Ads |
| `purchase` | Order completed | GA4, Google Ads |
| `search` | On-site search performed | GA4 |

**Implementation:** Automatic via Shopify (no manual code required)

### Pixel 2: Custom GTM Container

**Container ID:** 300613971
**Status:** LAX (implemented)
**Type:** Enhanced tracking (UX events)

**Additional events tracked:**

| Event | Trigger | Sent to |
|---|---|---|
| `video_play` | Product demo video started | GA4 |
| `video_complete` | Product demo video finished | GA4 |
| `form_submit` | Contact/inquiry form submitted | GA4 |
| `live_chat_start` | Live chat initiated | GA4 |
| `live_chat_message` | Chat message sent | GA4 |
| `scroll` | Page scrolled 50%+ | GA4 |
| `click` | Element clicked (tracked elements) | GA4 |

**Implementation:** Custom GTM setup (installed in Shopify theme)

---

## Conversion Labels in Google Ads

All conversion labels use primary conversion ID: **AW-17999886877**

### Active Conversion Labels

#### Label 1: Purchase (Primary Conversion)

```
Label: AW-17999886877/purchase-1
Event: purchase
Value: Dynamic (order total)
Category: Sales/Leads
Count: Every occurrence
Attribution model: Data-driven (when available)
Status: ✅ Active
Last fire: 2 hours ago
```

**GA4 Event:** purchase
**Ecommerce value:** order total (EUR)
**Example:** €156.50 purchase

#### Label 2: Begin Checkout (Secondary)

```
Label: AW-17999886877/begin_checkout-1
Event: begin_checkout
Value: Dynamic (estimated AOV €45)
Category: Sales/Leads
Count: Every occurrence
Attribution model: Data-driven
Status: ✅ Active
Last fire: 4 hours ago
```

**GA4 Event:** begin_checkout
**Ecommerce value:** estimated (average AOV for estimating value)

#### Label 3: Add to Cart (Secondary)

```
Label: AW-17999886877/add_to_cart-1
Event: add_to_cart
Value: Dynamic (product price)
Category: Sales/Leads
Count: Every occurrence
Attribution model: Data-driven
Status: ✅ Active
Last fire: 3 hours ago
```

**GA4 Event:** add_to_cart
**Ecommerce value:** item price (EUR)

#### Label 4: Add Payment Info (Secondary)

```
Label: AW-17999886877/add_payment_info-1
Event: add_payment_info
Value: Dynamic (estimated AOV €45)
Category: Sales/Leads
Count: Every occurrence
Attribution model: Data-driven
Status: ✅ Active
Last fire: 5 hours ago
```

**GA4 Event:** add_payment_info
**Ecommerce value:** estimated (AOV for value)

#### Label 5: View Item (Observation)

```
Label: AW-17999886877/view_item-1
Event: view_item
Value: Dynamic (product price)
Category: Engagement
Count: Every occurrence
Attribution model: N/A (observation only)
Status: ✅ Active
In bid strategy: No
```

**GA4 Event:** view_item
**Ecommerce value:** item price (EUR)
**Note:** Not used for bid optimization; observation only

---

## Tracking Template

Applied at **campaign level** (all 4 campaigns use same template):

```
{lpurl}?utm_source=google&utm_medium=cpc&utm_campaign={_campaign}&utm_content={creative}&utm_term={keyword}
```

### UTM Parameters Breakdown

| Parameter | Value | Source | Purpose |
|---|---|---|---|
| utm_source | google | Static | Identifies Google Ads traffic |
| utm_medium | cpc | Static | Identifies paid search |
| utm_campaign | {_campaign} | Dynamic | Campaign name (auto-populated) |
| utm_content | {creative} | Dynamic | Which ad creative (RSA variant) |
| utm_term | {keyword} | Dynamic | Triggered keyword |

### How It Works

1. User clicks ad with keyword "koivoer"
2. URL becomes: `https://vijvercentrum.nl/?utm_source=google&utm_medium=cpc&utm_campaign=[Vijvercentrum] 01 - A2KOI Migratie&utm_content=RSA Variant 1&utm_term=koivoer`
3. Shopify's gtag() fires `page_view` event with utm parameters
4. GA4 captures utm_source=google → "google" channel
5. GA4 captures utm_campaign → campaign detail
6. GA4 correlates to purchase → "google/cpc" channel conversion

### Google Auto-Tagging

**Status:** ✅ Enabled

**What it adds:** `gclid` parameter (Google Click ID)

```
{lpurl}?gclid=xyz123&utm_source=google&utm_medium=cpc...
```

**Why:** Enables click-level attribution (which ad led to conversion)

**Important:** Do NOT disable auto-tagging

---

## GA4 ↔ Google Ads Link

**Status:** ✅ Active (since 7 March 2026)

**Setup:** Google Ads account 471-168-2842 is linked to GA4 Property 478336344

**What this enables:**
1. GA4 conversion data flows to Google Ads bidding
2. Enhanced conversion tracking (cross-device)
3. ROAS calculations in Ads UI
4. Customer lifetime value (CLV) modeling
5. Lookalike audiences (future)

**Data sync:**
- Direction: GA4 → Google Ads API
- Frequency: Every 2 hours
- Latency: 2–4 hours typical

**Conversion import settings:**
- Primary conversion: `purchase` event
- Include in conversions: Yes
- Include in ROAS: Yes
- Attribution: Data-driven

---

## Dataflow Diagram (Text)

```
┌─────────────────────────────────────────────────────────────────┐
│ Shopify Checkout (Desktop / Mobile)                             │
└─────────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────────┐
│ Page Load Event                                                 │
│ - Order created                                                 │
│ - Payment processed                                             │
│ - Confirmation page visible                                    │
└─────────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────────┐
│ gtag() Fires: purchase Event                                    │
│ - order_id: xyz123                                              │
│ - transaction_id: xyz123                                        │
│ - value: 156.50 EUR                                             │
│ - currency: EUR                                                 │
│ - tax: 26.43 EUR                                                │
│ - shipping: 5.95 EUR                                            │
│ - items: [{ id, name, price, category, qty }, ...]            │
│ - gclid: (from URL auto-tag)                                    │
│ - utm_source: google                                            │
│ - utm_medium: cpc                                               │
│ - utm_campaign: [Vijvercentrum] 01 - A2KOI Migratie            │
│ - utm_term: koivoer                                             │
└─────────────────────────────────────────────────────────────────┘
          ↙                                          ↘
┌──────────────────────────┐              ┌────────────────────────┐
│ GA4 Firestore (Real-time)│              │ Google Ads API (2h lag)│
│ - Event: purchase        │              │ - Label fires: ✅      │
│ - Event value: 156.50    │              │ - Value: 156.50 EUR    │
│ - User ID: gxxxxx        │              │ - Conversion count: +1 │
│ - Session ID: sxxxxx     │              │ - Attribution: gclid   │
│ - Channel: google/cpc    │              │ - Counts toward ROAS   │
│ - Device: mobile/desktop │              │ - Counts toward CPA    │
│ - Campaign: campaign_id  │              └────────────────────────┘
│ - Source: google         │
│ - Medium: cpc            │
└──────────────────────────┘
        ↓ (Real-time)
┌──────────────────────────────────────────────────────┐
│ Google Analytics 4 Dashboard                         │
│ - Conversions report: +1 (google/cpc)               │
│ - Revenue: +€156.50 (google/cpc channel)            │
│ - ROAS: (updated in real-time)                      │
│ - CPA: (recalculated)                               │
│ - Funnel: purchase completion recorded              │
└──────────────────────────────────────────────────────┘
        ↓ (2h sync)
┌──────────────────────────────────────────────────────┐
│ Google Ads Campaign Dashboard                        │
│ - Conversions: +1                                    │
│ - Conversion value: €156.50                          │
│ - ROAS: (updated from GA4 data)                      │
│ - Bid adjustment: (based on ROAS target)            │
│ - Budget allocation: (optimized by ML)              │
└──────────────────────────────────────────────────────┘
```

---

## Conversion Goals Status

All 4 conversion goals were fixed on **15 March 2026** in Google Ads.

### Fixed Issues (Pre-15 March)

**Problem:** Conversion labels were not receiving event data

**Causes:**
1. GA4 pixel was not correctly configured in Shopify checkout
2. Conversion label IDs were not linked to GA4 events
3. GTM container had tracking errors

**Resolution:**
1. Verified Shopify Google & YouTube App is OPEN
2. Verified Shopify GTM container is LAX
3. Tested full purchase flow end-to-end
4. Confirmed gtag() fires on order confirmation page
5. Verified conversion labels receive data in real-time
6. Validated sync between GA4 and Google Ads (2h lag)

### Current Status (Post-15 March)

| Conversion | Status | Last Fire | Daily Volume | Trending |
|---|---|---|---|---|
| purchase-1 | ✅ Fixed | 2h ago | ~2–3 | Stable |
| begin_checkout-1 | ✅ Fixed | 4h ago | ~5–8 | Stable |
| add_to_cart-1 | ✅ Fixed | 3h ago | ~8–12 | Stable |
| add_payment_info-1 | ✅ Fixed | 5h ago | ~4–6 | Stable |

---

## Advanced Tracking Setup

### Enhanced Conversions (TODO)

**Status:** ❌ Not yet implemented

**What:** Cross-device conversion tracking using hashed customer data

**Benefits:**
- Track conversions across devices (search on mobile, convert on desktop)
- Improve conversion attribution accuracy
- Enable offline conversion matching

**Setup steps:**
1. Enable Enhanced conversions in Google Ads
2. Configure Shopify to send hashed email/phone
3. Map GA4 user_id to Shopify customer
4. Validate data matches rate (target >95%)

**Timeline:** Post Phase 2 (April)

### Consent Mode v2 (TODO)

**Status:** ❌ Not yet implemented

**What:** Respect user cookie consent while maintaining tracking

**Benefits:**
- GDPR compliant
- Still collect analytics even without consent
- Allow Google to infer conversions for non-consenting users

**Setup steps:**
1. Install Cookie Consent Banner (Shopify app or custom)
2. Configure GTM Consent Mode v2
3. Map cookie choices to gtag() consent parameters
4. Validate: GA4 still receives data with mode=consent

**Timeline:** Post Phase 2 (April) — COMPLIANCE REQUIREMENT

---

## Troubleshooting Guide

### Issue 1: No Conversions in Google Ads

**Symptoms:** GA4 shows purchase events, but Google Ads shows 0 conversions

**Diagnosis:**
1. Check conversion label status in Google Ads UI (Settings → Conversions)
2. Verify label is "Active" and not "Paused"
3. Check conversion label linked to GA4 property (ID 478336344)
4. Check gclid parameter is in URL (auto-tagging enabled?)

**Resolution:**
1. Pause and re-enable conversion label
2. Re-verify GA4 ↔ Ads link
3. Test purchase flow: capture URL with gclid
4. Wait 2 hours for API sync
5. Verify conversion appears in Google Ads

### Issue 2: GA4 Shows Events, Google Ads Shows Different Numbers

**Symptoms:** GA4 has 10 purchase events; Google Ads shows 8 conversions

**Causes:**
- Conversion counting settings (multiple vs per-session)
- Attribution window mismatch
- gclid missing on some sessions

**Resolution:**
1. Check conversion counting in Google Ads: "All conversions" or "unique/click"
2. Compare attribution windows: GA4 = 30 days, Ads = 30 days (should match)
3. Verify all URLs have gclid parameter
4. Small discrepancies (±10%) are normal

### Issue 3: Conversion Value Mismatches

**Symptoms:** GA4 shows €500 revenue; Google Ads shows €400

**Causes:**
- Tax/shipping included in GA4 but not Ads (or vice versa)
- Refunded orders counted differently
- Currency conversion issues

**Resolution:**
1. Check GA4 value = (subtotal + tax + shipping - discount)
2. Check Google Ads value = order subtotal only
3. Adjust GA4 event value to match Ads expectations
4. Ensure currency is EUR in both systems

### Issue 4: Tracking Lost After Website Update

**Symptoms:** Conversions drop to 0 after site refresh

**Causes:**
- gtag() code removed or broken
- Shopify pixel uninstalled
- GTM container updated with errors
- Checkout page template changed

**Resolution:**
1. Verify Shopify Google & YouTube App is still OPEN
2. Verify GTM container ID in Shopify theme
3. Test gtag() by opening browser console (should show gtag fires)
4. Check for JavaScript errors (F12 → Console)
5. Contact Shopify support if pixel is broken

---

## Testing & Validation

### Test Purchase Checklist

**Before launching campaigns, perform full test:**

- [ ] Add item to cart
- [ ] Go to checkout
- [ ] Complete purchase (test payment)
- [ ] Open browser console (F12 → Console)
- [ ] Verify: gtag() fires with purchase event
- [ ] Confirm: URL has gclid parameter
- [ ] Check GA4 (within 5 min): purchase event appears
- [ ] Check Google Ads (within 2h): conversion label fires
- [ ] Verify: Conversion value matches order total
- [ ] Confirm: Campaign/keyword attribution is correct

### Daily Sync Validation

**Run daily at 09:00 CET:**

1. Get GA4 purchases (last 24h)
2. Get Google Ads conversions (last 24h)
3. Calculate sync rate: Ads ÷ GA4
4. Alert if sync < 90%
5. If anomaly: Investigate same day (don't let it slide)

---

## Conversion Labels Reference

**Quick lookup:**

| Business Goal | GA4 Event | Ads Label | Bid Strategy Included |
|---|---|---|---|
| Revenue | purchase | AW-17999886877/purchase-1 | ✅ Yes |
| Checkout initiation | begin_checkout | AW-17999886877/begin_checkout-1 | ❌ No |
| Cart addition | add_to_cart | AW-17999886877/add_to_cart-1 | ❌ No |
| Payment setup | add_payment_info | AW-17999886877/add_payment_info-1 | ❌ No |
| Product interest | view_item | AW-17999886877/view_item-1 | ❌ No |

---

## Support & Escalation

**If tracking is broken:**

1. Post error to internal Slack
2. Tag: @Kees (account owner)
3. Include: URL, browser console error, timestamp
4. Escalate to Shopify support if pixel issue

**Contacts:**
- **Kees:** kees@vijvercentrum.nl (account owner)
- **Shopify Support:** support@shopify.com (for pixel issues)
- **Google Ads Support:** Via Google Ads UI (Help → Contact Support)

---

**Last validated:** 15 March 2026 | **Next check:** 22 March 2026
