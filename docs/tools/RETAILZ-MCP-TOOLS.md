# Retailz MCP Tools Reference — Google Ads Integration

**Version:** 1.0 | **Last Updated:** 15 March 2026 | **Status:** Reference Document

This document lists all available Retailz MCP (Model Context Protocol) tools that are relevant to the Vijvercentrum Google Ads account.

---

## Overview

**Total Available Tool Categories:** 8 (Shopify, Klaviyo, Google, Picqer, Search, Belco, Chrome, Gmail)

**Google Ads Specific Tools:** 2 read-only (GA4, GSC, GMC, GADS)

**Chrome Automation:** Available for Google Ads UI when API access blocked

---

## 1. Shopify Integration Tools

**Purpose:** Manage products, orders, customers, inventory from Shopify store

**Store:** vijvercentrum.myshopify.com

### Product Tools

#### `shopify_shop_info`
- **What:** Fetch store metadata
- **Returns:** Store name, domain, plan, currency, timezone, email
- **Use when:** Validating store connection, getting baseline info
- **Example:** `shopify_shop_info()` → Store ID, email, plan type

#### `shopify_products`
- **What:** Search products by title or filter by collection/status
- **Parameters:** query (search), collection_id, status (active/draft/archived), limit
- **Returns:** Product list with IDs, titles, types, vendors, pricing
- **Use when:** Finding products for audience targeting, inventory checks
- **Example:** `shopify_products(query="koivoer", status="active", limit=50)`

#### `shopify_product`
- **What:** Get full product details including variants, images, descriptions
- **Parameters:** product_id
- **Returns:** Product data + variants + metafields + collection mappings
- **Use when:** Verifying product content, pricing, availability
- **Example:** `shopify_product(product_id="123")`

#### `shopify_product_update`
- **What:** Update product metadata (title, description, price, status, tags, vendor)
- **Parameters:** product_id, title, body_html, status, tags, vendor, product_type, price
- **Returns:** Updated product object
- **Use when:** Bulk product updates for campaigns (e.g., tagging seasonal products)
- **Example:** `shopify_product_update(product_id="123", tags="seizoen-voorjaar")`

#### `shopify_collections`
- **What:** List all custom and smart collections
- **Parameters:** type (smart/custom/both), limit
- **Returns:** Collection list with titles, product counts, handles
- **Use when:** Finding landing page paths, collection structure
- **Example:** `shopify_collections(type="both", limit=50)`

### Order & Customer Tools

#### `shopify_orders`
- **What:** List orders filtered by status, date, fulfillment status
- **Parameters:** status (open/closed/cancelled/any), financial_status, fulfillment_status, created_at_min, limit
- **Returns:** Order IDs, totals, customer info, status
- **Use when:** Revenue tracking, anomaly detection, business metrics
- **Example:** `shopify_orders(status="closed", limit=50)` → Get last 50 completed orders

#### `shopify_order`
- **What:** Get complete order details (items, customer, shipping, payments)
- **Parameters:** order_id
- **Returns:** Full order data including items, quantities, prices, shipping address, payment method
- **Use when:** Understanding order composition, AOV analysis, customer insights
- **Example:** `shopify_order(order_id="123")` → Full order breakdown

#### `shopify_customers`
- **What:** Search customers by name or email
- **Parameters:** query (name/email), limit
- **Returns:** Customer list with IDs, emails, order counts, lifetime value
- **Use when:** Finding customer segments, building audiences, customer analysis
- **Example:** `shopify_customers(query="henk@", limit=20)`

#### `shopify_customer`
- **What:** Get full customer profile including addresses, order history, tags
- **Parameters:** customer_id
- **Returns:** Customer data + all orders + addresses + custom attributes
- **Use when:** Customer deep-dive, lifetime value, repeat purchase patterns
- **Example:** `shopify_customer(customer_id="456")`

### Inventory Tools

#### `shopify_inventory`
- **What:** Get current stock levels for products across locations
- **Parameters:** inventory_item_ids (comma-separated), location_ids (comma-separated)
- **Returns:** Stock levels per location, tracked/untracked status
- **Use when:** Stock-out alerts, inventory-based bidding decisions
- **Example:** `shopify_inventory(inventory_item_ids="111,222,333")`

---

## 2. Klaviyo Email Platform Tools

**Purpose:** Email marketing data, segments, campaigns, automation

**Account ID:** SNdxLL (4371218771)

### Account & List Tools

#### `klaviyo_account`
- **What:** Get Klaviyo account info (name, plan, timezone, email)
- **Returns:** Account metadata
- **Use when:** Validating Klaviyo connection
- **Example:** `klaviyo_account()` → Account details

#### `klaviyo_lists`
- **What:** List all email lists
- **Returns:** List IDs, names, subscriber counts, created dates
- **Use when:** Identifying audience segments, building integrations
- **Example:** `klaviyo_lists()` → All lists with subscriber counts

#### `klaviyo_list_profiles`
- **What:** Get subscriber profiles from specific list
- **Parameters:** list_id, limit
- **Returns:** Subscriber emails, names, custom properties
- **Use when:** Audience export, customer match setup
- **Example:** `klaviyo_list_profiles(list_id="subscribers", limit=1000)`

### Segments & Audiences

#### `klaviyo_segments`
- **What:** List all saved segments
- **Returns:** Segment IDs, names, criteria, member counts
- **Use when:** Understanding audience structure, customer matching
- **Example:** `klaviyo_segments()` → All active segments

### Campaign Tools

#### `klaviyo_campaigns`
- **What:** List email campaigns with performance data
- **Parameters:** filter (campaign status), limit
- **Returns:** Campaign IDs, names, performance metrics (open rate, click rate, revenue)
- **Use when:** Email performance analysis, correlation with ad campaigns
- **Example:** `klaviyo_campaigns(filter='equals(status,"sent")', limit=50)`

#### `klaviyo_campaign_detail`
- **What:** Get full campaign details and statistics
- **Parameters:** campaign_id
- **Returns:** Campaign metadata + detailed performance metrics
- **Use when:** Detailed campaign analysis, audience size validation
- **Example:** `klaviyo_campaign_detail(campaign_id="abc123")`

### Automation Tools

#### `klaviyo_flows`
- **What:** List automation flows
- **Returns:** Flow IDs, names, trigger types, statuses
- **Use when:** Understanding automation triggers, post-purchase sequences
- **Example:** `klaviyo_flows()` → All active automations

#### `klaviyo_flow_detail`
- **What:** Get flow structure with all actions
- **Parameters:** flow_id
- **Returns:** Flow trigger + actions + performance data
- **Use when:** Understanding customer journey, email follow-up sequences
- **Example:** `klaviyo_flow_detail(flow_id="post_purchase")`

### Profile & Event Tools

#### `klaviyo_profiles`
- **What:** Search customer profiles
- **Parameters:** email (search by email), limit
- **Returns:** Customer profile data + attributes
- **Use when:** Customer lookup, audience matching
- **Example:** `klaviyo_profiles(email="henk@pond.nl")`

#### `klaviyo_profile`
- **What:** Get full customer profile
- **Parameters:** profile_id
- **Returns:** Profile data + email history + custom attributes
- **Use when:** Customer deep-dive, lifetime value analysis
- **Example:** `klaviyo_profile(profile_id="cust123")`

#### `klaviyo_metrics`
- **What:** List all tracked metrics (events)
- **Returns:** Metric IDs, names, descriptions
- **Use when:** Understanding event tracking setup
- **Example:** `klaviyo_metrics()` → All tracked events (purchase, email_open, etc.)

#### `klaviyo_events`
- **What:** Get recent events for customer or metric
- **Parameters:** metric_id (filter by event type), profile_id (filter by customer), limit
- **Returns:** Event list with timestamps and data
- **Use when:** Customer journey analysis, event correlation
- **Example:** `klaviyo_events(metric_id="purchase", limit=100)`

#### `klaviyo_templates`
- **What:** List email templates
- **Returns:** Template IDs, names, creation dates
- **Use when:** Email content planning, template reuse
- **Example:** `klaviyo_templates()`

---

## 3. Google Analytics 4 (GA4) Tools

**Purpose:** Conversion tracking, user intent analysis, revenue reporting

**Property ID:** 478336344 | **Measurement ID:** G-9HQRM66093

### Reporting Tools

#### `ga4_report`
- **What:** Generate custom reports with any metrics/dimensions
- **Parameters:** dimensions (date, deviceCategory, country, pagePath, sessionSource), metrics (sessions, totalUsers, conversions, purchaseRevenue), start_date, end_date, filters, limit
- **Returns:** Custom data table with requested dimensions and metrics
- **Use when:** Custom analysis (ROAS by device, conversions by landing page, etc.)
- **Example:** `ga4_report(dimensions=["date", "sessionSource"], metrics=["sessions", "totalUsers", "conversions"], start_date="2026-03-01", end_date="2026-03-15")`

#### `ga4_realtime`
- **What:** Get real-time active users and events
- **Parameters:** dimensions (country, deviceCategory, unifiedScreenName), metrics (activeUsers)
- **Returns:** Real-time user counts and traffic breakdown
- **Use when:** Live monitoring (campaign launch verification, anomaly detection)
- **Example:** `ga4_realtime()` → Active users right now

#### `ga4_top_pages`
- **What:** Get top landing/exit pages by views or sessions
- **Parameters:** start_date, end_date, limit
- **Returns:** Page paths ranked by views with session counts
- **Use when:** Landing page performance, funnel identification
- **Example:** `ga4_top_pages(start_date="2026-03-01", limit=25)`

#### `ga4_ecommerce`
- **What:** E-commerce revenue data (transactions, AOV, product performance)
- **Parameters:** dimension (date, itemName, itemCategory, transactionId, sessionSource), start_date, end_date, limit
- **Returns:** Revenue, transaction count, AOV, product-level data
- **Use when:** Revenue tracking, budget calculations, ROAS analysis
- **Example:** `ga4_ecommerce(dimension="date", start_date="2026-03-08", end_date="2026-03-15", limit=30)` → Daily revenue (7 days)

---

## 4. Google Search Console (GSC) Tools

**Purpose:** Search performance, keyword analysis, CTR tracking

**Domain:** sc-domain:vijvercentrum.nl

### Performance Tools

#### `gsc_performance`
- **What:** Get search performance data (clicks, impressions, CTR, position)
- **Parameters:** dimensions (query, page, country, device, date), start_date, end_date, query_filter, page_filter, row_limit
- **Returns:** Performance metrics table with top queries/pages/devices
- **Use when:** Keyword research, landing page optimization, device targeting
- **Example:** `gsc_performance(dimensions=["query"], start_date="2026-03-01", end_date="2026-03-15", row_limit=50)` → Top 50 search queries

### Index Status Tools

#### `gsc_index_status`
- **What:** Check if specific URL is indexed
- **Parameters:** inspection_url (full URL to check)
- **Returns:** Indexation status (indexed, excluded, pending), coverage issues
- **Use when:** Verifying landing page indexation before campaign launch
- **Example:** `gsc_index_status(inspection_url="https://vijvercentrum.nl/products/koivoer")`

#### `gsc_sitemaps`
- **What:** Get sitemap status (indexed pages, issues)
- **Returns:** Sitemap list with coverage, submission date, errors
- **Use when:** Overall site health check, new category page indexation
- **Example:** `gsc_sitemaps()`

---

## 5. Google Ads (GADS) Tools

**Purpose:** Campaign & keyword performance data (read-only)

**Account ID:** 471-168-2842

### Campaign Tools

#### `gads_campaigns`
- **What:** List campaigns with performance data (impressions, clicks, conversions, cost)
- **Parameters:** status (ENABLED, PAUSED, REMOVED, ALL), start_date, end_date
- **Returns:** Campaign list with metrics
- **Use when:** Campaign overview, performance comparison
- **Example:** `gads_campaigns(status="ALL", start_date="2026-03-15", end_date="2026-03-15")` → Today's campaign performance

### Keyword Tools

#### `gads_keywords`
- **What:** Get keyword performance (impressions, clicks, conversions, CPC, CTR)
- **Parameters:** campaign_name (filter), start_date, end_date, limit
- **Returns:** Keyword list ranked by performance
- **Use when:** Keyword optimization, low-ROAS identification, QS analysis
- **Example:** `gads_keywords(start_date="2026-03-01", end_date="2026-03-15", limit=100)` → Top/bottom 100 keywords

---

## 6. Google Merchant Center (GMC) Tools

**Purpose:** Product feed management, Shopping campaign support

**Account ID:** 5743476888

### Product Tools

#### `gmc_products`
- **What:** Get product feed (250 items) with status
- **Parameters:** limit
- **Returns:** Product IDs, titles, prices, status (approved, disapproved, pending)
- **Use when:** Feed validation, product status checks
- **Example:** `gmc_products(limit=50)` → First 50 products

#### `gmc_status`
- **What:** Account and product feed status (approvals, warnings, issues)
- **Returns:** Feed summary (total products, approved, disapproved, pending, errors)
- **Use when:** Feed health check, issue identification
- **Example:** `gmc_status()` → Feed approval summary

---

## 7. Picqer Inventory Tools

**Purpose:** Stock levels, fulfillment, order management

**Environments:** retailz (commercial), cenfil (fulfillment)

### Product Tools

#### `picqer_products`
- **What:** Search products by name, SKU, or barcode
- **Parameters:** search, productcode, status (active/inactive), env, limit
- **Returns:** Product list with IDs, SKUs, prices, stock
- **Use when:** Product lookup, SKU verification
- **Example:** `picqer_products(search="koivoer", env="retailz", limit=20)`

#### `picqer_product`
- **What:** Get full product details from Picqer
- **Parameters:** product_id, env
- **Returns:** Product data (SKU, price, suppliers, stock locations)
- **Use when:** Product verification before campaign launch
- **Example:** `picqer_product(product_id="123", env="retailz")`

### Stock Tools

#### `picqer_stock`
- **What:** Get current stock levels for product
- **Parameters:** product_id, warehouse_id (optional), env
- **Returns:** Stock levels per warehouse, total free stock
- **Use when:** Stock-out alerts, inventory-based bidding
- **Example:** `picqer_stock(product_id="123", env="retailz")` → Current stock

#### `picqer_warehouse_stock`
- **What:** Get all stock in specific warehouse
- **Parameters:** warehouse_id, env
- **Returns:** All products + quantities in warehouse
- **Use when:** Warehouse capacity checks, stock distribution analysis
- **Example:** `picqer_warehouse_stock(warehouse_id="amsterdam", env="retailz")`

#### `picqer_stock_change`
- **What:** Record stock adjustment (mutation)
- **Parameters:** product_id, warehouse_id, change (amount), reason, env
- **Returns:** Updated stock level
- **Use when:** Stock corrections, inventory management (rare in ad context)

### Order Tools

#### `picqer_orders`
- **What:** List orders by status
- **Parameters:** status (open/processing/completed/cancelled), search, limit, env
- **Returns:** Order list with IDs, dates, customers, totals
- **Use when:** Order tracking, fulfillment monitoring
- **Example:** `picqer_orders(status="open", env="cenfil", limit=20)` → Pending fulfillment

#### `picqer_order`
- **What:** Get full order details
- **Parameters:** order_id, env
- **Returns:** Order data + items + shipping + status
- **Use when:** Order verification, fulfillment tracking
- **Example:** `picqer_order(order_id="PO123", env="cenfil")`

### Customer Tools

#### `picqer_customers`
- **What:** Search customers
- **Parameters:** search (name/email), limit, env
- **Returns:** Customer list with IDs, emails, order counts
- **Use when:** Customer lookup, audience matching
- **Example:** `picqer_customers(search="henk", env="retailz", limit=20)`

#### `picqer_customer`
- **What:** Get full customer profile
- **Parameters:** customer_id, env
- **Returns:** Customer data + addresses + order history
- **Use when:** Customer deep-dive, repeat purchase analysis
- **Example:** `picqer_customer(customer_id="cust456", env="retailz")`

### Warehouse & Supplier Tools

#### `picqer_warehouses`
- **What:** List warehouses
- **Parameters:** env
- **Returns:** Warehouse list with IDs, names, locations
- **Use when:** Multi-warehouse inventory management
- **Example:** `picqer_warehouses(env="retailz")`

#### `picqer_suppliers`
- **What:** List suppliers/vendors
- **Parameters:** env
- **Returns:** Supplier list with IDs, names, contact info
- **Use when:** Supplier analysis, budget allocation
- **Example:** `picqer_suppliers(env="retailz")`

---

## 8. Search & Indexing Tools

**Purpose:** Full-text search across documentation and code

### Search Tools

#### `search`
- **What:** Full-text search of all Retailz docs + code + config
- **Parameters:** query, type (doc/code/config/all), limit
- **Returns:** Matching documents with snippets
- **Use when:** Finding documentation, config examples, code patterns
- **Example:** `search(query="picqer bridge", type="all", limit=10)`

#### `semantic_search`
- **What:** Meaning-based search (finds related content even if exact words don't match)
- **Parameters:** query (natural language), type, limit
- **Returns:** Semantically related documents
- **Use when:** Exploring concepts, finding related documentation
- **Example:** `semantic_search(query="how do I integrate shopify with google ads", type="docs", limit=5)`

---

## 9. Chrome Automation Tools

**Purpose:** Google Ads UI interaction when API blocked

### Browser Control

#### `mcp__Claude_in_Chrome__computer`
- **What:** Click, type, scroll, screenshot in browser
- **Supports:** left_click, right_click, type, screenshot, scroll, navigate, wait
- **Use when:** Google Ads UI changes (bid updates, budget edits, campaign activation)
- **Example:** Click to activate campaign, update budget amount

#### `mcp__Claude_in_Chrome__read_page`
- **What:** Read page DOM, find elements
- **Use when:** Verifying page state, reading current campaign settings
- **Example:** Check if campaign is "Enabled" or "Paused"

#### `mcp__Claude_in_Chrome__find`
- **What:** Find elements by text or description
- **Use when:** Locating buttons, links, form fields
- **Example:** Find "Enable campaign" button

#### `mcp__Claude_in_Chrome__form_input`
- **What:** Set values in form fields
- **Use when:** Updating campaign budget, bid strategy
- **Example:** Set campaign budget to €25

#### `mcp__Claude_in_Chrome__javascript_tool`
- **What:** Execute JavaScript on page
- **Use when:** Advanced page interactions, data extraction
- **Example:** Extract all campaign IDs from page

---

## 10. Gmail Tools

**Purpose:** Email communication

### Email Operations

#### `gmail_search_messages`
- **What:** Search emails by sender, subject, date, etc.
- **Returns:** Email list with IDs, subjects, senders, snippets
- **Use when:** Finding campaign confirmations, stakeholder emails
- **Example:** `gmail_search_messages(q="google ads campaign")` → Find ads-related emails

#### `gmail_read_message`
- **What:** Read full email content
- **Returns:** Full email including headers, body, attachments
- **Use when:** Reading detailed email communications
- **Example:** `gmail_read_message(messageId="123")`

#### `gmail_create_draft`
- **What:** Create draft email (doesn't send)
- **Use when:** Drafting stakeholder updates, campaign reports
- **Example:** `gmail_create_draft(to="kees@vijvercentrum.nl", subject="Campaign Report", body="Week 1 summary...")`

---

## Tool Usage Decision Matrix

| Scenario | Tool Category | Specific Tool |
|---|---|---|
| Revenue tracking for budget | GA4 | `ga4_ecommerce` |
| Check if conversion target met | GA4 | `ga4_report` |
| Find underperforming keywords | GADS | `gads_keywords` |
| Search analysis & opportunities | GSC | `gsc_performance` |
| Product verification | Shopify | `shopify_products` |
| Order analysis | Shopify | `shopify_orders` |
| Customer matching (email) | Klaviyo | `klaviyo_profiles` |
| Email campaign analysis | Klaviyo | `klaviyo_campaigns` |
| Stock check | Picqer | `picqer_stock` |
| Google Ads UI interaction | Chrome | `mcp__Claude_in_Chrome__computer` |
| Documentation lookup | Search | `semantic_search` |

---

## Connection Status Summary

| System | API Access | Status | Notes |
|---|---|---|---|
| GA4 | ✅ Full | Active | Real-time data available |
| GSC | ✅ Full | Active | 12h delay typical |
| GMC | ✅ Limited | Read-only | Cannot modify feed via API |
| GADS | ✅ Limited | Read-only | Use Chrome for UI changes |
| Shopify | ✅ Full | Active | All operations available |
| Klaviyo | ✅ Full | Active | All operations available |
| Picqer | ✅ Full | Active | retailz & cenfil environments |
| Chrome | ✅ Full | Active | UI automation available |
| Gmail | ✅ Limited | Read & compose | Full access restricted |

---

**Last updated:** 15 March 2026 | **Version:** 1.0
