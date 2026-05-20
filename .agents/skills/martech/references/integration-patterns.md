# Common Martech Integration Patterns and Data Flows

## Pattern 1: Web → CRM (Lead Capture)

```
Website form submission
  → GTM fires form_submitted event
    → GA4 records conversion
    → HubSpot form / API receives contact data
      → Enrichment tool appends firmographics
        → Lead score calculated
          → Routing rule assigns to rep
```

**Tools involved:** GTM, GA4, HubSpot, Clearbit/Apollo
**Key data:** Email, UTM source/medium/campaign, firmographic fields

---

## Pattern 2: Product → Email (Behavioral Triggers)

```
User completes action in product
  → Product fires event (e.g., feature_used)
    → CDP (Segment) receives event
      → CDP routes to email tool (Customer.io / Klaviyo)
        → Email tool triggers campaign based on event
```

**Tools involved:** Product backend / frontend, Segment, Customer.io or Klaviyo
**Key data:** user_id, event name, event properties, timestamp

---

## Pattern 3: Product → CRM (PQL Routing)

```
User hits usage threshold in product (e.g., 5 exports in 7 days)
  → Analytics tool or CDP identifies PQL
    → Reverse ETL (Census/Hightouch) syncs PQL flag to CRM
      → CRM triggers sales task for rep
        → Rep reaches out with product context
```

**Tools involved:** Mixpanel/Amplitude, Snowflake/BigQuery, Census/Hightouch, Salesforce/HubSpot
**Key data:** user_id, company_id, usage metrics, PQL score

---

## Pattern 4: Ad Platform → CRM (Conversion Attribution)

```
User clicks ad (Google / Meta)
  → UTM parameters captured in CRM via form fill
    → Deal created in CRM
      → CRM sends conversion back to ad platform (offline conversion import)
        → Ad platform optimizes bids toward converted audiences
```

**Tools involved:** Google Ads / Meta Ads, HubSpot/Salesforce, UTM parameters
**Key data:** gclid/fbclid, UTM params, deal value, conversion timestamp

---

## Pattern 5: CRM → Ads (Audience Sync)

```
CRM segment defined (e.g., "Customers in healthcare industry")
  → Segment synced to ad platform via CDP or native integration
    → Ad platform creates custom audience
      → Lookalike audience generated
        → Campaign targets net-new prospects similar to best customers
```

**Tools involved:** HubSpot/Salesforce, Segment or native integration, Meta / Google / LinkedIn
**Key data:** Email list (hashed), firmographic filters

---

## Pattern 6: Data Warehouse → Marketing Tools (Reverse ETL)

```
Raw event data lands in Snowflake / BigQuery via Fivetran or Segment
  → SQL models compute aggregated user scores / segments
    → Census or Hightouch syncs computed data back to:
        - HubSpot (contact properties)
        - Customer.io (user attributes for triggers)
        - Meta (custom audiences)
```

**Tools involved:** Snowflake/BigQuery, Fivetran or Segment, Census/Hightouch, destination tools
**Use when:** Segments are too complex for CDP alone, require joins across multiple data sources

---

## Common Integration Anti-Patterns

| Anti-Pattern | Problem | Fix |
|-------------|---------|-----|
| Direct point-to-point integrations without a CDP | Data fragmentation, sync conflicts, multiple source-of-truth | Route events through a CDP first |
| CRM as the analytics database | CRM is transactional, not analytical; query performance degrades | Use data warehouse for analytics |
| Zapier for high-volume event routing | Zapier is not built for > 1k events/day; latency and cost spike | Use Segment or native webhooks |
| Syncing raw events to email tool | Email tools are not event databases; use them for triggers only | Filter/aggregate before sending |
| Not hashing PII before ad platform upload | Compliance risk (GDPR, CCPA) | Always hash email/phone before upload |
