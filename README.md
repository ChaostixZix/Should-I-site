# ShouldI Marketing Site Documentation

Documentation for the ShouldI marketing website (www.should-i.ai).

---

## Quick Links

### Content (Source of Truth for Copy)
- [Homepage Content](docs/content/homepage.md)
- [Example Report Content](docs/content/example-report.md)

### Technical Specs
- [Master Specification](docs/specs/master-spec.md) — Architecture, tooling, routing rules
- [SEO & LLM Strategy](docs/specs/seo-strategy.md) — Discovery optimization

### Design
- [Design Tokens](docs/design/design-tokens.md) — Colors, typography, spacing

### Context
- [Product Overview](docs/context/product-overview.md) — What ShouldI is

---

## Key Decisions

| Area | Decision |
|------|----------|
| Framework | Astro (static output only, no SSR for v1) |
| Hosting | Static deployment (Netlify/Vercel/DO static) |
| Design | Neutral editorial, single teal accent (`#0E7490`) |
| CTA Routing | All CTAs → GoHighLevel on `go.should-i.ai` |
| Docker | **Not used for v1** — static-first approach |

---

## Domain Architecture

| Domain | Role |
|--------|------|
| `www.should-i.ai` | Marketing, SEO, trust (indexable) |
| `go.should-i.ai` | Funnels, forms, checkout (noindex) |
| `app.should-i.ai` | Product delivery (auth only) |

---

## Build Order

As per Tim's instructions, build in this order:

1. **Homepage** — use `content/homepage.md`
2. **Example Report** — use `content/example-report.md`

Map sections into reusable Astro components: `Hero`, `Section`, `InsightBlock`, `CTA`

---

## Visual References

Build with this level of restraint (not templates):

- [Stripe Payments](https://stripe.com/payments)
- [Linear](https://linear.app)
- [Basecamp Shape Up](https://basecamp.com/shapeup)

> "Build Should-I with Stripe's restraint, Linear's simplicity, and Basecamp's editorial calm — if anything feels flashy or clever, remove it."
