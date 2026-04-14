# Slim Pro Max

A fork of [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) by [Next Level Builder](https://github.com/nextlevelbuilder), restructured for better token efficiency in [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## What Changed From the Original

The original ui-ux-pro-max-skill is a design intelligence database with BM25 search. This fork keeps the same core data and search algorithm but restructures how results are delivered to reduce token consumption in Claude Code sessions:

- **Master + Overrides persistence** — design system recommendations are written to `MASTER.md` and page-specific override files (`design-system/pages/{page}.md`), so the same design context doesn't need to be re-queried and re-injected into every conversation turn. The original is stateless per-session.
- **Reference file separation** — quick-reference rules, common UI standards, and a pre-delivery checklist are broken into standalone files in `references/` that the skill loads on demand, rather than inlining all guidance into a single prompt. This lets Claude read only the relevant reference for the current task.
- **Result selection scoring** — the design system generator applies priority-weighted scoring against the `ui-reasoning.csv` ruleset when selecting which BM25 results to surface, reducing irrelevant results that waste context tokens.
- **Output truncation** — long CSV field values are capped at 300 characters in search output. The original returns full field content.
- **Skill definition as routing layer** — `SKILL.md` defines when to use each search domain and reference file, so Claude doesn't load the entire knowledge base speculatively. The original skill definition is more monolithic.

Everything else — the BM25 implementation, CSV data files, domain structure, and search interface — comes directly from the original project.

## What It Does

Provides structured UI/UX knowledge that Claude Code can query during frontend development — style recommendations, color palettes, typography pairings, UX guidelines, chart selection, and stack-specific best practices.

- **50+ UI styles** — glassmorphism, brutalism, minimalism, neumorphism, bento grid, etc.
- **161 color palettes** — organized by product type with full token sets
- **57 font pairings** — categorized by mood with Google Fonts URLs and Tailwind config
- **161 product types** — SaaS, e-commerce, fintech, healthcare, and more
- **99 UX guidelines** — accessibility, touch, performance, navigation, forms
- **25 chart types** — with accessibility grades, library recommendations, and anti-patterns
- **16 stack guidelines** — React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, Angular, Laravel, Three.js, and more

## Search Domains

| Domain | Data | Records |
|--------|------|---------|
| `style` | UI styles, effects, CSS keywords | 50+ |
| `color` | Color palettes by product type | 161 |
| `typography` | Font pairings with import code | 57 |
| `product` | Product type patterns | 161 |
| `ux` | Best practices and anti-patterns | 99 |
| `chart` | Chart type recommendations | 25 |
| `landing` | Page structure and CTA strategies | — |
| `google-fonts` | Individual font lookup | 1500+ |
| `react` | React/Next.js performance rules | — |
| `web` | App interface guidelines | — |
| `icons` | Icon library recommendations | — |

## Usage

### Generate a Design System

```bash
python3 scripts/search.py "SaaS analytics dashboard" --design-system
```

Returns a complete recommendation: style, color palette, typography, effects, and anti-patterns.

### Persist a Design System

```bash
python3 scripts/search.py "SaaS analytics" --design-system --persist -p "Acme Dashboard"
python3 scripts/search.py "SaaS analytics" --design-system --persist -p "Acme Dashboard" --page "settings"
```

Creates `design-system/MASTER.md` and optional page-specific overrides in `design-system/pages/`.

### Domain Search

```bash
python3 scripts/search.py "glassmorphism" --domain style
python3 scripts/search.py "fitness app" --domain color
python3 scripts/search.py "elegant serif" --domain typography
```

### Stack-Specific Guidelines

```bash
python3 scripts/search.py "performance" --stack react
python3 scripts/search.py "navigation" --stack swiftui
python3 scripts/search.py "animation" --stack flutter
```

Available stacks: `react`, `nextjs`, `vue`, `svelte`, `astro`, `swiftui`, `react-native`, `flutter`, `nuxtjs`, `nuxt-ui`, `html-tailwind`, `shadcn`, `jetpack-compose`, `threejs`, `angular`, `laravel`

## Setup

### Prerequisites

- Python 3.10+
- No external dependencies (uses only stdlib)

### As a Claude Code Skill

Copy the directory structure to `~/.claude/skills/slim-pro-max/` and `SKILL.md` enables the `/slim-pro-max` slash command.

### Standalone

```bash
git clone https://github.com/uehlingeric/slim-pro-max.git
cd slim-pro-max
python3 scripts/search.py "your query" --design-system
```

## Architecture

```
slim-pro-max/
├── scripts/
│   ├── search.py          # CLI entry point
│   ├── core.py            # BM25 search engine + CSV config
│   └── design_system.py   # Design system generator
├── data/
│   ├── styles.csv         # 50+ UI styles
│   ├── colors.csv         # 161 color palettes
│   ├── typography.csv     # 57 font pairings
│   ├── products.csv       # 161 product types
│   ├── ux-guidelines.csv  # 99 UX rules
│   ├── charts.csv         # 25 chart types
│   ├── google-fonts.csv   # 1500+ fonts
│   ├── landing.csv        # Landing page patterns
│   ├── icons.csv          # Icon recommendations
│   └── stacks/            # 16 stack-specific CSVs
├── references/
│   ├── quick-reference.md     # 10-priority rule categories
│   ├── common-rules.md        # Professional UI standards
│   └── pre-delivery-checklist.md
└── SKILL.md               # Claude Code skill definition
```

The search engine is a from-scratch BM25 implementation (~160 lines) with no dependencies. Auto-detects the most relevant domain from the query when none is specified.

## Rule Priority

| # | Category | Impact |
|---|----------|--------|
| 1 | Accessibility | CRITICAL |
| 2 | Touch & Interaction | CRITICAL |
| 3 | Performance | HIGH |
| 4 | Style Selection | HIGH |
| 5 | Layout & Responsive | HIGH |
| 6 | Typography & Color | MEDIUM |
| 7 | Animation | MEDIUM |
| 8 | Forms & Feedback | MEDIUM |
| 9 | Navigation Patterns | HIGH |
| 10 | Charts & Data | LOW |

## Attribution

This project is a fork of [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) by [Next Level Builder](https://github.com/nextlevelbuilder). The original project's BM25 search engine, CSV data architecture, and design domain structure are the foundation this fork builds on.

## License

MIT (same as the [original project](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill))
