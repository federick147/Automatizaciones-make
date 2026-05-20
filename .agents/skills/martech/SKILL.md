---
name: martech
description: When the user wants to evaluate, build, or optimize their marketing technology stack. Also use when the user asks about "martech stack," "marketing tools," "CRM," "marketing automation," "customer data platform," "CDP," "data enrichment," "lead routing," "attribution modeling," "multi-touch attribution," "marketing ops," "marketing operations," "tech stack audit," "tool consolidation," "HubSpot," "Salesforce," "Marketo," "Segment," "Klaviyo," "Intercom," "Customer.io," "marketing infrastructure," "data pipeline," "identity resolution," or "integration between marketing tools." For revenue operations and CRM processes, see revops. For analytics tracking implementation, see analytics.
metadata:
  version: 1.0.0
---

# Marketing Technology (Martech)

You are an expert in marketing technology strategy and operations. Your goal is to help design, audit, and optimize a martech stack that enables data-driven marketing at scale — without unnecessary complexity or cost.

## Before Starting

**Check for product marketing context first:**
If `.agents/product-marketing.md` exists (or `.claude/product-marketing.md`), read it before asking questions.

Gather this context (ask if not provided):

### 1. Company Context
- Business model (B2B / B2C / marketplace)
- Team size (marketing and engineering)
- Stage (startup, growth, enterprise)
- Current tools in use

### 2. Problem to Solve
- What is broken or missing?
- What decision or workflow is blocked?
- What data is unavailable that should be?

### 3. Technical Constraints
- Engineering bandwidth available for integrations?
- Existing systems that must be preserved (CRM, ERP)?
- Budget range?
- Data privacy / compliance requirements (GDPR, HIPAA)?

---

## Martech Stack Layers

A well-designed martech stack has five layers. Start by mapping what exists at each layer:

```
┌─────────────────────────────────────────────────┐
│ 5. ACTIVATION (ads, email, in-app, push, SMS)   │
├─────────────────────────────────────────────────┤
│ 4. ORCHESTRATION (automation, CRM, nurture)     │
├─────────────────────────────────────────────────┤
│ 3. DATA HUB (CDP, data warehouse, identity)     │
├─────────────────────────────────────────────────┤
│ 2. COLLECTION (analytics, tracking, forms)      │
├─────────────────────────────────────────────────┤
│ 1. FOUNDATION (website/app, tag manager, CMP)   │
└─────────────────────────────────────────────────┘
```

Build from bottom to top. A broken foundation makes every layer above unreliable.

---

## Layer 1: Foundation

| Tool Category | Purpose | Common Tools |
|--------------|---------|-------------|
| Tag Manager | Deploy and manage marketing scripts without code deploys | Google Tag Manager, Tealium |
| Consent Management | Comply with GDPR/CCPA, manage cookie consent | Cookiebot, OneTrust, Axeptio |
| Identity / Auth | Identify users consistently across sessions | Auth0, Clerk |

**Checklist:**
- [ ] Tag manager deployed on all pages (not hardcoded scripts)
- [ ] Consent management active with proper consent mode
- [ ] User ID passed consistently through all tools

---

## Layer 2: Data Collection

| Tool Category | Purpose | Common Tools |
|--------------|---------|-------------|
| Web Analytics | Traffic, behavior, conversions | GA4, Plausible, Heap |
| Product Analytics | In-product usage events | Mixpanel, Amplitude, PostHog |
| Session Recording | Qualitative behavior | Hotjar, FullStory, Microsoft Clarity |
| Form / Survey | Lead capture, voice of customer | Typeform, HubSpot Forms, Survicate |

**Key principle:** Every event should have a business question it answers. See the **analytics** skill for implementation.

**Common mistakes:**
- Tracking everything → analysis paralysis and storage cost
- Inconsistent naming conventions → broken reports
- No PII hygiene → compliance risk

---

## Layer 3: Data Hub

This is the most commonly missing or underbuilt layer in early-stage stacks.

### Customer Data Platform (CDP)

A CDP unifies customer data from all sources into a single customer profile.

| CDP Type | Best For | Examples |
|----------|---------|---------|
| Streaming CDP | Real-time activation, event routing | Segment, RudderStack |
| Warehouse-native CDP | SQL-first teams, existing data warehouse | Census, Hightouch, Datagrain |
| All-in-one CDP | SMBs wanting less infrastructure | Ortto, Bloomreach |

**When you need a CDP:**
- Data lives in 3+ tools with no shared customer ID
- You want to personalize campaigns but can't connect product usage to email
- Marketing team can't access customer data without engineering

**When you don't need a CDP yet:**
- < 50k customers
- Single acquisition channel
- Engineering can build point-to-point integrations cheaply

### Data Warehouse

| Tool | Best For |
|------|---------|
| BigQuery | GCP ecosystem, high query volume |
| Snowflake | Enterprise, multi-cloud |
| Redshift | AWS ecosystem |
| ClickHouse | High-performance event analytics |
| DuckDB | Local/serverless analytics |

### Identity Resolution

Matching the same person across anonymous sessions, devices, and login states.

- **Deterministic matching**: email, phone, user ID — high confidence
- **Probabilistic matching**: IP, browser fingerprint, behavior — lower confidence
- **Best practice**: Assign an anonymous ID at first visit, merge to user ID at signup

---

## Layer 4: Orchestration

### CRM

| CRM | Best For |
|-----|---------|
| HubSpot | SMB/mid-market B2B, all-in-one |
| Salesforce | Enterprise B2B, complex sales |
| Pipedrive | SMB sales-led |
| Attio | Modern, data-model-first |
| Close | High-velocity outbound |

**CRM data quality checklist:**
- [ ] Standard lifecycle stages defined (Subscriber → Lead → MQL → SQL → Opportunity → Customer)
- [ ] Lead source field populated consistently
- [ ] Duplicate management rules active
- [ ] Field mapping documented
- [ ] Data enrichment running (Clearbit, Apollo, Clay)

### Marketing Automation

| Tool | Best For |
|------|---------|
| HubSpot | B2B nurture, forms, landing pages |
| Marketo | Enterprise B2B demand gen |
| Klaviyo | E-commerce email + SMS |
| Customer.io | Product-triggered behavioral email |
| Intercom | In-app messaging + support |
| Braze | Mobile-first, multi-channel |
| ActiveCampaign | SMB all-in-one |

**Choosing automation tools:**

| Trigger Type | Right Tool |
|-------------|-----------|
| Time-based (3 days after signup) | Any ESP |
| Behavior-based (completed action X) | Customer.io, Braze, Klaviyo |
| Score-based (MQL threshold reached) | HubSpot, Marketo |
| Purchase/transaction-based | Klaviyo, Braze |

---

## Layer 5: Activation

| Channel | Tools |
|---------|-------|
| Email | Klaviyo, Customer.io, Postmark (transactional) |
| Paid Ads | Google Ads, Meta Ads Manager, LinkedIn Campaign Manager |
| In-app messaging | Intercom, Pendo, Appcues |
| Push notifications | OneSignal, Braze |
| SMS | Klaviyo, Attentive, Twilio |
| Direct mail | Lob, Sendoso |
| Retargeting | AdRoll, Criteo, Meta Custom Audiences |

---

## Attribution Modeling

Attribution answers: which marketing touchpoints drove conversion?

### Attribution Models

| Model | How It Works | Best For |
|-------|-------------|---------|
| Last touch | 100% credit to last touchpoint | Simple measurement, short sales cycles |
| First touch | 100% credit to first touchpoint | Awareness/acquisition measurement |
| Linear | Equal credit to all touchpoints | Understanding full journey |
| Time decay | More credit to recent touchpoints | Long B2B sales cycles |
| Data-driven | ML-weighted based on actual conversion patterns | High-volume, GA4 |
| W-shaped | 30% first, 30% last, 40% mid | B2B demand gen |

### Attribution Stack

| Layer | Tool |
|-------|------|
| Web click attribution | UTM parameters + GA4 |
| Ad platform attribution | Google Ads / Meta native attribution |
| Multi-touch (self-serve) | Triple Whale, Northbeam (e-com) |
| Multi-touch (B2B) | Rockerbox, Attribution, HubSpot attribution |
| Incrementality testing | Geo holdout tests, Meta Conversion Lift |

**Important:** No attribution model is perfect. Use multiple models and triangulate.

---

## Data Enrichment

Automatically append firmographic or contact data to leads.

| Tool | Best For | Data Type |
|------|---------|----------|
| Clearbit | B2B firmographics, company data | Company size, industry, tech stack |
| Apollo.io | B2B contact + company | Email, phone, LinkedIn |
| Clay | Flexible enrichment, waterfall | Multi-source enrichment |
| ZoomInfo | Enterprise B2B data | Contact + intent data |
| Lusha | SMB contact data | Email, phone |

**Enrichment workflow:**
1. New lead enters CRM
2. Enrichment tool matches on email/domain
3. Firmographic data appended (company, size, industry, role)
4. Lead scoring rules re-evaluate
5. Routing or segmentation updates automatically

---

## Stack Audit Framework

When auditing an existing martech stack:

### Step 1: Inventory
List all tools with:
- Annual cost
- Number of actual users
- Primary use case
- Data inputs / outputs
- Owner (who manages it)

### Step 2: Score Each Tool

| Criterion | Question |
|-----------|---------|
| Usage | Is it used daily/weekly? |
| Unique value | Does another tool already do this? |
| Integration | Does it connect cleanly to the rest of the stack? |
| ROI | Can you measure what it contributes? |

### Step 3: Identify Consolidation Opportunities

Common waste patterns:
- Two tools doing the same job (two ESPs, two CDPs)
- Tool purchased but never fully implemented
- Point-to-point integrations that a CDP would replace
- Enterprise license for a startup-stage team

### Step 4: Prioritize Gaps

Missing capabilities that block marketing:
- No behavioral email (sending time-based only)
- No attribution (no UTM discipline)
- No data enrichment (blank fields in CRM)
- No consent management (GDPR risk)

---

## Output Format

### Stack Map

```markdown
# Martech Stack: [Company Name]

## Current Stack

| Layer | Tool | Cost/yr | Status |
|-------|------|---------|--------|
| Foundation | GTM | Free | ✅ Active |
| Collection | GA4 | Free | ✅ Active |
| Collection | Mixpanel | $X | ⚠️ Underused |
| Orchestration | HubSpot | $X | ✅ Active |
| Activation | Klaviyo | $X | ✅ Active |

## Gaps
- [ ] No CDP — customer data siloed between Mixpanel and HubSpot
- [ ] No attribution model — UTMs inconsistent

## Recommendations
1. [Action] — [rationale] — [priority: high/medium/low]
```

---

## References

- **[references/stack-map.md](references/stack-map.md)** — Stack templates by company stage
- **[references/attribution-models.md](references/attribution-models.md)** — Attribution model comparison and selection guide
- **[references/integration-patterns.md](references/integration-patterns.md)** — Common tool integration patterns and data flows

---

## Related Skills

- **analytics**: For tracking implementation within the martech stack
- **revops**: For CRM process design, lead routing, and pipeline operations
- **emails**: For email marketing strategy and execution
- **growth-marketing**: For connecting martech to growth loops and experiments
- **ab-testing**: For experimentation tooling and measurement
