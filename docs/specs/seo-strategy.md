# Should-I SEO & LLM Discovery Strategy (v1)

## Why SEO + LLM Discovery Matters (for Bintang)

Traditional SEO helps people find Should‑I when they search Google.  
LLM discovery (ChatGPT, Perplexity, SearchGPT, Copilot, etc.) helps people *encounter* Should‑I when they ask high‑level questions like:

> “Should I open a laundromat in Melbourne?”  
> “Is buying a dental practice worth it?”

These systems favour **clear structure, fast pages, explicit meaning, and authoritative framing** — not gimmicks. The goal is not to “hack AI”, but to make the site **easy to understand, cite, and summarise**. Astro’s static HTML output gives us a strong foundation. What follows are the non‑negotiable optimisation rules.

---

## 1. Page Structure (Critical)

Every indexable page must have:
- One clear **H1** stating the decision context
- Logical **H2s** that answer real questions
- Short paragraphs (2–4 lines)
- Bullet lists where possible

Example:
- H1: “Should You Open a Laundromat in Melbourne?”
- H2: “Local Demand and Catchment Reality”
- H2: “Competitive Saturation Risks”

LLMs extract meaning from structure before prose.

---

## 2. Explicit Semantics (Do Not Assume Understanding)

State facts plainly. Avoid clever phrasing.

Bad:
> “We analyse opportunity signals.”

Good:
> “We analyse local demand, competition density, pricing pressure, and operating costs.”

LLMs rely on **explicit nouns**, not implication.

---

## 3. Structured Data (JSON‑LD)

Implement schema on www pages:
- Organization
- WebSite
- BreadcrumbList (industry pages)
- FAQPage (only if FAQs are genuinely custom)

This increases eligibility for:
- Google rich results
- AI citations and summaries

---

## 4. Internal Linking (Context Web)

- Homepage → industries
- Industries → example report
- Example report → health check

Avoid orphan pages.  
LLMs infer importance from **link density and consistency**.

---

## 5. Performance & Crawlability

- Static HTML (Astro SSG)
- No heavy JS frameworks
- Minimal third‑party scripts
- Clean URLs

Fast, simple sites are favoured by both Google and AI crawlers.

---

## 6. Content Signals LLMs Prefer

- Clear decision framing (“Should I…”, “Is it worth…”)
- Industry specificity
- Real data points (percentages, thresholds)
- Calm, authoritative tone (not hype)

Avoid:
- Marketing superlatives
- Generic AI language
- Empty thought leadership

---

## 7. What We Are NOT Doing (Intentionally)

- No AI‑generated filler content
- No mass blog spam
- No keyword stuffing
- No programmatic SEO pages (for now)

Authority > volume.

---

## 8. Success Signals

You’re doing this right if:
- Pages rank for long‑tail, intent‑driven queries
- People reference Should‑I when asking decision questions
- LLM answers paraphrase your framing accurately

This is slow, compounding leverage — not instant traffic.

---

## Final Rule

If a page would confuse a smart human skimming it,  
it will confuse an LLM even more.

Clarity wins.