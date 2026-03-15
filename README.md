# 🐟 Vijvercentrum.nl — GOAT Google Ads Account

**Google Ads Account ID:** 471-168-2842
**MCC (Retailz BV):** 994-144-9739
**Status:** ✅ Live & Optimizing
**Daily Budget:** €91 (5% van 7-day rolling revenue average)
**MTD Spend:** [See BUDGET-EN-KPI.md]

---

## Wat is deze repo?

Dit is een **complete 360° Google Ads strategie- en implementatie repository** voor Vijvercentrum.nl — een Nederlandse online webwinkel voor vijverproducten en koivoer. De repo bevat:

- **Campagnestructuur & configuratie** — 4 gekalibreerde Search campagnes
- **Persona-driven targeting** — twee kernpersona's (Henk & Marieke)
- **Tracking architecture** — GA4 ↔ Google Ads linkage, conversie-labels, UTM setup
- **System audit** — alle integraties (Shopify, Klaviyo, GMC, GSC, Clarity)
- **AI Agent instructies** — complete playbook voor automatisering via MCP tools
- **CSV import bestanden** — 8 bestanden klaar voor Ads Editor import (campaigns, ad groups, keywords, ads, sitelinks, callouts)
- **Budget & KPI model** — dynamische budgetformule, bid strategy roadmap, anomaly detection

---

## Inhoudsopgave

1. [Wat zit er in deze repo?](#wat-zit-er-in-deze-repo)
2. [Campagnestructuur](#campagnestructuur)
3. [Persona's](#personas)
4. [Ads Editor Import](#ads-editor-import)
5. [Wat is er live ingesteld?](#wat-is-er-live-ingesteld)
6. [Tools & Integraties](#tools--integraties)
7. [Budget Model](#budget-model)
8. [KPI Targets](#kpi-targets)
9. [Lancering Checklist](#lancering-checklist)
10. [Voor AI Agents](#voor-ai-agents)

---

## Wat zit er in deze repo?

```
/tmp/vijvercentrum-google-ads/
├── README.md                          ← Dit bestand
├── .gitignore
└── docs/
    ├── AGENT-INSTRUCTIES.md           ← Complete AI agent playbook
    ├── SYSTEEM-AUDIT.md               ← Alle integraties & findings
    ├── CONVERSIE-TRACKING.md          ← Conversion label architecture
    ├── CAMPAGNE-DETAILS.md            ← Full campaign specs
    ├── BUDGET-EN-KPI.md               ← Budget formule & KPI's
    ├── LANCERING-CHECKLIST.md         ← Phased rollout checklist
    └── tools/
        ├── RETAILZ-MCP-TOOLS.md       ← MCP tool reference
        └── GOOGLE-ADS-EDITOR.md       ← CSV import handleiding
```

### CSV Import Bestanden (in AGENT-INSTRUCTIES.md)

8 bestanden klaar voor Ads Editor import — volgende volgorde:

1. **campaigns.csv** — 4 search campagnes (budgets, bid strategies, targeting)
2. **ad_groups.csv** — 16 ad groups verdeeld over 4 campagnes
3. **keywords.csv** — 112 keywords (exact, phrase, broad match modified)
4. **ads.csv** — Responsive Search Ads met 15 headlines + 4 descriptions
5. **sitelinks.csv** — 12 sitelink extensions
6. **callouts.csv** — 8 callout extensions
7. **final_urls.csv** — Landing page mapping per ad group
8. **labels.csv** — Labels voor campagne tracking & performance grouping

---

## Campagnestructuur

| Campaign ID | Naam | Type | Budget/dag | Bid Strategy | Status | Personas |
|---|---|---|---|---|---|---|
| 1 | [Vijvercentrum] 01 - A2KOI Migratie | Search | €18 | Maximize Clicks | Paused (Week 1) | Henk |
| 2 | [Vijvercentrum] 02 - Brand Search | Search | €14 | Maximize Clicks | Paused (Week 1) | Both |
| 3 | [Vijvercentrum] 03 - Non-Brand Producten | Search | €25 | Maximize Conversions | Paused (Week 3) | Henk |
| 4 | [Vijvercentrum] 04 - Seizoen Marieke | Search | €16 | Maximize Conversions | Paused (Week 3) | Marieke |
| | | | | | | |
| **TOTAL** | | | **€73/dag** | | | |
| *Reserved* | Fase 2: Retargeting + België | | €18/dag | — | Planned | — |

**Nota:** €91 daily budget = €73 campaigns + €18 reserve

---

## Persona's

### 👨 Henk — De Technische Vijverman (55+)

- **Profiel:** Ervaren vijvereigenaar, kent alle merken en producten
- **Search gedrag:** Specifieke zoekopdrachten (merk + producttype)
- **Intent:** Exact wat hij zoekt, weinig afdwaling
- **Campagnes:** A2KOI Migratie, Brand Search, Non-Brand Producten
- **Keywords:** High intent, long-tail, product-centric
- **Device:** Desktop/laptop primair
- **Jaarlijks budget vijver:** €800–2000

### 👩 Marieke — De Nieuwe Vijvereigenaar (35–50)

- **Profiel:** Relatief nieuw met vijver, zoekt advies en ondersteuning
- **Search gedrag:** Seizoensgebonden, breed spectrum
- **Intent:** Wil leren, zoekt solutions voor problemen
- **Campagnes:** Seizoen Marieke, Brand Search
- **Keywords:** Informational + transactional, product guidance
- **Device:** Mobile + desktop balanced
- **Jaarlijks budget vijver:** €300–800

---

## Ads Editor Import

**Stap-voor-stap handleiding in `docs/tools/GOOGLE-ADS-EDITOR.md`**

### Import volgorde (KRITIEK):

```
1. campaigns.csv       ← Maakt 4 campagnes aan
   ↓
2. ad_groups.csv      ← Maakt 16 ad groups aan (relies on campaigns)
   ↓
3. keywords.csv       ← Voegt 112 keywords toe (relies on ad_groups)
   ↓
4. ads.csv            ← Voegt RSAs toe (relies on ad_groups)
   ↓
5. sitelinks.csv      ← Voegt 12 sitelinks toe
   ↓
6. callouts.csv       ← Voegt 8 callouts toe
   ↓
7. final_urls.csv     ← Zet landing pages
   ↓
8. labels.csv         ← Voegt tracking labels toe

DONE → Paused activeren per fase
```

---

## Wat is er live ingesteld?

### ✅ Tracking

- **Tracking template:** `{lpurl}?utm_source=google&utm_medium=cpc&utm_campaign={_campaign}&utm_content={creative}&utm_term={keyword}`
- **Auto-tagging:** ✅ ON (sinds 7 maart 2026)
- **GA4 linkage:** ✅ Linked (Property 478336344)
- **Conversion tracking:** ✅ 4 goals fixed (purchase, begin_checkout, add_to_cart, view_item)

### ✅ Negative Keywords (27 total)

**Competitors:** intratuin, hornbach, gamma, praxis, koiplanet, acqua

**Product categories:** aquarium, zwembad, vijvertuin, terrainium

**Job/Service:** vacatures, werkingen, reparatie dienst

**Commercial:** gratis, korting code, cashback, review

**Miscellaneous:** auto, boot, camping, restaurant

### ✅ Conversion Goals Fixed (15 March 2026)

| Label | Conversion | Status |
|---|---|---|
| AW-17999886877/purchase-1 | Purchase (Revenue) | ✅ Fixed |
| AW-17999886877/begin_checkout-1 | Begin Checkout | ✅ Fixed |
| AW-17999886877/add_to_cart-1 | Add to Cart | ✅ Fixed |
| AW-17999886877/view_item-1 | View Item (Observation) | ✅ Fixed |

### ✅ Ad Extensions

- **12 Sitelinks** — Product categories, Blog, FAQ, Contact
- **8 Callouts** — Free shipping, Expert advice, 24h support, etc.
- **Call extension** — +31 (0)6 12345678 (on request)

---

## Tools & Integraties

| System | ID/Account | Status | Purpose |
|---|---|---|---|
| **Google Ads** | 471-168-2842 | ✅ Active | Campaign management |
| **GA4** | G-9HQRM66093 (Property 478336344) | ✅ Active | Conversion tracking, intent analysis |
| **Google Search Console** | sc-domain:vijvercentrum.nl | ✅ Active | Keyword performance, CTR, position |
| **Google Merchant Center** | 5743476888 | ⚠️ Limited | PMax support (NL NOT in feed!) |
| **Shopify** | vijvercentrum.myshopify.com | ✅ Active | Revenue, product data, customer |
| **Klaviyo** | SNdxLL (4371218771) | ✅ Active | Email follow-up, audience sync |
| **Clarity** | vv2q87c0to | ✅ Active | User behavior tracking |
| **Picqer** | (Commercial) | ✅ Active | Inventory, fulfillment |

**Zie `docs/SYSTEEM-AUDIT.md` voor volledige audit & API status.**

---

## Budget Model

### Formule

```
Dagbudget = (7-day rolling average daily revenue) × 5%
Minimum: €15/dag
Maximum: €200/dag (Q1 2026)
```

### Huidigestatus (15 maart 2026)

- **7-day rolling avg revenue:** €1,825/dag
- **Calculated budget:** €91/dag
- **Actual allocation:** €73/dag + €18 reserve

### Fasen

| Fase | Datum | Budget | Focus |
|---|---|---|---|
| **Phase 0** | 7–14 maart | €50 | Migratie + setup |
| **Phase 1** | 15–28 maart | €73 | A2KOI + Brand campaigns |
| **Phase 2** | 29 maart–11 april | €91 | Non-Brand + Seizoen activation |
| **Phase 3** | 12 april+ | €110–130 | Bid strategy upgrade + Belgium |

### Beschikbare Credits

- **Promo credit:** €1,200 (spend €2,400 before 6 May 2026 to claim)

---

## KPI Targets

| Campaign | Target CTR | Target CPA | Target ROAS | Conv Rate | Impression Share |
|---|---|---|---|---|---|
| A2KOI Migratie | 8–10% | €18–22 | 3.5x | 4–5% | >70% |
| Brand Search | 12–15% | €15–18 | 4.0x | 5–6% | >80% |
| Non-Brand Producten | 5–7% | €22–28 | 3.0x | 3–4% | >60% |
| Seizoen Marieke | 4–6% | €25–32 | 2.8x | 2–3% | >50% |

**Baseline metrics:**
- Google/cpc (old) = 0.39% conv rate → NL NOT in GMC feed (CRITICAL FINDING)
- Organic = 2.21% conv rate
- Email = 6.5% conv rate

---

## Lancering Checklist

### Pre-Launch ✅ (Complete)

- [x] Conversion goals fixed (purchase, begin_checkout, add_to_cart, view_item)
- [x] Tracking template configured
- [x] 27 negative keywords added
- [x] 8 CSV import files created
- [x] RSAs expanded (15 headlines, 4 descriptions per ad group)
- [x] GA4 ↔ Ads linkage verified
- [x] Personas & landing pages mapped

### Week 1 (15–21 maart)

- [ ] Import campaigns.csv via Ads Editor
- [ ] Import ad_groups.csv through ads.csv (in order)
- [ ] Review all campaigns in draft state
- [ ] Verify targeting, keywords, ad copy
- [ ] **Activate:** A2KOI Migratie campaign
- [ ] **Activate:** Brand Search campaign
- [ ] Monitor first 48 hours (anomalies, tracking)

### Week 3 (29 maart–4 april)

- [ ] Evaluate A2KOI + Brand performance
- [ ] Switch A2KOI to "Maximize Conversions" bid strategy
- [ ] **Activate:** Non-Brand Producten campaign
- [ ] **Activate:** Seizoen Marieke campaign
- [ ] Review conversion data (GA4 ↔ Ads sync)

### Week 5 (12–18 april)

- [ ] Switch all campaigns to "Maximize Conversions" (if ROAS > 3.0x)
- [ ] Consider "Target CPA" bid strategy
- [ ] Start Customer Match setup
- [ ] Plan Belgium campaign (Fase 2)

### Week 9+ (9 mei+)

- [ ] Evaluate "Target ROAS" bid strategy readiness
- [ ] Launch retargeting campaigns (Fase 2)
- [ ] Belgium market expansion

### Ongoing

- [ ] Weekly budget review (revenue tracking)
- [ ] Bid strategy optimization (phase gates)
- [ ] Keyword performance reviews
- [ ] Conversion tracking validation

---

## Voor AI Agents

**Complete AI agent playbook:** `docs/AGENT-INSTRUCTIES.md`

**Bevat:**
- Account details & API status
- Available MCP tools (Shopify, Klaviyo, GA4, GSC, GMC, Picqer, Chrome, Gmail)
- Campaign naming convention & budget rules
- Conversion hierarchy & tracking setup
- Negative keyword strategy
- Critical findings (GMC NL issue, PMax 0.39% conv rate)
- Bid strategy roadmap phases
- Weekly/daily automation tasks

**MCP tools reference:** `docs/tools/RETAILZ-MCP-TOOLS.md`

---

## Links

- **Account Dashboard:** https://ads.google.com/aw/campaigns?cid=471-168-2842
- **MCC Dashboard:** https://ads.google.com/aw/mcc/overview?cid=994-144-9739
- **GA4 Property:** https://analytics.google.com/analytics/web/#/p/478336344
- **Shopify Store:** https://admin.shopify.com/store/vijvercentrum
- **Google Merchant Center:** https://merchants.google.com/mc/5743476888

---

**Last updated:** 15 March 2026
**Maintained by:** Retailz AI Agents & Human Team
**License:** Internal (Vijvercentrum)
