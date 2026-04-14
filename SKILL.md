---
name: ui-ux-pro-max
description: "UI/UX design intelligence for web and mobile. Includes 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 10 stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, and HTML/CSS). Actions: plan, build, create, design, implement, review, fix, improve, optimize, enhance, refactor, and check UI/UX code. Projects: website, landing page, dashboard, admin panel, e-commerce, SaaS, portfolio, blog, and mobile app. Elements: button, modal, navbar, sidebar, card, table, form, and chart. Styles: glassmorphism, claymorphism, minimalism, brutalism, neumorphism, bento grid, dark mode, responsive, skeuomorphism, and flat design. Topics: color systems, accessibility, animation, layout, typography, font pairing, spacing, interaction states, shadow, and gradient. Integrations: shadcn/ui MCP for component search and examples."
---

# UI/UX Pro Max — Design Intelligence

Searchable design database with 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 10 stacks.

## When to Use

Use when tasks involve UI structure, visual design decisions, interaction patterns, or UX quality control. Skip for pure backend, API-only, infrastructure, or non-visual work.

## Rule Priority (1=highest)

| # | Category | Impact | Domain |
|---|----------|--------|--------|
| 1 | Accessibility | CRITICAL | `ux` |
| 2 | Touch & Interaction | CRITICAL | `ux` |
| 3 | Performance | HIGH | `ux` |
| 4 | Style Selection | HIGH | `style`, `product` |
| 5 | Layout & Responsive | HIGH | `ux` |
| 6 | Typography & Color | MEDIUM | `typography`, `color` |
| 7 | Animation | MEDIUM | `ux` |
| 8 | Forms & Feedback | MEDIUM | `ux` |
| 9 | Navigation Patterns | HIGH | `ux` |
| 10 | Charts & Data | LOW | `chart` |

## Workflow

### Step 1: Generate Design System (start here)

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<product_type> <industry> <keywords>" --design-system [-p "Project Name"]
```

Returns: pattern, style, colors, typography, effects, and anti-patterns.

To persist for cross-session use, add `--persist`:

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<query>" --design-system --persist -p "Project Name" [--page "dashboard"]
```

Creates `design-system/MASTER.md` and optional `design-system/pages/{page}.md` overrides.

### Step 2: Domain Searches (as needed)

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<keyword>" --domain <domain> [-n <max_results>]
```

| Domain | Use For |
|--------|---------|
| `product` | Product type patterns (SaaS, e-commerce, portfolio) |
| `style` | UI styles and effects (glassmorphism, minimalism) |
| `typography` | Font pairings (elegant, playful, professional) |
| `color` | Color palettes by product type |
| `landing` | Page structure, CTA strategies |
| `chart` | Chart types and recommendations |
| `ux` | Best practices, anti-patterns |
| `google-fonts` | Individual font lookup |
| `react` | React/Next.js performance |
| `web` | App interface guidelines (iOS/Android) |
| `prompt` | AI prompts, CSS keywords |

### Step 3: Stack Guidelines

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<keyword>" --stack react-native
```

## Reference Files (load on demand)

These files contain detailed rules. Read only the relevant file for the current task:

- **`references/quick-reference.md`** — Full rules for all 10 priority categories. Consult when implementing or reviewing specific UI areas (accessibility, animation, forms, navigation, etc.)
- **`references/common-rules.md`** — Professional UI standards for icons, interaction, light/dark mode, layout. Consult when reviewing UI polish.
- **`references/pre-delivery-checklist.md`** — Final verification checklist. Consult before delivering UI code.

## Output Formats

```bash
# ASCII (default)
python3 skills/ui-ux-pro-max/scripts/search.py "query" --design-system
# Markdown
python3 skills/ui-ux-pro-max/scripts/search.py "query" --design-system -f markdown
```
