# TNI Toolkit - Claude Code Context

## Project Overview

Community-built data files and planning tools for **Tower Networking Inc.** by Pocosia Studios.

**Repository:** https://github.com/salvo-praxis/tni-toolkit  
**Live Site:** https://tni-toolkit.salvo.host/

**Related Projects:**
- [TNI Seed Harvester](https://github.com/salvo-praxis/tni-seed-harvester) — Automation for seed data extraction
- [TNI Wiki Harvester](https://github.com/salvo-praxis/tni-wiki-harvester) — In-game wiki screenshot → transcription pipeline

---

## ⚡ SESSION STATE (VOLATILE)

> **This section tracks current work and is cleared after each successful commit.**

### Current Work

**Status:** IN PROGRESS  
**Session Date:** 2025-12-18  
**Last Commit:** Backlink config, OG image workflow, archive workflow updates, per-page og:image + GitHub SVG for all pages

---

### Pending This Session

| Task | Status |
|------|--------|
| Add inline SVG favicon to all 12 HTML files | ✅ Done |
| Add JSON-LD schema markup to all 12 HTML files | ✅ Done |

---

### Favicon Implementation

**Design:** Network node topology (green diagonals + orange cardinals) matching TNI Toolkit style guide.

**Method:** Single inline SVG data URI (~3.5 KB per file). No external files needed — each HTML remains fully standalone.

**Browser Support:** Chrome, Firefox, Edge, Safari 15+, iOS Safari 15+, Steam Deck. Covers 100% of Windows/Linux Steam audience.

**The favicon line to add inside `<head>` (after `<meta charset>`):**

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'><defs><linearGradient id='bg' x1='0%' y1='0%' x2='100%' y2='100%'><stop offset='0%' stop-color='%230a0e14'/><stop offset='50%' stop-color='%231a1f2e'/><stop offset='100%' stop-color='%230d1117'/></linearGradient><filter id='glowG' x='-150%' y='-150%' width='400%' height='400%'><feGaussianBlur stdDeviation='4'/><feColorMatrix type='matrix' values='0 0 0 0 0 0 0 0 0 1 0 0 0 0 0.53 0 0 0 0.2 0'/></filter><filter id='glowO' x='-150%' y='-150%' width='400%' height='400%'><feGaussianBlur stdDeviation='3'/><feColorMatrix type='matrix' values='0 0 0 0 0.94 0 0 0 0 0.53 0 0 0 0 0.24 0 0 0 0.2 0'/></filter><radialGradient id='inset' cx='50%' cy='50%' r='50%'><stop offset='70%' stop-color='%23000' stop-opacity='0'/><stop offset='100%' stop-color='%23000' stop-opacity='0.12'/></radialGradient></defs><rect width='64' height='64' rx='8' fill='%23f0883e'/><rect x='1.5' y='1.5' width='61' height='61' rx='6.5' fill='url(%23bg)'/><rect x='1.5' y='1.5' width='61' height='61' rx='6.5' fill='url(%23inset)'/><g filter='url(%23glowG)'><line x1='32' y1='32' x2='16' y2='16' stroke='%2300ff88' stroke-width='3'/><line x1='32' y1='32' x2='48' y2='16' stroke='%2300ff88' stroke-width='3'/><line x1='32' y1='32' x2='16' y2='48' stroke='%2300ff88' stroke-width='3'/><line x1='32' y1='32' x2='48' y2='48' stroke='%2300ff88' stroke-width='3'/><circle cx='16' cy='16' r='6' fill='%2300ff88'/><circle cx='48' cy='16' r='6' fill='%2300ff88'/><circle cx='16' cy='48' r='6' fill='%2300ff88'/><circle cx='48' cy='48' r='6' fill='%2300ff88'/><circle cx='32' cy='32' r='10' fill='%2300ff88'/></g><g filter='url(%23glowO)'><line x1='32' y1='32' x2='32' y2='12' stroke='%23f0883e' stroke-width='2'/><line x1='32' y1='32' x2='32' y2='52' stroke='%23f0883e' stroke-width='2'/><line x1='32' y1='32' x2='12' y2='32' stroke='%23f0883e' stroke-width='2'/><line x1='32' y1='32' x2='52' y2='32' stroke='%23f0883e' stroke-width='2'/><circle cx='32' cy='12' r='4' fill='%23f0883e'/><circle cx='32' cy='52' r='4' fill='%23f0883e'/><circle cx='12' cy='32' r='4' fill='%23f0883e'/><circle cx='52' cy='32' r='4' fill='%23f0883e'/></g><line x1='32' y1='32' x2='32' y2='12' stroke='%239c5628' stroke-width='1.5'/><line x1='32' y1='32' x2='32' y2='52' stroke='%239c5628' stroke-width='1.5'/><line x1='32' y1='32' x2='12' y2='32' stroke='%239c5628' stroke-width='1.5'/><line x1='32' y1='32' x2='52' y2='32' stroke='%239c5628' stroke-width='1.5'/><line x1='32' y1='32' x2='16' y2='16' stroke='%2300a658' stroke-width='2'/><line x1='32' y1='32' x2='48' y2='16' stroke='%2300a658' stroke-width='2'/><line x1='32' y1='32' x2='16' y2='48' stroke='%2300a658' stroke-width='2'/><line x1='32' y1='32' x2='48' y2='48' stroke='%2300a658' stroke-width='2'/><circle cx='32' cy='12' r='3.5' fill='%23161b22' stroke='%23f0883e' stroke-width='1.5'/><circle cx='32' cy='52' r='3.5' fill='%23161b22' stroke='%23f0883e' stroke-width='1.5'/><circle cx='12' cy='32' r='3.5' fill='%23161b22' stroke='%23f0883e' stroke-width='1.5'/><circle cx='52' cy='32' r='3.5' fill='%23161b22' stroke='%23f0883e' stroke-width='1.5'/><circle cx='16' cy='16' r='5' fill='%23161b22' stroke='%2300ff88' stroke-width='2'/><circle cx='48' cy='16' r='5' fill='%23161b22' stroke='%2300ff88' stroke-width='2'/><circle cx='16' cy='48' r='5' fill='%23161b22' stroke='%2300ff88' stroke-width='2'/><circle cx='48' cy='48' r='5' fill='%23161b22' stroke='%2300ff88' stroke-width='2'/><circle cx='32' cy='32' r='8' fill='%2300ff88'/><circle cx='32' cy='32' r='4' fill='%230a0e14'/></svg>">
```

**Files to update (12 total):**

| File | Location |
|------|----------|
| `index.html` | repo root |
| `credits.html` | repo root |
| `contributions.html` | repo root |
| `contributing.html` | repo root |
| `device-calculator.html` | tools/ |
| `seed-finder.html` | tools/ |
| `style-guide.html` | docs/ |
| `proposals-reference.html` | docs/ |
| `programs-reference.html` | docs/ |
| `cli-reference.html` | docs/ |
| `traffic-types-reference.html` | docs/ |
| `store-reference.html` | docs/ |

---

### Schema Markup (JSON-LD)

Add structured data for machine-readable page metadata. Place `<script type="application/ld+json">` in `<head>` after the favicon line.

**Approach:** Analyze each page's actual content and purpose, then select the most appropriate schema type. Don't apply generic types — each page has distinct value.

**Common fields for all pages:**
```json
{
  "@context": "https://schema.org",
  "isPartOf": {
    "@type": "WebSite",
    "name": "TNI Toolkit",
    "url": "https://tni-toolkit.salvo.host/"
  },
  "about": {
    "@type": "VideoGame",
    "name": "Tower Networking Inc.",
    "url": "https://store.steampowered.com/app/2939600/Tower_Networking_Inc/"
  }
}
```

**Schema type guidance (analyze content to confirm/adjust):**

| Page | Likely @type | Content Analysis Notes |
|------|--------------|------------------------|
| `index.html` | `WebSite` + `ItemList` | Landing page, lists available tools/resources |
| `device-calculator.html` | `WebApplication` | Interactive calculator tool |
| `seed-finder.html` | `WebApplication` | Interactive search/filter tool |
| `credits.html` | `AboutPage` | Attribution and credits |
| `contributions.html` | `AboutPage` | Contribution log/history |
| `contributing.html` | `HowTo` | Guide for contributors |
| `style-guide.html` | `TechArticle` | CSS/design documentation |
| `store-reference.html` | `TechArticle` | Equipment catalog with specs |
| `programs-reference.html` | `TechArticle` | Software/service catalog |
| `cli-reference.html` | `TechArticle` | Command reference documentation |
| `proposals-reference.html` | `TechArticle` | Proposal catalog with categories |
| `traffic-types-reference.html` | `TechArticle` | Classification/taxonomy of traffic types |

**Key instruction:** Read each page's content before writing its schema. Consider:
- What is this page's primary purpose?
- Is it a tool, a catalog, a guide, documentation?
- Does it contain a list of distinct items that could be individually typed?
- What would a user searching for this content expect to find?

**Example for an interactive tool:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "TNI Device Calculator",
  "description": "Server and program compatibility calculator for Tower Networking Inc.",
  "url": "https://tni-toolkit.salvo.host/tools/device-calculator.html",
  "applicationCategory": "GameTool",
  "operatingSystem": "Web Browser",
  "offers": { "@type": "Offer", "price": "0", "priceCurrency": "USD" },
  "isPartOf": {
    "@type": "WebSite",
    "name": "TNI Toolkit",
    "url": "https://tni-toolkit.salvo.host/"
  },
  "about": {
    "@type": "VideoGame",
    "name": "Tower Networking Inc.",
    "url": "https://store.steampowered.com/app/2939600/Tower_Networking_Inc/"
  }
}
</script>
```

**Example for a reference page:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "name": "TNI Store Reference",
  "headline": "Complete Equipment Catalog for Tower Networking Inc.",
  "description": "All 101 purchasable items across 16 categories. Servers, switches, routers, firewalls, cables, racks, and more with full specifications and prices.",
  "url": "https://tni-toolkit.salvo.host/docs/store-reference.html",
  "author": {
    "@type": "Person",
    "name": "Salvo Praxis"
  },
  "publisher": {
    "@type": "Organization",
    "name": "TNI Toolkit"
  },
  "isPartOf": {
    "@type": "WebSite",
    "name": "TNI Toolkit",
    "url": "https://tni-toolkit.salvo.host/"
  },
  "about": {
    "@type": "VideoGame",
    "name": "Tower Networking Inc.",
    "url": "https://store.steampowered.com/app/2939600/Tower_Networking_Inc/"
  }
}
</script>
```

---

### Deployment Chain

```
push to main
    ↓
Generate Sitemap (triggers on push)
    ↓
Generate OG Images (triggers on sitemap completion)
    ↓
Build ZIP (triggers on og-images completion)
    ↓
Deploy to FTP (triggers on build-zip completion)

───────────────────────────────────────────────────────────────
Submit To Wayback Machine — Daily (00:00 UTC) + Manual
Submit To Software Heritage — Manual only
```

---

## Architecture

All tools are **standalone HTML files** with embedded CSS/JS. No build process, no external dependencies, works offline. Each tool embeds its own data.

```
tni-toolkit/
├── .github/
│   └── workflows/
│       ├── generate-sitemap.yml         # Step 1: Auto-generate sitemap
│       ├── generate-og-images.yml       # Step 2: Auto-generate OG preview images
│       ├── build-zip.yml                # Step 3: Build tni-toolkit.zip
│       ├── ftp-deploy.yml               # Step 4: Deploy repo to FTP
│       ├── archive-wayback-machine.yml  # Daily + manual: Archive to Wayback
│       └── archive-software-heritage.yml # Manual: Archive to Software Heritage
├── CLAUDE.md              # You are here
├── CONTRIBUTING.md        # Contribution guidelines
├── CONTRIBUTIONS.md       # Contribution history log
├── index.html             # Landing page
├── contributing.html      # Contribution guide (styled)
├── contributions.html     # Contribution history (styled)
├── credits.html           # Credits, sources, greetz
├── README.md              # GitHub readme
├── sitemap.xml            # XML sitemap
├── robots.txt             # Crawler directives
├── tni-toolkit.zip        # Downloadable archive
├── data/                  # Source JSON datasets
│   ├── tni-store.json     # Equipment catalog
│   ├── tni-programs.json  # Server programs
│   ├── tni-proposals.json # Proposals catalog
│   ├── tni-cli-commands.json
│   └── tni-traffic-types.json
├── tools/                 # Standalone HTML tools
│   ├── device-calculator.html
│   └── seed-finder.html
└── docs/
    ├── STYLE_GUIDE.md     # Detailed styling reference
    ├── style-guide.html   # HTML version of style guide
    ├── proposals-reference.html      # Proposals quick reference (styled)
    ├── proposals-reference.md        # Proposals quick reference (markdown)
    ├── programs-reference.html       # Programs quick reference (styled)
    ├── programs-reference.md         # Programs quick reference (markdown)
    ├── cli-reference.html            # CLI commands quick reference (styled)
    ├── cli-reference.md              # CLI commands quick reference (markdown)
    ├── traffic-types-reference.html  # Traffic types quick reference (styled)
    ├── traffic-types-reference.md    # Traffic types quick reference (markdown)
    ├── store-reference.html          # Store catalog quick reference (styled)
    └── store-reference.md            # Store catalog quick reference (markdown)
```

### When Building New Tools

1. Use `tools/seed-finder.html` as the template (most complete example)
2. Follow `docs/STYLE_GUIDE.md` for all CSS patterns
3. Embed data directly in the HTML (no external fetches)
4. Include the inline SVG favicon in `<head>`
5. Test offline functionality before committing

---

## TODO

### Pending Attributions

| Who | Context | Status |
|-----|---------|--------|
| *(None pending)* | | |

### Data Projects

- [ ] **Store Reference Tooltips** — Hover tooltips showing item details + in-game images
  - Requires: 101 screenshots from game, cropped to item images
  - Process: Capture → crop → embed/reference in store-reference.html
  - Blocker: Screenshots not yet captured

- [ ] **In-Game Wiki Mirror** *(moved to [tni-wiki-harvester](https://github.com/salvo-praxis/tni-wiki-harvester))*
  - Goal: Extract wiki text for Claude context when building tools
  - Blocker: Screenshots not yet captured

### General

- [x] **Add inline SVG favicon to all 12 HTML files** *(done)*
- [x] **Add JSON-LD schema markup to all 12 HTML files** *(done — using TechArticle for reference pages)*

### Discoverability

- [ ] Write Steam Guide *(future — community visibility, wiki transcription will help)*

---

## Roadmap

### In Progress
- [ ] **CLI Command Builder** — Form-based command generator for NetShell

### Up Next  
- [ ] **Store Browser / Cart Calculator** — Browse equipment, build carts, calculate totals
  - *Blocker: Need equipment images from game*
- [ ] **Power Budget Calculator** — UPS capacity planning, power draw totals

### Planned
- [ ] Producer/Converter Dependency Planner
- [ ] Network Throughput Calculator
- [ ] Switch/Router Comparison Tool
- [ ] Decentro Network Planner
- [ ] Equipment ROI Calculator

---

## Working with Claude

Tips for effective development sessions.

### Session Discipline

1. **Start right**: Upload current files, state versions, check TODO
2. **Stay focused**: One feature/fix at a time when possible
3. **End clean**: Version bump, update all files, commit message, handoff

### Be Specific About Scope

Instead of: *"Build a power calculator"*

Say: *"Create `tools/power-calculator.html` following the style guide. It should let users select equipment from tni-store.json and sum up power draw. Use the same panel/card structure as seed-finder."*

### Iterate in Small Chunks

1. "Create the basic HTML structure with header and one panel"
2. "Add the equipment selection grid"
3. "Add the calculation logic"
4. "Add the results display"

If something breaks, you know exactly which step caused it.

### Reference Existing Files

*"Look at `tools/seed-finder.html` and use the same card hover pattern"*

Point to concrete examples rather than abstract descriptions.

### Checkpoint Often

After each working chunk, save locally. Git commit at session end.

### When Things Break

Don't say: *"It's broken, fix it"*

Say: *"The click handler on line 145 isn't firing. Check the event binding."*

Specific symptoms → faster fixes → less thrashing.

### Reset to Source of Truth

If confused: *"Stop. Read CLAUDE.md and docs/STYLE_GUIDE.md again. Then look at the current state of [file]."*

### Context Management

- **Running low on context?** Ask Claude for a session handoff
- **Starting fresh?** Upload files + state versions + check TODO
- **Version skew?** Trust file headers as source of truth, not memory

---

## Links

- [Style Guide](docs/STYLE_GUIDE.md) — Detailed CSS reference
- [Contributing](CONTRIBUTING.md) — How to contribute (markdown)
- [Contributing Guide](contributing.html) — How to contribute (styled)
- [Credits](credits.html) — Sources, contributors, greetz
- [TNI on Steam](https://store.steampowered.com/app/2939600/Tower_Networking_Inc/)
- [Pocosia Studios](https://pocosia.com/)
- [TNI Discord](https://discord.com/invite/nNKRMjDhf2) — Community
