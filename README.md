# github-different-pointofviews

A collection of **Repo Awareness Pages** — professionally designed GitHub Pages that bring
visibility to software repositories across four distinct audiences.

---

## What Are Awareness Pages?

Awareness Pages are a set of five HTML files, generated from a repository's source code and
documentation, that explain the same project from four different angles:

| Page | Audience | What It Covers |
|------|----------|----------------|
| `index.html` | Everyone | Hub: links to all four pages with stats and quick description |
| `engineering.html` | Developers & Architects | Architecture, tech stack, code walkthrough, design decisions |
| `product.html` | Product Managers & End Users | User journey, features, personas, before-vs-after |
| `capability.html` | Business Strategists & Partners | Cross-domain applications, combination plays, emerging opportunity |
| `executive.html` | C-Suite & Leadership | Market framing, what was built, traction, strategic value |

All pages share a unified dark design system (Plus Jakarta Sans + JetBrains Mono),
are fully responsive, and require no build step — they use React and Tailwind via CDN.

---

## Current Awareness Pages

### Retail Analytics (`docs/`)

Awareness pages for [arvind3/retail_analytics](https://github.com/arvind3/retail_analytics) —
an enterprise-grade in-browser retail analytics platform powered by DuckDB-WASM and Parquet,
deployed as a static site on GitHub Pages with zero backend infrastructure.

**Live platform:** https://arvind3.github.io/retail_analytics/#/

#### Pages

| File | Description | Direct Link (after enabling GitHub Pages) |
|------|-------------|-------------------------------------------|
| [`docs/index.html`](docs/index.html) | Hub — entry point for all audiences | `/` |
| [`docs/engineering.html`](docs/engineering.html) | Architecture, DuckDB-WASM internals, setup guide | `/engineering.html` |
| [`docs/product.html`](docs/product.html) | User journey, features, personas, before/after | `/product.html` |
| [`docs/capability.html`](docs/capability.html) | Cross-domain applications, capability map | `/capability.html` |
| [`docs/executive.html`](docs/executive.html) | Strategic narrative, traction, founder story | `/executive.html` |

#### How to Enable GitHub Pages for This Repo

1. Go to **Settings → Pages** in this repository
2. Under **Source**, select **Deploy from a branch**
3. Set **Branch**: `main` | **Folder**: `/docs`
4. Click **Save**

Your awareness pages will be live at:
```
https://[your-username].github.io/github-different-pointofviews/
```

---

### FakerUI (`docs/`)

Awareness pages for [arvind3/fakerUI](https://github.com/arvind3/fakerUI) —
a browser-native data generation platform that runs Python's full Faker ecosystem entirely
in-browser via Pyodide. No backend, no install, no API key. Browse 300+ Faker methods,
compose multi-field schemas, and export clean JSON/CSV datasets in seconds.

**Live platform:** https://arvind3.github.io/fakerUI/

**Design system:** Space Grotesk + JetBrains Mono · Dark navy (`#080c14`) · Cyan (`#22d3ee`) · Emerald (`#34d399`) · Purple (`#a78bfa`) · Amber (`#fbbf24`)

> Inferred content is marked with `*` footnotes throughout each page.

#### Pages

| File | Audience | What It Covers |
|------|----------|----------------|
| [`docs/index.html`](docs/index.html) | Everyone | Hub — entry point with stats bar and cards linking to all four pages |
| [`docs/engineering.html`](docs/engineering.html) | Developers & Architects | Build pipeline, Pyodide runtime, architecture diagram, tech stack, design decisions, performance, setup guide |
| [`docs/product.html`](docs/product.html) | QA Teams & Product Managers | Problem narrative, solution overview, user journey flowchart, 6 feature cards, 3 persona tiles, before/after comparison |
| [`docs/capability.html`](docs/capability.html) | Strategists & Innovation Teams | Capability hub-and-spoke map, 6 cross-domain applications, building blocks, 3 combination plays, emerging opportunity |
| [`docs/executive.html`](docs/executive.html) | C-Suite & Leadership | Market opportunity, 3-sentence product description, production traction, strategic value, founder quote |

#### How to View Locally

Open any `.html` file directly in a browser — no build step needed. All dependencies
(React, Tailwind, Babel, Google Fonts) are loaded via CDN.

```bash
# macOS / Linux
open docs/index.html

# Windows
start docs/index.html
```

#### Key Facts About the FakerUI Pages

- **Technology stack:** React 18 (CDN) · Tailwind CSS (CDN) · Babel Standalone · Space Grotesk + JetBrains Mono (Google Fonts)
- **Data source:** All content derived from the [fakerUI repository](https://github.com/arvind3/fakerUI) README, source files, and CONTRIBUTING.md
- **Inferred content:** Items marked `*` are estimated based on architecture analysis (e.g., load times, locale counts, business impact metrics)
- **Faker version covered:** v19.13.0 with Pyodide v0.27.2
- **No data leaves the browser:** The pages are fully static; nothing is tracked or stored

---

## How to Generate Awareness Pages for a New Repo

This repository includes the skill prompt that was used to generate these pages.

1. Open [REPO_AWARENESS_PAGES_SKILL.md](REPO_AWARENESS_PAGES_SKILL.md) in Claude Code
2. Run: `use the skill @REPO_AWARENESS_PAGES_SKILL.md to create page for https://github.com/[owner]/[repo]`
3. Answer the 4 enrichment questions when asked
4. Claude will generate all 5 HTML files, commit them to a new branch, and open a PR

The whole process takes approximately 5 minutes per repository.

---

## Design Systems

Each repo's awareness pages use a distinct visual identity chosen to match the project's personality.

### Retail Analytics — "Data Dashboard" aesthetic
- **Fonts**: Plus Jakarta Sans (display) + JetBrains Mono (code/labels)
- **Palette**: Deep ink (`#0a0a14`) · Indigo (`#6366f1`) · Amber (`#f59e0b`) · Green (`#10b981`)

### FakerUI — "Precision Terminal" aesthetic
- **Fonts**: Space Grotesk (display) + JetBrains Mono (code/labels)
- **Palette**: Deep navy (`#080c14`) · Cyan (`#22d3ee`) · Emerald (`#34d399`) · Purple (`#a78bfa`) · Amber (`#fbbf24`)

### Shared across all pages
- **Stack**: React 18 (CDN) · Tailwind CSS (CDN) · Babel Standalone · Google Fonts
- **No build step required** — open any `.html` file directly in a browser
- **Animations**: CSS keyframe `fadeInUp` entrance animations, hero grid backgrounds
- **Responsive**: Tailwind responsive grid classes for mobile, tablet, and desktop

---

*Generated using the Repo Awareness Pages Skill v1.1*
