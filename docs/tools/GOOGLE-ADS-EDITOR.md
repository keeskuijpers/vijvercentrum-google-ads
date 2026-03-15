# Google Ads Editor Import Guide — Vijvercentrum

**Version:** 1.0 | **Last Updated:** 15 March 2026 | **Purpose:** Step-by-step CSV import to Google Ads

---

## Prerequisites

- Google Ads Editor (download: https://ads.google.com/aw/tools/editor)
- Account ID: 471-168-2842 (Vijvercentrum)
- All 8 CSV files ready (campaigns through labels)
- Account owner login credentials
- ~30 minutes of time

---

## Step 1: Download & Install Google Ads Editor

1. Visit: https://ads.google.com/aw/tools/editor
2. Download for your OS (Windows, Mac, Linux)
3. Run installer
4. Launch Google Ads Editor

---

## Step 2: Login to Account

1. Open Google Ads Editor
2. Click "Account" → "Log In"
3. Enter Google account email
4. Authenticate with account owner credentials
5. Select account **471-168-2842 (Vijvercentrum.nl)**
6. Click "Download"
7. Wait for download to complete (may take 5 minutes)

---

## Step 3: Import CSV Files (Phased Approach)

**CRITICAL:** Import files in EXACT order. Each import depends on previous ones.

### Phase 1: Foundation (Campaigns & Structure)

#### Import 1: campaigns.csv

```
Step 1: In Google Ads Editor, click "File" → "Import"
Step 2: Select campaigns.csv
Step 3: In import dialog:
        - Map CSV columns to Ads Editor fields
        - Campaign Name → {Campaign}
        - Budget → {Budget}
        - Bid Strategy → {Bid Strategy}
        - Status → Leave PAUSED (for phased activation)
Step 4: Click "Next"
Step 5: Review preview (should show 4 campaigns)
Step 6: Click "Import"
Step 7: Wait for completion (usually <1 min)
Step 8: Take screenshot of imported campaigns
```

**Verification after import:**
- [ ] 4 campaigns appear in left panel
- [ ] Campaign names match pattern: [Vijvercentrum] XX - Name
- [ ] Budgets: €18, €14, €25, €16
- [ ] All campaigns show "Paused" status
- [ ] No errors in import summary

#### Import 2: ad_groups.csv

```
Step 1: File → Import
Step 2: Select ad_groups.csv
Step 3: In import dialog:
        - Ad Group Name → {Ad Group}
        - Campaign → {Campaign} (will link to imported campaigns)
        - Status → Leave PAUSED
Step 4: Review preview (should show 16 ad groups)
Step 5: Import
Step 6: Verify in left panel: campaigns now show child ad groups
```

**Verification:**
- [ ] 16 ad groups imported
- [ ] Organized under 4 campaigns
- [ ] Ad Group names match expected structure
- [ ] No import errors

### Phase 2: Keywords & Content

#### Import 3: keywords.csv

```
Step 1: File → Import
Step 2: Select keywords.csv
Step 3: In import dialog:
        - Keyword → {Keyword}
        - Match Type → {Match Type} (Exact, Phrase, Broad)
        - Ad Group → {Ad Group}
        - Status → Leave PAUSED
Step 4: Review preview (should show 112 keywords)
Step 5: Import
Step 6: Wait (may take 1–2 min for 112 keywords)
```

**Verification:**
- [ ] 112 keywords imported
- [ ] Match types correct (exact, phrase, broad modified)
- [ ] All keywords linked to correct ad groups
- [ ] No duplicate keywords within ad groups
- [ ] No obvious misspellings

#### Import 4: ads.csv (Responsive Search Ads)

```
Step 1: File → Import
Step 2: Select ads.csv
Step 3: In import dialog:
        - Headline 1–15 → {Headline 1–15}
        - Description 1–4 → {Description 1–4}
        - Ad Group → {Ad Group}
        - Final URL → Specify separately (next import)
Step 4: Review preview (each ad group should have 1 RSA)
Step 5: Import
```

**Verification:**
- [ ] RSAs imported (1 per ad group = 16 RSAs)
- [ ] Each RSA has 15 headlines visible
- [ ] Each RSA has 4 descriptions visible
- [ ] Headlines and descriptions are thematic to campaign
- [ ] No import errors

### Phase 3: Extensions & URLs

#### Import 5: sitelinks.csv

```
Step 1: File → Import
Step 2: Select sitelinks.csv
Step 3: In import dialog:
        - Sitelink Text → {Text}
        - Final URL → {URL}
        - Description Line 1–2 → {Description}
        - Campaign → {Campaign} (applies to all campaigns equally)
Step 4: Review preview (should show 12 sitelinks)
Step 5: Import
```

**Verification:**
- [ ] 12 sitelinks imported
- [ ] Sitelinks assigned to campaigns
- [ ] URLs are valid (no typos)
- [ ] Descriptions are concise and relevant

#### Import 6: callouts.csv

```
Step 1: File → Import
Step 2: Select callouts.csv
Step 3: In import dialog:
        - Callout Text → {Text}
        - Campaign → {Campaign}
Step 4: Review preview (should show 8 callouts)
Step 5: Import
```

**Verification:**
- [ ] 8 callouts imported
- [ ] Text is compelling and concise
- [ ] No duplicate callouts
- [ ] Applied at campaign level

#### Import 7: final_urls.csv

```
Step 1: File → Import
Step 2: Select final_urls.csv
Step 3: In import dialog:
        - Final URL → {URL}
        - Ad Group → {Ad Group}
Step 4: Review preview (should show landing page per ad group)
Step 5: Import
```

**Verification:**
- [ ] Landing pages assigned to ad groups
- [ ] URLs are valid (no 404s)
- [ ] URLs match landing page strategy
  - A2KOI → /collections/a2koi-alternatie
  - Brand → homepage or /collections/all
  - Product → /collections/{category}
  - Seasonal → /guides/{season}

#### Import 8: labels.csv (Tracking Labels)

```
Step 1: File → Import
Step 2: Select labels.csv
Step 3: In import dialog:
        - Label → {Label Name}
        - Campaign → {Campaign}
Step 4: Review preview (should show labels for tracking)
Step 5: Import
```

**Verification:**
- [ ] Labels imported
- [ ] Useful for reporting & campaign grouping

---

## Step 4: Post-Import QA Checklist

### Structure Validation

- [ ] **4 Campaigns:**
  - [Vijvercentrum] 01 - A2KOI Migratie
  - [Vijvercentrum] 02 - Brand Search
  - [Vijvercentrum] 03 - Non-Brand Producten
  - [Vijvercentrum] 04 - Seizoen Marieke

- [ ] **16 Ad Groups:**
  - Campaign 1: 3 ad groups (Exact, Phrase, Closed)
  - Campaign 2: 3 ad groups (Exact, Phrase, Generiek)
  - Campaign 3: 6 ad groups (Koivoer, Filters, Pumps, Plants, Aanleg, UV-C)
  - Campaign 4: 4 ad groups (Spring, Summer, Fall, Winter)

- [ ] **112 Keywords** distributed across ad groups

- [ ] **16 Responsive Search Ads** (1 per ad group)

- [ ] **12 Sitelinks** + **8 Callouts** applied

- [ ] **16 Landing Page URLs** (1 per ad group)

### Data Quality Checks

- [ ] No duplicate keywords within same ad group
- [ ] No misspelled product names or brand names
- [ ] All URLs are valid (no obvious typos)
- [ ] All landing pages return HTTP 200 (not 404)
- [ ] Tracking parameters present in URLs (utm_source=google, etc.)
- [ ] Ad copy matches persona messaging
  - Henk persona: Technical specs, brand names, product features
  - Marieke persona: Guidance, seasonal advice, beginner-friendly
- [ ] No profanity or policy violations in ad copy
- [ ] Quality Score predictions (should be 6–8 range for most ads)

### Campaign Settings Validation

- [ ] **Budget per campaign:**
  - Campaign 1: €18/day
  - Campaign 2: €14/day
  - Campaign 3: €25/day
  - Campaign 4: €16/day
  - Total: €73/day (+ €18 reserve)

- [ ] **Bid Strategy:**
  - All campaigns: "Maximize Clicks" (ready for Phase 2 upgrade)

- [ ] **Targeting:**
  - Location: Netherlands
  - Language: Dutch
  - Device: All

- [ ] **Status:**
  - All campaigns: "Paused" (ready for phased activation)

- [ ] **Conversion Tracking:**
  - Conversion label: AW-17999886877/purchase-1 (visible in settings)

---

## Step 5: Pre-Launch Final Review

Before clicking "Upload", do final human review:

1. **Review Campaign Strategy:**
   - [ ] Campaign 1 targets A2KOI migration (high-intent)
   - [ ] Campaign 2 protects brand searches
   - [ ] Campaign 3 captures product searches (Henk persona)
   - [ ] Campaign 4 targets seasonal searches (Marieke persona)

2. **Review Budget Allocation:**
   - [ ] €73/day is 5% of 7-day avg revenue (€1,825)
   - [ ] Distribution matches performance strategy (product-heavy)

3. **Review Ad Copy & Keywords:**
   - [ ] Ad copy is professional and brand-aligned
   - [ ] Keywords match search intent
   - [ ] No accidental keyword overlap causing competition

4. **Review Landing Pages:**
   - [ ] Every ad group has landing page assigned
   - [ ] Landing pages are relevant to ad copy
   - [ ] Landing pages load without errors

5. **Sign-Off:**
   - [ ] Campaign owner (Kees) approves
   - [ ] No policy violations detected
   - [ ] Team ready for activation

---

## Step 6: Upload to Google Ads

Once all QA passed:

```
Step 1: In Google Ads Editor, click "File" → "Upload"
Step 2: Review summary:
        - 4 campaigns to add
        - 16 ad groups to add
        - 112 keywords to add
        - 16 ads to add
        - Extensions to add
Step 3: Click "Upload"
Step 4: Wait for upload to complete (may take 2–5 minutes)
Step 5: Confirm "Upload successful"
Step 6: Take screenshot of confirmation
Step 7: Close Google Ads Editor
```

---

## Step 7: Verify in Google Ads UI

Go to https://ads.google.com/aw/campaigns?cid=471-168-2842

```
Step 1: Login to Google Ads account
Step 2: Verify 4 campaigns appear in campaign list
Step 3: Click into each campaign to verify:
        - Ad groups present
        - Keywords present
        - Ads present
        - Extensions present
        - Budget set correctly
        - Status: Paused (until activation)
Step 4: Check that all campaigns show €0 spend (haven't been activated yet)
Step 5: Document screenshots for records
```

---

## Step 8: Phased Activation

**DO NOT ACTIVATE ALL AT ONCE.** Follow phased rollout:

### Week 1: Activate Phase 1 (A2KOI + Brand)

```
Campaign 1 - A2KOI Migratie:
- Go to campaign settings
- Status: Change from "Paused" to "Enabled"
- Save
- Verify impressions appear within 2 hours

Campaign 2 - Brand Search:
- Go to campaign settings
- Status: Change from "Paused" to "Enabled"
- Save
- Verify impressions appear within 2 hours
```

**Monitor for 48 hours:**
- [ ] Impressions flowing?
- [ ] Clicks occurring?
- [ ] Spend tracking?
- [ ] Conversions flowing?
- [ ] No anomalies?

### Week 3: Activate Phase 2 (All 4 Campaigns)

```
Campaign 3 - Non-Brand Producten:
- Go to campaign settings
- Status: Change from "Paused" to "Enabled"
- Save

Campaign 4 - Seizoen Marieke:
- Go to campaign settings
- Status: Change from "Paused" to "Enabled"
- Save
```

**Monitor for 48 hours:**
- [ ] All campaigns active?
- [ ] Combined spend ~€73/day?
- [ ] Conversions stable?
- [ ] No errors?

---

## Troubleshooting

### Issue: "Campaign names don't match" during import

**Cause:** Typo in CSV or in Ads Editor field mapping

**Fix:**
1. Cancel import
2. Check CSV campaign names vs. Ads Editor
3. Ensure exact match (including spaces, punctuation)
4. Re-import

### Issue: "Ad Groups not linking to Campaigns"

**Cause:** Campaign names in ad_groups.csv don't match campaigns.csv

**Fix:**
1. Open ad_groups.csv
2. Check "Campaign" column matches exact campaign name in Ads Editor
3. Re-import with correct names

### Issue: "Keywords not showing in ad groups"

**Cause:** Ad group names in keywords.csv are typos

**Fix:**
1. Open keywords.csv
2. Verify ad group names match what was imported in ad_groups.csv
3. Correct typos
4. Re-import keywords.csv

### Issue: "Landing page URLs are showing errors"

**Cause:** URL typos or pages don't exist

**Fix:**
1. Test all URLs in browser manually
2. Verify pages exist and load without 404
3. Correct URLs in final_urls.csv
4. Re-import

### Issue: "Import fails with 'Duplicate keyword in ad group'"

**Cause:** Same keyword appears twice in ad group (same match type)

**Fix:**
1. Open keywords.csv
2. Find and remove duplicates
3. Re-import

### Issue: "Campaigns activated but no impressions after 2 hours"

**Cause:** Keywords not approved, ads under review, or targeting too narrow

**Fix:**
1. Go to Google Ads UI
2. Check keyword status (all should be "Enabled", not "Under review")
3. Check ad status (all should be "Enabled", not "Under review")
4. Check ad quality score (look for warnings)
5. Wait another 2 hours (Google takes time to process)
6. If still 0: Investigate campaign settings (budget, bidding, geo targeting)

---

## Quick Reference: Import Order

```
1. campaigns.csv      ← Foundation (4 campaigns)
2. ad_groups.csv      ← Structure (16 ad groups)
3. keywords.csv       ← Keywords (112 keywords)
4. ads.csv            ← RSA copy (16 ads)
5. sitelinks.csv      ← Extensions (12)
6. callouts.csv       ← Extensions (8)
7. final_urls.csv     ← Landing pages (16)
8. labels.csv         ← Tracking (labels)

DONE → Upload → Verify in UI → Phased Activation
```

---

## Support

**If import fails or you need help:**

1. Check this guide for troubleshooting
2. Take screenshot of error message
3. Post to internal Slack #google-ads-alerts
4. Tag @Kees
5. Include screenshot + CSV row causing issue

**Emergency contact:** kees@vijvercentrum.nl

---

**Last updated:** 15 March 2026 | **Created:** 15 March 2026
