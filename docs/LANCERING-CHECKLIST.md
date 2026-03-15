# Lancering Checklist — Vijvercentrum Google Ads

**Version:** 2.0 | **Last Updated:** 15 March 2026 | **Status:** Pre-Launch

---

## Pre-Launch Phase ✅ (Complete)

All items required before Week 1 launch have been completed.

### Tracking & Analytics Setup

- [x] GA4 property created (ID: 478336344)
- [x] GA4 ↔ Google Ads linked (since 7 March)
- [x] Conversion labels created (4 total: purchase, begin_checkout, add_to_cart, add_payment_info)
- [x] Conversion tracking tested (full purchase flow validated)
- [x] Shopify Google & YouTube App installed (ID: 4434821459, status OPEN)
- [x] Shopify GTM container installed (ID: 300613971, status LAX)
- [x] Auto-tagging enabled in Google Ads
- [x] Tracking template configured: `{lpurl}?utm_source=google&utm_medium=cpc&utm_campaign={_campaign}&utm_content={creative}&utm_term={keyword}`
- [x] Enhanced conversions enabled (GA4 purchase tracking)

### Campaign Structure

- [x] Campaign 1 (A2KOI Migratie) configured
- [x] Campaign 2 (Brand Search) configured
- [x] Campaign 3 (Non-Brand Producten) configured
- [x] Campaign 4 (Seizoen Marieke) configured
- [x] All campaigns named per convention: [Vijvercentrum] XX - Name
- [x] Budget allocation model defined (5% of revenue)
- [x] Bid strategies assigned per phase roadmap

### Keyword & Negative Keyword Setup

- [x] 112 keywords created across 16 ad groups
- [x] 27 negative keywords added (competitors, OOS categories, job searches, noise)
- [x] Negative keywords verified at campaign level
- [x] Keyword match types verified (exact, phrase, broad modified)
- [x] Search term analysis prepared (GSC data integrated)

### Responsive Search Ads (RSA)

- [x] 15 headlines per ad group
- [x] 4 descriptions per ad group
- [x] Ads tested for quality score prediction
- [x] Messaging aligned with persona (Henk + Marieke)
- [x] CTAs optimized for conversions

### Extensions

- [x] 12 Sitelinks created
  - [ ] Koivoer (product page)
  - [ ] Filters (product page)
  - [ ] Pumps (product page)
  - [ ] Plants (product page)
  - [ ] Blog (educational content)
  - [ ] FAQ (customer support)
  - [ ] Contact (support page)
  - [ ] Shipping Info (policies)
  - [ ] Returns (policies)
  - [ ] About Us (company page)
  - [ ] A2KOI Alternatie (migration page)
  - [ ] Seasonal Guides (seasonal content)
- [x] 8 Callout extensions created
  - [ ] Free shipping over €50
  - [ ] Expert advice available
  - [ ] 24/7 customer support
  - [ ] Same-day dispatch
  - [ ] 30-day returns
  - [ ] Trusted since 1995
  - [ ] 20+ year expertise
  - [ ] Premium brands

### CSV Import Files

- [x] campaigns.csv (4 campaigns, all budget/bid/targeting)
- [x] ad_groups.csv (16 ad groups, all targeting)
- [x] keywords.csv (112 keywords, all match types)
- [x] ads.csv (RSAs with 15 headlines + 4 descriptions)
- [x] sitelinks.csv (12 sitelinks with URLs + descriptions)
- [x] callouts.csv (8 callouts with descriptions)
- [x] final_urls.csv (landing page mapping per ad group)
- [x] labels.csv (performance labels for tracking)

### Landing Page Preparation

- [x] A2KOI migration landing page optimized
- [x] Brand landing page (homepage) ready
- [x] Product category pages ready (6 categories)
- [x] Seasonal landing pages ready (spring, summer, fall, winter)
- [x] All pages have correct tracking tags
- [x] All pages mobile-optimized
- [x] All pages conversion tracking validated

### Documentation & Playbooks

- [x] README.md (comprehensive overview)
- [x] AGENT-INSTRUCTIES.md (AI agent playbook)
- [x] SYSTEEM-AUDIT.md (system integration audit)
- [x] CONVERSIE-TRACKING.md (tracking architecture)
- [x] CAMPAGNE-DETAILS.md (all campaign specs)
- [x] BUDGET-EN-KPI.md (budget model + KPIs)
- [x] This checklist
- [x] MCP tools reference
- [x] Ads Editor guide

---

## Week 1: Initial Launch (15–21 March)

### Day 1 (Friday, 15 March)

- [ ] **Morning (09:00):**
  - [ ] Final tracking validation (test purchase)
  - [ ] Verify all conversion labels firing in Google Ads
  - [ ] Confirm GA4 ↔ Ads sync (2h lag)
  - [ ] Verify budget allocation: €18 A2KOI, €14 Brand
  - [ ] Set team reminder: "Campaign import starts at 11:00"

- [ ] **Mid-morning (11:00):**
  - [ ] Download Google Ads Editor
  - [ ] Login to account 471-168-2842
  - [ ] Import campaigns.csv
  - [ ] Import ad_groups.csv
  - [ ] Review both imports for errors
  - [ ] Save local copy of imported data

- [ ] **Afternoon (14:00):**
  - [ ] Import keywords.csv
  - [ ] Import ads.csv
  - [ ] Review keywords (QA check)
  - [ ] Review ads (copy quality check)
  - [ ] Screenshot current state for records

- [ ] **Late afternoon (16:00):**
  - [ ] Import sitelinks.csv
  - [ ] Import callouts.csv
  - [ ] Import final_urls.csv
  - [ ] Import labels.csv
  - [ ] Do final Ads Editor validation (all objects present)
  - [ ] Post validation status to Slack

### Days 2–4 (Saturday–Tuesday, 16–18 March)

- [ ] **Campaign Review (in Ads Editor, still draft state):**
  - [ ] Campaign 1 (A2KOI Migratie):
    - [ ] Review 3 ad groups (Exact, Phrase, Closed)
    - [ ] Verify 30 keywords
    - [ ] Check 15 headlines + 4 descriptions
    - [ ] Verify landing page URLs
  - [ ] Campaign 2 (Brand Search):
    - [ ] Review 3 ad groups (Exact, Phrase, Generiek)
    - [ ] Verify 16 keywords
    - [ ] Check ad quality
    - [ ] Verify landing pages
  - [ ] Campaign 3 (Non-Brand Producten):
    - [ ] Review 6 ad groups
    - [ ] Verify 60 keywords
    - [ ] Check product category messaging
    - [ ] Verify landing pages per category
  - [ ] Campaign 4 (Seizoen Marieke):
    - [ ] Review 4 ad groups (Spring, Summer, Fall, Winter)
    - [ ] Verify 26 keywords
    - [ ] Check seasonal messaging
    - [ ] Verify seasonal landing pages

- [ ] **Quality Assurance:**
  - [ ] No duplicate keywords across ad groups
  - [ ] No misspelled brand names
  - [ ] All URLs are valid (no typos)
  - [ ] All landing pages respond with HTTP 200
  - [ ] All tracking parameters present in URLs
  - [ ] No obviously low-quality ads (no ALL CAPS, excessive punctuation)

- [ ] **Stakeholder Review:**
  - [ ] Schedule 30-min review call with Kees (account owner)
  - [ ] Walk through all 4 campaigns
  - [ ] Discuss targeting strategy per persona
  - [ ] Confirm budget allocation
  - [ ] Get sign-off on campaign structure

### Days 5–7 (Wednesday–Friday, 19–21 March)

- [ ] **Phase 1 Activation:**
  - [ ] **A2KOI Migratie campaign:**
    - [ ] Set to "Enabled" (was paused)
    - [ ] Verify bid strategy: Maximize Clicks
    - [ ] Confirm budget: €18/day
    - [ ] Verify targeting: Netherlands, Dutch
    - [ ] Check impressions flowing within 2 hours
  - [ ] **Brand Search campaign:**
    - [ ] Set to "Enabled" (was paused)
    - [ ] Verify bid strategy: Maximize Clicks
    - [ ] Confirm budget: €14/day
    - [ ] Verify targeting: Netherlands, Dutch
    - [ ] Check impressions flowing within 2 hours

- [ ] **Keep Paused (until Week 3):**
  - [ ] Campaign 3 (Non-Brand Producten) — paused
  - [ ] Campaign 4 (Seizoen Marieke) — paused

- [ ] **Live Monitoring (48 hours after activation):**
  - [ ] Check impressions: >500 expected
  - [ ] Check clicks: >50 expected
  - [ ] Check spend: €32 expected (€18+€14)
  - [ ] Check CTR: 5–10% expected (still learning)
  - [ ] Check conversion tracking: Any conversions yet?
  - [ ] Check for anomalies (errors, warnings in Ads UI)
  - [ ] Post 24h & 48h status reports to Slack

- [ ] **Post-Launch Documentation:**
  - [ ] Document activation timestamp
  - [ ] Screenshot campaign status (enabled)
  - [ ] Log first impressions, clicks, spend
  - [ ] Log first conversions (if any)
  - [ ] Document any issues or blockers

---

## Week 3: Phase 2 Expansion (29 March–4 April)

### Pre-Activation Review

- [ ] **Performance Evaluation (A2KOI + Brand):**
  - [ ] Total conversions since launch: ≥ 500?
  - [ ] Combined ROAS: ≥ 1.5x?
  - [ ] Combined conversion rate: ≥ 1.5%?
  - [ ] No major anomalies or tracking issues?
  - [ ] Budget spend tracking accurately?
  - [ ] Keyword performance in GSC positive?

- [ ] **Phase 1 Gate Check:**
  - [ ] ✓ Minimum 500 conversions
  - [ ] ✓ ROAS ≥ 1.5x
  - [ ] ✓ Conversion rate ≥ 1.5%
  - [ ] ✓ Stable for 7+ days

### Phase 2 Activation

- [ ] **Bid Strategy Migration (Phase 1 → Phase 2):**
  - [ ] A2KOI campaign: Switch to "Maximize Conversions" (from Maximize Clicks)
  - [ ] Brand campaign: Switch to "Maximize Conversions" (from Maximize Clicks)
  - [ ] Set conversion goal: `purchase` event (AW-17999886877/purchase-1)
  - [ ] Document timestamp of change

- [ ] **Launch Phase 2 Campaigns:**
  - [ ] Campaign 3 (Non-Brand Producten):
    - [ ] Set to "Enabled" (was paused)
    - [ ] Verify bid strategy: Maximize Conversions
    - [ ] Confirm budget: €25/day
    - [ ] Verify 6 ad groups active
    - [ ] Check impressions flowing
  - [ ] Campaign 4 (Seizoen Marieke):
    - [ ] Set to "Enabled" (was paused)
    - [ ] Verify bid strategy: Maximize Conversions
    - [ ] Confirm budget: €16/day
    - [ ] Verify 4 ad groups active
    - [ ] Check impressions flowing

- [ ] **Post-Activation Monitoring:**
  - [ ] Check all 4 campaigns active
  - [ ] Combined daily spend: ~€73/day
  - [ ] Monitor for 48 hours (any anomalies?)
  - [ ] Verify conversion tracking across all campaigns
  - [ ] Document status

---

## Week 5: Bid Strategy Upgrade (12–18 April)

### Phase 2 → Phase 3 Gate Check

- [ ] **Performance Validation:**
  - [ ] Total conversions (purchase only): ≥ 100/day?
  - [ ] Combined ROAS: ≥ 2.5x?
  - [ ] Combined conversion rate: ≥ 2.5%?
  - [ ] 14 consecutive days of stable metrics?
  - [ ] CPA tracking accurately?
  - [ ] No major tracking anomalies?

### Phase 3 Activation (Target CPA)

- [ ] **All Campaigns: Switch to Target CPA:**
  - [ ] A2KOI Migratie: Target CPA €20
  - [ ] Brand Search: Target CPA €17
  - [ ] Non-Brand Producten: Target CPA €25
  - [ ] Seizoen Marieke: Target CPA €28
  - [ ] Verify conversion goal is set (purchase)
  - [ ] Document timestamp

- [ ] **Monitoring Phase 3:**
  - [ ] CPA stability (within ±15% of target for 3 days)
  - [ ] Conversion volume stable?
  - [ ] ROAS maintaining ≥ 3.0x?
  - [ ] Budget utilization ≥ 80%?

---

## Week 9+: Long-Term Optimization (9 May+)

### Phase 3 → Phase 4 Gate Check

- [ ] **Readiness for Target ROAS:**
  - [ ] Target CPA stable for 4+ weeks?
  - [ ] ROAS consistently 3.0–3.5x?
  - [ ] No major seasonal changes forecast?
  - [ ] Budget infrastructure ready?

### Phase 4 Activation (Target ROAS)

- [ ] **All Campaigns: Switch to Target ROAS:**
  - [ ] Target ROAS: 3.5x (all campaigns)
  - [ ] Verify conversion goal (purchase)
  - [ ] Document timestamp

---

## Ongoing: Daily/Weekly Tasks

### Daily (09:00 CET)

- [ ] Budget sync (revenue tracking, formula check)
- [ ] No major anomalies overnight?
- [ ] All campaigns active?
- [ ] Spend on track?

### Daily (14:00 CET)

- [ ] Keyword performance check (top 10 keywords)
- [ ] Anomaly detection (ROAS, CPA, conversion rate)
- [ ] Any underperforming keywords to pause?

### Daily (18:00 CET)

- [ ] Conversion tracking validation (GA4 ↔ Ads sync)
- [ ] Conversion count matches expected?
- [ ] Sync rate ≥ 90%?

### Weekly (Monday 10:00 CET)

- [ ] Budget review meeting with Kees
- [ ] Performance summary (ROAS, CPA, conversions)
- [ ] Search term analysis (GSC top queries)
- [ ] Keyword changes needed?
- [ ] Bid strategy adjustments?
- [ ] New negative keywords?

### Weekly (Friday 14:00 CET)

- [ ] Upcoming week forecast (revenue, seasonal)
- [ ] Any anticipated budget changes?
- [ ] Phase gate evaluation (if applicable)

### Monthly (1st of month, 09:00 CET)

- [ ] Full performance report (all KPIs)
- [ ] Compare to prior month
- [ ] Identify trends & patterns
- [ ] Plan next month strategy
- [ ] Update budget model
- [ ] Seasonal adjustments (if needed)

---

## Future Phases (Planned)

### Fase 2: Retargeting + Belgium (May 2026)

- [ ] Retargeting campaign (website visitors)
- [ ] Dynamic retargeting ads (product-specific)
- [ ] Belgium market expansion
  - [ ] GMC feed: Add Belgium to target countries
  - [ ] Translate ads to Dutch (Belgium variant)
  - [ ] Adapt landing pages for Belgian market
  - [ ] Set up separate campaigns for BE market

### Fase 3: Customer Match & Lookalikes (June 2026)

- [ ] Customer Match audience (existing customers from Shopify)
- [ ] Lookalike audiences (based on high-value customers)
- [ ] Shopping campaigns (enabled once GMC NL issue fixed)
- [ ] Performance Max campaigns (cross-channel)

### Fase 4: Advanced Optimization (July+ 2026)

- [ ] Bid strategy: Target ROAS optimization
- [ ] Enhanced conversions (offline + online)
- [ ] Consent Mode v2 (GDPR compliance)
- [ ] Cross-device attribution
- [ ] CLV-based bidding (if data available)

---

## Rollback Procedures

If critical issues occur, use these procedures:

### Immediate Rollback (Pause All)

**Trigger:** ROAS drops below 1.0x, tracking broken, or budget bleed >50%

**Steps:**
1. Pause all campaigns immediately
2. Document error/issue
3. Post to Slack #google-ads-alerts
4. Contact Kees: kees@vijvercentrum.nl
5. Investigate root cause
6. Fix issue
7. Resume campaigns after approval

### Partial Rollback (Pause Campaign)

**Trigger:** Single campaign ROAS < 1.0x for 6+ hours

**Steps:**
1. Pause affected campaign
2. Document which campaign + timestamp
3. Investigate issue (tracking, keywords, creatives)
4. Fix root cause
5. Resume after verification

### Bid Strategy Rollback (Step Back One Phase)

**Trigger:** Phase gate criteria not met after 7 days

**Example:** ROAS stays <1.5x during Phase 1

**Steps:**
1. Keep bid strategy for 3 more days
2. If still <1.5x: Revert to previous bid strategy
3. Document revert timestamp
4. Increase data collection period
5. Re-evaluate phase gate after 7 more days

---

## Success Criteria (End States)

### Week 1 Success

```
✓ 2 campaigns live (A2KOI + Brand)
✓ >500 impressions
✓ >50 clicks
✓ Spending ~€32/day
✓ No major tracking issues
✓ Conversions flowing (any)
```

### Week 3 Success

```
✓ All 4 campaigns live
✓ Phase 1 gate met (500 conv, 1.5x ROAS, 1.5% conv rate)
✓ Bid strategies upgraded to Maximize Conversions
✓ Spending ~€73/day
✓ Conversion quality stable
```

### Week 5 Success

```
✓ Phase 2 gate met (100+ daily conv, 2.5x ROAS, 2.5% conv rate)
✓ Bid strategies upgraded to Target CPA
✓ CPA stable within targets
✓ Spending ~€73/day
✓ Ready for Phase 3
```

### Month 1 Success

```
✓ Total spend: ~€1,971 (27 days × €73)
✓ Phase 3 readiness confirmed
✓ All KPI targets met or exceeded
✓ No major issues or anomalies
✓ Team trained on all tools
```

---

**Launch Date:** 15 March 2026
**Last Updated:** 15 March 2026
**Next Review:** 22 March 2026
**Contact:** kees@vijvercentrum.nl (any blockers/issues)
