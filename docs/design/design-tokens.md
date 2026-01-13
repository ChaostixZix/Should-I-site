# ShouldI Design Tokens

Design specifications from Tim's email for the ShouldI marketing website.

---

## Colors

Use these exact values:

| Token | Value | Usage |
|-------|-------|-------|
| Background | `#F7F8FA` | Page background |
| Surface | `#FFFFFF` | Cards, elevated elements |
| Text | `#111827` | Primary text |
| Text muted | `#6B7280` | Secondary/supporting text |
| Border | `#E5E7EB` | Dividers, borders |
| Accent teal | `#0E7490` | **CTAs only** |

---

## Typography

**Font Family:** Inter (single family throughout)

| Element | Size | Weight | Line Height |
|---------|------|--------|-------------|
| Hero | 72px | 700 | 1.1 |
| H2 | 48px | 700 | 1.1 |
| H3 | 20px | 600 | 1.1 |
| Body | 16px | 400 | 1.6 |

---

## Spacing

| Property | Desktop | Mobile |
|----------|---------|--------|
| Section padding (vertical) | 160px | 80px |
| Container padding (horizontal) | 48px | — |
| Max content width | 1280px | — |

---

## Visual Direction

Reference sites (copy the level of **restraint**, not the templates):

- **Stripe:** https://stripe.com/payments
- **Linear:** https://linear.app
- **Basecamp:** https://basecamp.com/shapeup

> "Build Should-I with Stripe's restraint, Linear's simplicity, and Basecamp's editorial calm — if anything feels flashy or clever, remove it."

---

## Visual Rules

- White/off-white background, dark text
- One teal accent only for primary CTAs + key emphasis
- Big readable typography, generous spacing
- Single-column scroll, minimal visuals, no gimmicks/animations
- **No dark mode**
- **No gradients**

---

## CSS Variables Reference

```css
:root {
  /* Colors */
  --color-background: #F7F8FA;
  --color-surface: #FFFFFF;
  --color-text: #111827;
  --color-text-muted: #6B7280;
  --color-border: #E5E7EB;
  --color-accent: #0E7490;
  
  /* Typography */
  --font-family: 'Inter', sans-serif;
  --font-size-hero: 72px;
  --font-size-h2: 48px;
  --font-size-h3: 20px;
  --font-size-body: 16px;
  --font-weight-bold: 700;
  --font-weight-semibold: 600;
  --font-weight-regular: 400;
  --line-height-heading: 1.1;
  --line-height-body: 1.6;
  
  /* Spacing */
  --section-padding-desktop: 160px;
  --section-padding-mobile: 80px;
  --container-padding: 48px;
  --max-width: 1280px;
}
```
