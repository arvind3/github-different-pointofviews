# SKILL: Repo Awareness Pages Generator
**Version**: 1.1  
**Author**: For use with Claude Code  
**Purpose**: For any given GitHub repository, generate four professional GitHub Pages — Engineering, Product, Capability, and Executive Summary — using React (via CDN), Tailwind CSS, and state-of-the-art UX/UI design.

---

## HOW TO USE THIS SKILL

**Step 1** — Open Claude Code and navigate to your repo:
```bash
cd /path/to/your/repo
```
**Step 2** — Paste the entire contents of this file as your prompt to Claude Code, replacing the last line with your repo path or URL.

**Step 3** — Answer Claude's 4 enrichment questions when asked.

**Step 4** — Claude will generate all pages, commit them to a new branch `awareness-pages`, and open a Pull Request for your review.

**Step 5** — Review the PR. When happy, merge to `main` — your pages go live automatically.

**Repeat** for each repo. The whole process takes ~5 minutes per repo.

---

## MASTER PROMPT (copy everything below this line)

---

You are a world-class technical writer, product strategist, and frontend engineer. Your job is to analyze a GitHub repository and generate four beautifully designed, professional awareness pages as GitHub Pages HTML files.

These pages serve a specific mission: **bring visibility to a software solution across four distinct audiences** — engineers, product users, business strategists, and executives.

---

## PHASE 1 — REPO DISCOVERY

Before writing a single line of HTML, perform a thorough analysis of the repository. Read the following in this order:

1. `README.md` — primary source of truth
2. All files in `/docs`, `/wiki`, or `/notes` if they exist
3. Top-level folder and file structure (understand architecture)
4. `package.json`, `requirements.txt`, `pyproject.toml`, `Cargo.toml`, or equivalent (understand tech stack)
5. Key source files — enough to understand what the solution *actually does*, not just what it claims
6. Any existing tests, examples, or demo files — these reveal real usage patterns
7. GitHub issues, discussions, or changelogs if accessible — reveals pain points and evolution

From this analysis, extract and internally document:
- **Core problem solved** (1 sentence)
- **How it works technically** (architecture, key components, data flow)
- **Who uses it and how** (end user journey)
- **Tech stack** (languages, frameworks, key dependencies)
- **Maturity level** (prototype, MVP, production-ready)
- **Unique differentiator** (what makes this different from alternatives)

---

## PHASE 2 — ENRICHMENT QUESTIONS

After repo analysis, ask the owner these **exactly 4 questions** in a single message. Do not proceed to generation until you have answers.

```
Before I generate your four awareness pages, I need 4 inputs from you:

1. TARGET INDUSTRY / DOMAIN
   What industry or domain is the primary home for this solution?
   (e.g., "Healthcare data pipelines", "E-commerce personalization", "Developer tooling for ML teams")

2. KNOWN REAL-WORLD USE CASES
   List 2–3 specific scenarios where this has been or could be used.
   (e.g., "Used by fintech startup to reduce onboarding time by 40%")

3. BUSINESS IMPACT METRICS
   Any numbers, benchmarks, or outcomes you want highlighted.
   (e.g., "Reduces setup time from 3 days to 2 hours", "Handles 1M events/sec")
   If none yet, write: "None — generate plausible estimates based on the tech"

4. FOUNDER NARRATIVE
   In 2–4 sentences, tell me: Why did you build this? What problem were you personally
   frustrated by? What's the bigger vision?
```

If the owner says "generate everything from the repo", proceed with your best inferences and clearly mark inferred content with a subtle `*` footnote on each page.

---

## PHASE 3 — PAGE ARCHITECTURE

Generate **5 files** inside a `/docs` folder in the repository:

```
/docs/
  index.html          ← Hub page: links to all 4 pages with a beautiful landing UI
  engineering.html    ← Page 1: Engineering Perspective
  product.html        ← Page 2: Product Perspective  
  capability.html     ← Page 3: Capability Perspective
  executive.html      ← Page 4: Executive Summary
```

Also generate or update:
```
/_config.yml          ← GitHub Pages config (theme: none, since we use custom HTML)
```

---

## PHASE 4 — DESIGN SYSTEM (apply to ALL pages)

All five files share a **unified design language**. Before writing code, commit to ONE aesthetic direction that fits the solution's personality. Examples:
- A DevOps tool → industrial/precision aesthetic: dark background, monospace accents, terminal-inspired
- A healthcare AI tool → clinical/trustworthy: clean whites, deep navy, authoritative typography  
- A creative platform → expressive: bold color, editorial layout, unexpected typography
- A data pipeline tool → architectural/systematic: grid-based, technical elegance

**Technical stack per file (no build step required):**
```html
<!-- React via CDN -->
<script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

<!-- Tailwind via CDN -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Google Fonts — choose 2 distinctive fonts, NOT Inter, Roboto, Arial -->
<link href="https://fonts.googleapis.com/css2?family=YOUR_CHOICE..." rel="stylesheet">
```

**Design requirements (non-negotiable):**
- Fully responsive (mobile, tablet, desktop)
- Smooth scroll, subtle entrance animations (CSS keyframes)
- Navigation bar with links to all 4 pages + back to hub
- A distinct hero section per page with the page's thesis statement
- Footer with repo link, GitHub icon, and page name
- Consistent color palette via CSS variables across all files
- No placeholder content — every section must have real, repo-derived content
- Accessibility: semantic HTML, proper heading hierarchy, sufficient color contrast

---

## PHASE 5 — PAGE SPECIFICATIONS

### PAGE 1: `engineering.html` — Engineering Perspective
**Audience**: Developers, architects, technical evaluators  
**Tone**: Precise, credible, peer-to-peer  
**Target length**: 800–1200 words of content  

**Required sections** (in this order):
1. **Hero** — Solution name + one-line technical thesis (what it does and how, technically)
2. **Architecture Overview** — Visual diagram using pure CSS/HTML (boxes, arrows, layers) showing system components and data flow. No external diagram tools.
3. **Tech Stack** — Badges/chips for languages, frameworks, key dependencies with a one-liner on why each was chosen
4. **How It Works** — Step-by-step technical walkthrough (numbered, with code snippets where relevant, use `<pre><code>` blocks)
5. **Key Design Decisions** — 3–5 architectural decisions made and the tradeoffs considered
6. **Performance & Scalability** — Benchmarks, scale characteristics, known limits
7. **Getting Started** — Quick setup code block (install → configure → run)
8. **Contributing / Repo Link** — CTA to the GitHub repo

---

### PAGE 2: `product.html` — Product Perspective  
**Audience**: Product managers, end users, buyers, operators  
**Tone**: Empathetic, outcome-focused, benefit-driven  
**Target length**: 600–900 words of content  

**Required sections** (in this order):
1. **Hero** — Solution name + user-facing value proposition (what problem it solves for the user, not how)
2. **The Problem** — A narrative paragraph about the pain this solves. Make it visceral and recognizable.
3. **The Solution** — How the product addresses that pain, written from the user's perspective
4. **User Journey** — A visual step-by-step flow (CSS-only flowchart) showing how a user discovers → adopts → gets value from this solution
5. **Key Features** — 4–6 features as cards with icon (emoji or SVG), feature name, and 2-sentence user benefit description
6. **Who Is This For** — 2–3 user persona tiles (role, pain, how this helps)
7. **Before vs. After** — A two-column comparison showing life without vs. with this solution
8. **CTA** — Try it / Learn more / View on GitHub

---

### PAGE 3: `capability.html` — Capability Perspective  
**Audience**: Business strategists, domain experts, innovation teams, potential partners  
**Tone**: Expansive, imaginative, domain-aware  
**Target length**: 700–1000 words of content  

**Required sections** (in this order):
1. **Hero** — Solution name + capability thesis ("This is not just a tool for X — it is a platform for Y")
2. **Core Capability Map** — A CSS-only visual showing the central capability at the hub with 4–6 radiating use case domains
3. **Cross-Domain Applications** — For each of 4–6 industries/domains: domain name, the specific problem in that domain, how this solution applies, potential impact. Use enrichment input from the owner.
4. **Capability Building Blocks** — What underlying capabilities make this reusable/extensible (APIs, integrations, data model, etc.)
5. **Combination Plays** — 2–3 scenarios showing how this solution combined with other tools/platforms creates compound value
6. **Emerging Opportunity** — One forward-looking paragraph on where this capability is headed as technology evolves
7. **Partnership / Integration CTA** — Invitation for collaborators, integrators, or domain experts to connect

---

### PAGE 4: `executive.html` — Executive Summary (Founder's Perspective)  
**Audience**: C-suite, investors, board members, senior leadership  
**Tone**: Authoritative, narrative-driven, outcome-focused. No jargon. No fluff.  
**Target length**: 400–600 words of content (brevity is the point)  

**Required sections** (in this order):
1. **Hero** — Solution name + a single bold founder statement (the "why this exists" sentence)
2. **The Opportunity** — Market or operational problem framed at business scale (use enrichment metrics)
3. **What We Built** — 3 sentences max. What it is, who it's for, what it does.
4. **Traction / Evidence** — Metrics, milestones, usage data, or notable outcomes. Use enrichment input. If unavailable, use capability indicators (e.g., "Production-ready architecture supporting X scale")
5. **Strategic Value** — Why this matters beyond the immediate use case. Defensibility, moat, platform potential.
6. **The Ask / Next Step** — One clear call to action (schedule a demo, review the roadmap, fund the next phase, etc.) — ask the owner to specify or infer from context
7. **Founder Quote Block** — A styled pull-quote using the founder narrative from enrichment input

---

### HUB PAGE: `index.html` — Navigation Hub  
**Purpose**: The entry point. Orients any visitor and routes them to the right page.  

**Required sections**:
1. **Hero** — Solution name, tagline, and a 2-sentence description
2. **Four Page Cards** — One card per page with: page title, audience label, 1-sentence description, and a CTA button linking to that page. Cards should visually differentiate (distinct accent color or icon per card).
3. **Quick Stats Bar** — 3–4 key numbers about the solution (tech stack count, use case domains, etc.)
4. **Repo Link** — Prominent GitHub button

---

## PHASE 6 — BRANCH, COMMIT, AND PULL REQUEST

After all 5 HTML files and `_config.yml` are generated and written to disk, execute the following git workflow **automatically** without asking the user. This is the expected behavior every time.

### Step 1 — Detect default branch
```bash
git remote show origin | grep 'HEAD branch' | awk '{print $NF}'
```
Store the result as `DEFAULT_BRANCH` (usually `main` or `master`).

### Step 2 — Ensure you are on the default branch and up to date
```bash
git checkout $DEFAULT_BRANCH
git pull origin $DEFAULT_BRANCH
```

### Step 3 — Create and switch to a new feature branch
Use a consistent, predictable branch name:
```bash
git checkout -b awareness-pages
```
If a branch named `awareness-pages` already exists (e.g. this is a re-run), use:
```bash
git checkout -b awareness-pages-$(date +%Y%m%d)
```

### Step 4 — Stage and commit all generated files
```bash
git add docs/ _config.yml
git commit -m "feat: add awareness pages (engineering, product, capability, executive)

Generated by the Repo Awareness Pages skill.
- docs/index.html        → Hub navigation page
- docs/engineering.html  → Engineering perspective
- docs/product.html      → Product perspective
- docs/capability.html   → Capability perspective
- docs/executive.html    → Executive summary
- _config.yml            → GitHub Pages configuration"
```

### Step 5 — Push the branch to remote
```bash
git push -u origin awareness-pages
```
(Use the actual dated branch name if applicable.)

### Step 6 — Open a Pull Request using GitHub CLI
Check if `gh` (GitHub CLI) is available:
```bash
gh --version
```

**If `gh` is available**, run:
```bash
gh pr create \
  --title "feat: Add awareness pages (engineering, product, capability, executive)" \
  --body "## Awareness Pages — Review Checklist

This PR adds four professionally designed GitHub Pages to bring visibility to this solution across four audiences.

### Pages Added
| File | Audience | URL (after merge) |
|------|----------|-------------------|
| \`docs/index.html\` | All visitors | \`/\` |
| \`docs/engineering.html\` | Developers & architects | \`/engineering.html\` |
| \`docs/product.html\` | Product managers & users | \`/product.html\` |
| \`docs/capability.html\` | Business strategists | \`/capability.html\` |
| \`docs/executive.html\` | C-suite & leadership | \`/executive.html\` |

### Before Merging — Please Verify
- [ ] Hub page cards link correctly to all 4 pages
- [ ] Design/aesthetic matches the solution's personality
- [ ] No inferred content marked with \`*\` needs correction
- [ ] All sections have real content (no placeholders)
- [ ] Pages look good on mobile

### After Merging
1. Go to **Settings → Pages → Source → Deploy from branch**
2. Set branch: \`main\` | folder: \`/docs\`
3. Click Save — your pages will be live at:
   \`https://[your-username].github.io/[repo-name]/\`

> Generated by the Repo Awareness Pages Skill v1.1" \
  --base $DEFAULT_BRANCH \
  --head awareness-pages
```

**If `gh` is NOT available**, output these exact instructions for the user:
```
## Manual PR Instructions

gh CLI was not found. To open the Pull Request manually:

1. Go to: https://github.com/[your-username]/[repo-name]/compare/awareness-pages
2. Click "Create Pull Request"
3. Title: feat: Add awareness pages (engineering, product, capability, executive)
4. Review the files, then submit the PR.

After merging, enable GitHub Pages:
  Settings → Pages → Source → Deploy from branch
  Branch: main | Folder: /docs → Save

Your pages will be live at:
  https://[your-username].github.io/[repo-name]/
```

### Step 7 — Confirm to the user
After the PR is created (or instructions provided), output this summary:

```
✅ Done! Here's what was created:

Branch:  awareness-pages
Files:   docs/index.html, engineering.html, product.html, capability.html, executive.html
         _config.yml

PR:      [PR URL from gh output, or link to compare page]

Next steps:
1. Review the PR — check each page looks right
2. Merge to main when happy
3. Enable GitHub Pages in repo Settings (first time only)
4. Your awareness pages will be live at:
   https://[username].github.io/[repo-name]/
```

---

## QUALITY RULES (self-check before delivering)

Before finalizing, verify:
- [ ] All 5 HTML files are complete and self-contained (no broken imports)
- [ ] Navigation between all pages works via relative links
- [ ] No section is left with placeholder text like "Lorem ipsum" or "[INSERT X]"
- [ ] Every inferred piece of content is marked with a subtle footnote asterisk `*`
- [ ] Animations are CSS-only or use only CDN-loaded libraries
- [ ] All pages share the same color palette and font choices
- [ ] Each page has a unique hero section — no copy-paste across pages
- [ ] Mobile responsiveness confirmed via Tailwind responsive classes
- [ ] GitHub repo URL appears in footer of every page
- [ ] Branch `awareness-pages` has been pushed to remote
- [ ] Pull Request has been opened (via `gh` CLI or manual instructions provided)
- [ ] PR description contains the review checklist and post-merge GitHub Pages setup steps

---

## INPUT — PROVIDE BELOW THIS LINE

**Repository**: [paste GitHub URL or local path here]

---
*End of skill prompt*
