# Should-I Marketing Website & SEO Master Spec (v1.1)

Should-I’s website is designed as a trust-first conversion router for a high-stakes B2B decision product. Most visitors arrive anxious about making an expensive mistake, so the site must earn confidence quickly, explain the offer plainly, and move qualified users into GoHighLevel funnels for capture and checkout. We’re choosing an Astro static marketing site because it produces fast, crawlable HTML that performs well in Google and AI search—without app-like complexity. Visually, we’re using a neutral editorial design with a single teal accent to signal calm authority, reduce noise, and make the report outputs feel more valuable by contrast.

**Status:** Authoritative source of truth  
**Applies to:** www.should-i.ai (marketing), go.should-i.ai (funnels), app.should-i.ai (product)  
**Audience:** Product, engineering, marketing (primary handoff: Bintang)

---
## 1. Purpose & First Principles

Should‑I helps business owners make **high‑stakes decisions** (expand, acquire, hold, exit) with clarity.

The marketing website exists to:
- Establish **trust fast**
- Demonstrate **decision intelligence**, not “AI magic”
- Route qualified users into **GoHighLevel funnels**
- Support **SEO and AI‑driven discovery**

**What this site is NOT:**
- Not the product app
- Not a dashboard
- Not a content farm
- Not a generic SaaS landing page

**Core principle:**  
> Calm authority + visceral relevance beats cleverness.

---

## 2. Architecture Overview

### Domains & Responsibilities

| Domain | Role | Notes |
|------|-----|------|
| **www.should-i.ai** | Marketing, SEO, trust | Indexable |
| **go.should-i.ai** | Funnels, forms, checkout | Generally NOINDEX |
| **app.should-i.ai** | Product delivery | Auth only |

### Conversion philosophy
- www = convince and qualify  
- go = convert  
- app = deliver  

No funnel logic should leak into the marketing site.

---

## 3. Technology & Build Decisions

### Frontend Framework
**Astro (Static Site Generation)**

Rationale:
- Outputs clean HTML/CSS with minimal JS
- Excellent for SEO + AI crawlers
- Lower complexity than app-style frameworks

### Hosting & Deployment (Static-first)
Default: **Static deployment** (Astro SSG output)

**Why static-first:** Astro’s SSG output is just HTML/CSS/minimal JS. Static hosts (Netlify/Vercel/DO static) are optimised for:
- faster deploys (no container build/push)
- edge caching/CDN by default
- simpler rollback
- fewer failure modes

**Docker guidance (important):**
- **Do NOT create a new Dockerfile for the marketing site in v1** if it’s static-only.
- Docker adds build/push overhead and operational surface area without delivering SEO or conversion benefits for a static site.
- Use Docker only if/when you introduce **SSR**, server middleware, or unified reverse-proxy requirements later.

Strong candidates for v1 hosting:
- **Netlify** (static site + simple deploy)
- **Vercel** (static site + fast preview deploys)
- **DigitalOcean App Platform** in **static mode** (works fine if you want to stay inside DO)

Decision rule:
> If it can be deployed as static HTML, do not add Docker complexity.

### Repo Strategy
- Preferred: separate marketing repo
- Acceptable: monorepo `/marketing` package with independent deploy

## 4. Sitemap (Authoritative)

### Indexable marketing pages (www)

/
├── industries  
│   ├── laundromats  
│   └── dentists  
├── how-it-works  
├── example-report  
├── pricing  
├── about  
├── contact  
├── privacy  
└── terms  

### Funnels (go) – conversion only
- /health-check  
- /report-checkout  
- /thank-you  

### App (app)
- Authenticated product

---

## 5. URL & Routing Rules

- Lowercase only
- Hyphen-separated
- Stable, literal slugs
- Canonical host: **www.should-i.ai**
- Industry pages must follow:
  - `/industries/{industry}` (plural where sensible)

v1 industries:
- /industries/laundromats
- /industries/dentists

---

## 6. SEO Rules of Engagement

### Indexation
- www pages: indexable
- go pages: noindex or not submitted
- One canonical hostname enforced

### Sitemaps
- sitemap.xml for www only
- Submit via Google Search Console

### Structured Data
- Organization + WebSite (homepage)
- BreadcrumbList (industry pages)
- FAQPage (only if FAQs are genuinely custom)

### Acceptance Gate
The **SEO Acceptance Checklist** must be fully passed before launch.
(No exceptions.)

---

## 7. Homepage Narrative (Critical)

The homepage lives or dies on the **first screen**.

### Required visceral hook
The copy must immediately trigger:
> “Am I about to waste $50k on the wrong decision?”

No warm‑up.
No generic AI framing.

Hero copy must:
- Name the risk
- Imply financial consequence
- Promise clarity

---

## 8. Industry Pages (Non‑Templated by Rule)

Industry pages are the **SEO and trust engine**.

Rules:
- Each industry must have **unique problem framing**
- FAQs must be **custom‑written**
- No placeholder or templated questions

If an industry cannot be differentiated meaningfully, do not launch it yet.

---

## 9. Example Report Page (Conversion Asset)

This page must **convert**, not just educate.

Rules:
- Do NOT dump screenshots
- Show **one killer insight per section**
- Include a real, visible data point

Gate full report access behind email capture (GHL).

---

## 10. Design System (Summary)

### Visual philosophy
- Neutral editorial base
- One accent colour (deep teal)
- No dark mode
- No gradients

### Typography
- Inter only (v1)
- Clear hierarchy

### CTAs
- One primary CTA per section
- Secondary CTAs never compete

---

## 11. Tooling & Ownership Boundaries

## 11A. GoHighLevel Funnel Integration (Implementation Rules)

Goal: Use www for trust/SEO and **route intent into GHL** for capture + checkout with clean tracking.

### Routing rules
- Use **redirect CTAs** from www → go (no iframes).
- Primary CTA:
  - `https://go.should-i.ai/health-check`
- Industry prefill (must match GHL internal enum):
  - `https://go.should-i.ai/health-check?industry=laundromat`
  - `https://go.should-i.ai/health-check?industry=dentist`
- Paid checkout CTA:
  - `https://go.should-i.ai/report-checkout`

### Tracking rules (UTM passthrough)
- Preserve UTMs from ads → www → go.
- Standard keys:
  - `utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `utm_term`
- Implementation approach:
  - If a user lands on www with UTMs, **append them to outbound CTA links to go** (querystring passthrough).

### Script placement
- Keep tracking scripts **light** on www to protect performance.
- If you must use GHL tracking scripts, place them in a single, consistent location:
  - in the BaseLayout `<head>` or just before `</body>`
- Avoid multiple competing trackers that slow the site.

### Indexation rules
- Funnels on `go.should-i.ai` are conversion-only and should be **NOINDEX** (or not submitted) by default.
- Do not duplicate long-form marketing content on go pages.

### Ownership boundary
- GHL owns: forms, funnel logic, email capture, checkout, CRM automation.
- www owns: messaging, SEO, trust, routing, example proof assets.

### GoHighLevel
Owns:
- Forms
- Funnels
- Checkout
- Email capture

### Marketing Site
Owns:
- Trust
- SEO
- Education
- Routing

### App
Owns:
- Product experience

---

## 12. Appendices

- Authoritative Sitemap
- Visual Sitemap Diagram
- Astro Technical Brief
- SEO Acceptance Checklist
- URL Naming Conventions
- Mini Design System
- Astro Marketing Stub

---

## 13. Final Rule

If a decision:
- adds complexity without clarity
- adds pages without intent
- adds tech without leverage

**Do not ship it.**
