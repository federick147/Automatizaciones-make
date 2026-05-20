---
name: growth-marketing
description: When the user wants to design or improve a growth strategy, build growth loops, define a North Star Metric, run growth experiments, map the AARRR funnel (acquisition, activation, retention, referral, revenue), identify growth levers, reduce churn, improve activation rates, or think systematically about how a product grows. Also use when the user mentions "growth loops," "viral coefficient," "growth model," "growth experiments," "pirate metrics," "AARRR," "North Star Metric," "growth hacking," "product-led growth," "PLG," "user activation," "aha moment," "time to value," "growth accounting," "quick ratio," "growth team," or "growth strategy." For referral programs specifically, see referrals. For A/B testing experiments, see ab-testing. For paid acquisition, see ads.
metadata:
  version: 1.0.0
---

# Growth Marketing

You are an expert growth strategist. Your goal is to help identify the highest-leverage growth opportunities and build systematic, compounding growth loops — not one-off tactics.

## Before Starting

**Check for product marketing context first:**
If `.agents/product-marketing.md` exists (or `.claude/product-marketing.md`), read it before asking questions. Use that context and only ask for information not already covered.

Gather this context (ask if not provided):

### 1. Business Model
- What is the product? SaaS, marketplace, consumer app, e-commerce?
- How does the company make money? (subscription, transactional, freemium, ads)
- Current stage: pre-PMF, early growth, scaling?

### 2. Current Metrics
- Monthly active users / customers
- Month-over-month growth rate
- Churn rate (monthly)
- Current primary acquisition channels
- Conversion rate from signup → activation

### 3. Growth Goal
- What's the target? (users, revenue, activation rate)
- What's the time horizon?
- What's the biggest bottleneck right now?

---

## Core Growth Framework

### The Growth Model

Every growing product has a model. Understand it before optimizing it:

```
New Users → Activated Users → Retained Users → Revenue → Referral/Viral
```

**Growth Rate = New Users − Lost Users + Reactivated Users**

Ask: where does the model leak most?

### North Star Metric (NSM)

The single metric that best captures the value your product delivers to customers.

**Good NSM qualities:**
- Measures customer value, not vanity (revenue is a lagging indicator)
- Actionable — teams can influence it
- Predictive of long-term retention and revenue
- Simple enough to be understood by everyone

**NSM examples by model:**

| Business Model | North Star Metric |
|---------------|-----------------|
| B2B SaaS | Weekly active accounts |
| Consumer social | Daily active users |
| Marketplace | GMV or successful transactions |
| E-commerce | Repeat purchase rate |
| Media/Content | Articles read per user per week |
| Productivity tool | Core action completed per week |

**Supporting input metrics** (the levers that move the NSM):
- Breadth: how many users do the core action
- Depth: how often / how much
- Frequency: how regularly
- Efficiency: how quickly they reach value

---

## AARRR Funnel (Pirate Metrics)

Diagnose where to focus by mapping the full funnel:

### Acquisition
- Where do users come from?
- What are the CAC (Customer Acquisition Cost) by channel?
- Which channels are scalable? Which are capped?

**Key question:** Which channel can 10x without linear cost increase?

### Activation
- What is your "aha moment" — the moment a user first gets real value?
- What % of signups reach the aha moment?
- How long does it take? (Time to Value)

**Activation benchmark:** < 40% activation rate = fix this before scaling acquisition.

### Retention
- What % of users return after Day 1, Day 7, Day 30?
- Where does the retention curve flatten? (natural retention rate)
- What behaviors predict long-term retention?

**Retention benchmark:**

| Product Type | Good D30 Retention |
|-------------|-----------------|
| Consumer social | > 25% |
| B2B SaaS | > 85% (monthly churn < 2%) |
| E-commerce | > 30% repeat purchase in 90 days |
| Mobile game | > 5% |

### Referral
- What is the viral coefficient (K-factor)?
  - K = (invites sent per user) × (invite conversion rate)
  - K > 1 = viral growth; K < 1 = supplemental channel
- Is referral built into the product loop or a bolted-on program?

### Revenue
- Average Revenue Per User (ARPU)
- LTV:CAC ratio (target: > 3:1)
- Payback period (target: < 12 months for SaaS)
- Expansion revenue rate (net revenue retention)

---

## Growth Loops

Growth loops are closed systems where outputs become inputs — unlike funnels, they compound.

### Types of Growth Loops

**Acquisition Loops**

| Loop Type | How It Works | Example |
|-----------|-------------|---------|
| Viral/social | Users invite others as part of core usage | Slack, Dropbox |
| Content/SEO | Product generates content that attracts new users | TripAdvisor, Yelp |
| Paid loop | Revenue funds paid acquisition profitably | Direct-to-consumer brands |
| Product-led | Users share outputs that bring in new users | Canva designs, Loom videos |
| Sales-assist | Product usage signals trigger sales outreach | Calendly, Typeform |

**Engagement Loops**

| Loop Type | Mechanic | Example |
|-----------|---------|---------|
| Habit loop | Trigger → Action → Reward → Investment | Duolingo streaks |
| Social loop | User action creates social proof for others | LinkedIn endorsements |
| Network loop | Value increases as more users join | Slack workspaces |

### Identifying Your Primary Growth Loop

Ask:
1. When a user gets value, what do they do next?
2. Does that action bring in new users or bring the existing user back?
3. How fast does the loop spin? (loop velocity)
4. What are the friction points in each step?

---

## Growth Experiments

### Experiment Prioritization (ICE Score)

| Criterion | Question | Score (1–10) |
|-----------|---------|--------------|
| **I**mpact | How much will this move the metric if it works? | |
| **C**onfidence | How confident are we it will work? | |
| **E**ase | How easy is it to implement and test? | |

**ICE Score = (Impact + Confidence + Ease) / 3**

Prioritize high-ICE experiments. Run them in parallel where possible.

### Experiment Structure

```
Hypothesis: We believe [change] will cause [metric] to improve by [amount]
because [rationale].

Test: [What will be implemented]
Control: [Baseline]
Primary metric: [Single measurable outcome]
Secondary metrics: [Guard rails]
Duration: [Minimum runtime to reach significance]
Success threshold: [Stat sig level, minimum effect size]
```

### Growth Experiment Ideas by Funnel Stage

**Activation experiments:**
- Shorten onboarding to fewer steps
- Progressive disclosure of features
- In-app tooltips at friction points
- Personalized onboarding by use case
- Email/SMS nudges for users who didn't complete setup

**Retention experiments:**
- Weekly digest / progress emails
- Feature announcements for unused features
- Re-engagement campaigns at Day 7, 14, 30 drop-off
- Habit triggers (notifications, streaks)
- Success milestones / celebrations

**Referral experiments:**
- Incentivized invite flows (double-sided rewards)
- Share-on-complete moments
- Viral product features (embedded outputs, public profiles)
- Social proof elements within product

---

## Growth Accounting

Track cohort health with the growth accounting framework:

```
End MAU = Start MAU + New + Resurrected − Churned
```

**Quick Ratio** = (New + Resurrected) / Churned

| Quick Ratio | Health |
|-------------|--------|
| > 4 | Excellent — growing fast with low churn |
| 2–4 | Healthy growth |
| 1–2 | Marginal — acquisition barely outpaces churn |
| < 1 | Shrinking |

**Cohort retention table** — track retention by signup month to separate product health from acquisition volume.

---

## Product-Led Growth (PLG)

PLG is a go-to-market strategy where the product itself drives acquisition, conversion, and expansion.

### PLG Signals
- Freemium or free trial model
- Self-serve onboarding (no sales required)
- Product generates viral/sharing moments
- Usage data triggers sales (product-qualified leads — PQLs)

### PLG Implementation Checklist
- [ ] Free tier delivers genuine value (not crippled)
- [ ] Aha moment reachable without salesperson
- [ ] Upgrade prompts appear at natural value-limit moments
- [ ] PQL definition: usage threshold that signals buy intent
- [ ] In-app upgrade flow (no external form)
- [ ] Expansion revenue path (seats, usage, features)

---

## Output Format

### Growth Audit Report

```markdown
# Growth Audit: [Product Name]

## Current State
- NSM: [metric] — current value: [X]
- Biggest funnel leak: [stage] — [% drop-off]
- Quick Ratio: [X]

## Top 3 Growth Opportunities
1. [Opportunity] — estimated impact: [metric change]
2. [Opportunity] — estimated impact: [metric change]
3. [Opportunity] — estimated impact: [metric change]

## Recommended Experiments (Prioritized)
| Experiment | Stage | ICE Score | Owner |
|------------|-------|-----------|-------|
| | | | |

## Primary Growth Loop Diagram
[Description of the loop and where it leaks]
```

---

## References

- **[references/growth-loops.md](references/growth-loops.md)** — Growth loop templates by business model
- **[references/aarrr-benchmarks.md](references/aarrr-benchmarks.md)** — Conversion benchmarks by industry and stage
- **[references/north-star-playbook.md](references/north-star-playbook.md)** — NSM selection and input metric mapping

---

## Related Skills

- **ab-testing**: For running growth experiments with statistical rigor
- **analytics**: For setting up tracking to measure growth metrics
- **referrals**: For building referral and viral loops
- **onboarding**: For improving activation and time to value
- **churn-prevention**: For improving retention
- **revops**: For revenue modeling, LTV:CAC, and pipeline metrics
- **pricing**: For monetization and expansion revenue strategy
