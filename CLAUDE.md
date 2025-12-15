# TNI Toolkit - Claude Code Context

## Project Overview

Community-built data files and planning tools for **Tower Networking Inc.** by Pocosia Studios.

**Repository:** https://github.com/salvo-praxis/tni-toolkit  
**Live Site:** https://tni-toolkit.salvo.host/

---

## ⚡ SESSION STATE (VOLATILE)

> **This section tracks current work and is cleared after each successful commit.**

### Current Work

**Status:** IN PROGRESS — SEO & Archivability Setup  
**Session Date:** 2025-12-15

### Session Goals

1. **Visibility (SEO)** — Get indexed on Google, Bing, etc.
2. **Archivability** — Archive.org (Wayback Machine) + Software Heritage

### Changes This Session

**New files to create:**
- `sitemap.xml` — XML sitemap for search engines
- `robots.txt` — Crawler directives with sitemap reference
- `.github/workflows/generate-sitemap.yml` — Auto-generate sitemap on push
- `.github/workflows/archive-software-heritage.yml` — Archive to Software Heritage on release

**Files to update:**
- All HTML files — Add SEO meta tags (OG, canonical, keywords)
- `CLAUDE.md` — Document SEO meta tag standards
- `docs/style-guide.html` — Add meta tags section to documentation
- `docs/STYLE_GUIDE.md` — Add meta tags section
- `contributing.html` — Add meta tags documentation

### Pending User Actions

Salvo is handling these in parallel:
- [ ] Register site with Google Search Console (URL Prefix: `https://tni-toolkit.salvo.host`)
- [ ] Register site with Bing Webmaster Tools
- [ ] Manual "Save Page Now" on Archive.org for key URLs
- [ ] Submit repos to Software Heritage: `https://archive.softwareheritage.org/save/`
  - `https://github.com/salvo-praxis/tni-toolkit`
  - `https://github.com/salvo-praxis/tni-seed-harvester`

### Visibility Checklist (SEO)

| Task | Status | Notes |
|------|--------|-------|
| Create `sitemap.xml` | 🔴 TODO | Include all public HTML + JSON files |
| Create `robots.txt` | 🔴 TODO | Reference sitemap |
| Add SEO meta tags to HTML | 🔴 TODO | OG, canonical, description |
| Google Search Console | ⏳ Salvo | URL Prefix: tni-toolkit.salvo.host |
| Bing Webmaster Tools | ⏳ Salvo | Covers Yahoo/DuckDuckGo |
| Sitemap generation workflow | 🔴 TODO | Auto-update on push |
| Community outreach | ⏳ Future | Discord, Steam, Reddit |

### Archivability Checklist

| Task | Status | Notes |
|------|--------|-------|
| Manual Save Page Now | ⏳ Salvo | Key URLs on web.archive.org |
| Submit to Software Heritage | ⏳ Salvo | Both repos |
| Archive workflow (releases) | 🔴 TODO | Auto-trigger on GitHub release |
| Add Software Heritage badge | 🔴 TODO | README.md after first archive |

### Files Ready for Commit

sitemap.xml                     # NEW: XML sitemap
robots.txt                      # NEW: Crawler directives
generate-sitemap.yml            # NEW: Auto-generate sitemap
archive-software-heritage.yml   # NEW: Archive on release

---

## Architecture

All tools are **standalone HTML files** with embedded CSS/JS. No build process, no external dependencies, works offline. Each tool embeds its own data.

```
tni-toolkit/
├── .github/
│   └── workflows/
│       ├── build-zip-and-ftp-deploy-full-repo.yml  # CI/CD automation
│       ├── generate-sitemap.yml                     # NEW: Auto-generate sitemap
│       └── archive-software-heritage.yml            # NEW: Archive on release
├── CLAUDE.md              # You are here
├── CONTRIBUTING.md        # Contribution guidelines
├── CONTRIBUTIONS.md       # Contribution history log
├── index.html             # Landing page
├── contributing.html      # Contribution guide (styled)
├── contributions.html     # Contribution history (styled)
├── credits.html           # Credits, sources, greetz
├── README.md              # GitHub readme
├── sitemap.xml            # NEW: XML sitemap
├── robots.txt             # NEW: Crawler directives
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
    ├── proposals-reference.html      # Proposals quick reference
    ├── programs-reference.html       # Programs quick reference
    ├── cli-reference.html            # CLI commands quick reference
    ├── traffic-types-reference.html  # Traffic types quick reference
    └── store-reference.html          # Store catalog quick reference
```

### When Building New Tools

1. **Read `docs/STYLE_GUIDE.md` first** — Contains complete CSS reference, component patterns, and copy-paste templates
2. **Single HTML file** — All CSS in `<style>`, all JS in `<script>`, data embedded as JS objects
3. **Match the NOC aesthetic** — Dark theme, monospace font, green/blue accents
4. **Include standard footer** — Links to TNI Toolkit and Steam page
5. **Test offline** — Tools must work without network access
6. **Include SEO meta tags** — See Meta Tags section below

---

## Quick Reference

### Color Palette
```css
--bg-gradient: linear-gradient(135deg, #0a0e14 0%, #1a1f2e 50%, #0d1117 100%);
--surface: rgba(22, 27, 34, 0.8);
--border: #30363d;
--text-primary: #c9d1d9;
--text-secondary: #8b949e;
--text-muted: #7d8590;
--accent-green: #00ff88;
--accent-blue: #58a6ff;
--accent-orange: #f0883e;
--accent-red: #f85149;
--success: #238636;
```

### Typography
```css
font-family: "JetBrains Mono", "Fira Code", "SF Mono", Consolas, monospace;
```

### Standard Sizes
- H1: 20px, uppercase, letter-spacing: 2px
- H2 (panel headers): 13px, uppercase, letter-spacing: 1px
- Body text: 12px
- Small text: 11px
- Fine print: 10px

---

## File Header Standards

All project files include standardized headers for version tracking, attribution, and changelog.

### JSON Files

JSON data files include a `_meta` object as the first key:

```json
{
  "_meta": {
    "game": "Tower Networking Inc.",
    "dataset": "dataset-name",
    "version": "1.0.0",
    "last_updated": "YYYY-MM-DD",
    "description": "What this dataset contains",
    "sources": [
      { "name": "In-game observation", "notes": "..." },
      { "name": "Discord Community", "notes": "..." },
      { "name": "External Source", "url": "https://...", "author": "@handle", "retrieved": "YYYY-MM-DD" }
    ],
    "contributors": ["Name or Handle"],
    "corrections": [
      { "version": "1.0.1", "correction": "Description", "reported_by": "Who", "corrected_by": "Who" }
    ],
    "future_additions": [
      { "suggestion": "Brief description", "details": "Context", "suggested_by": "Who" }
    ]
  }
}
```

### HTML Files

HTML tools include a comment header **before** `<!DOCTYPE html>`:

```html
<!--
╔══════════════════════════════════════════════════════════════════════════════╗
║  Tool Name                                                                   ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  Version: X.Y.Z                                                              ║
║  Updated: YYYY-MM-DD                                                         ║
║  Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)          ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  Description:                                                                ║
║    Brief description of what this tool does.                                 ║
║                                                                              ║
║  Features:                                                                   ║
║    - Feature 1                                                               ║
║    - Feature 2                                                               ║
║                                                                              ║
║  Contributors:                                                               ║
║    - Name (contribution type)                                                ║
║                                                                              ║
║  Changelog:                                                                  ║
║    X.Y.Z - Description of changes                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
-->
```

### HTML Meta Tags (SEO)

All HTML files should include these meta tags in the `<head>` section after `<meta charset>` and `<meta viewport>`:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[Page Title] - TNI Toolkit</title>
    
    <!-- SEO Meta Tags -->
    <meta name="description" content="[Page-specific description, 150-160 chars]">
    <meta name="keywords" content="Tower Networking Inc, TNI, Pocosia Studios, [page-specific keywords]">
    <meta name="author" content="Salvo Praxis">
    <meta name="robots" content="index, follow">
    
    <!-- Open Graph (Facebook, Discord, etc.) -->
    <meta property="og:title" content="[Page Title] - TNI Toolkit">
    <meta property="og:description" content="[Same as meta description]">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://tni-toolkit.salvo.host/[path]">
    <meta property="og:site_name" content="TNI Toolkit">
    
    <!-- Twitter Card -->
    <meta name="twitter:card" content="summary">
    <meta name="twitter:title" content="[Page Title] - TNI Toolkit">
    <meta name="twitter:description" content="[Same as meta description]">
    
    <!-- Canonical URL -->
    <link rel="canonical" href="https://tni-toolkit.salvo.host/[path]">
    
    <style>
        /* ... */
    </style>
</head>
```

**Page-specific descriptions:**

| Page | Description |
|------|-------------|
| index.html | Community-built data files and planning tools for Tower Networking Inc. by Pocosia Studios. Device calculator, seed finder, and reference guides. |
| device-calculator.html | Plan your TNI server builds. Select devices, check off programs, verify CPU/Memory/Storage requirements fit. Works offline. |
| seed-finder.html | Find Tower Networking Inc. world seeds by starting proposals. 455 combinations across 3,794 verified seeds. |
| store-reference.html | Complete Tower Networking Inc. equipment catalog. 101 items across 16 categories with specs and prices. |
| programs-reference.html | All 25 TNI server programs with CPU, memory, storage requirements and I/O specifications. |
| proposals-reference.html | All 30 Tower Networking Inc. proposals with prerequisites, costs, and effects. |
| cli-reference.html | Complete NetShell command reference for Tower Networking Inc. 24 commands with syntax and examples. |
| traffic-types-reference.html | 14 network traffic types for TNI firewall rules and router configuration. |
| style-guide.html | TNI Toolkit design system. Colors, typography, UI components, and code patterns. |
| contributing.html | How to contribute to TNI Toolkit. Data corrections, feature suggestions, and pull requests. |
| contributions.html | TNI Toolkit contribution history log. Community corrections, features, and data additions. |
| credits.html | TNI Toolkit credits. Contributors, data sources, and community acknowledgments. |

### YAML Files

YAML configuration files (GitHub Actions, CI/CD) use comment headers:

```yaml
# ============================================================================
# TNI Toolkit - [File Type/Purpose]
# File: [path/to/file.yml]
# Name: [Workflow or Config Name]
# Version: X.Y.Z
# Updated: YYYY-MM-DD
# Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
# Description:
#   Brief description of what this file does.
#   Can span multiple lines if needed.
# Contributors:
#   - Name (@handle) - contribution type
#   - Claude - contribution type
# Changelog:
#   X.Y.Z - Description of changes
# ============================================================================
```

### Python Files

Python scripts use docstring headers:

```python
#!/usr/bin/env python3
"""
TNI Toolkit - [Script Name]
File: [path/to/script.py]
Version: X.Y.Z
Updated: YYYY-MM-DD
Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)

Description:
    Brief description of what this script does.
    Can span multiple lines if needed.

Contributors:
    - Name (@handle) - contribution type
    - Claude - contribution type

Changelog:
    X.Y.Z - Description of changes
"""
```

---

## Data Files

Tools should embed data directly. Source files in `data/`:

| File | Use For |
|------|---------|
| `tni-store.json` | Equipment specs, prices, power draw |
| `tni-programs.json` | Program requirements, I/O, dependencies |
| `tni-proposals.json` | Proposal prerequisites, costs, effects, unlocks |
| `tni-cli-commands.json` | Terminal commands, syntax, examples |
| `tni-traffic-types.json` | Network traffic types for firewall/router rules |

---

## Asset Strategy (Images)

### Problem
HTML tools are standalone and work offline, but images require external files or embedding.

### Options

1. **No images** (current) — Text-only, minimal footprint
2. **Base64 embedded** — Self-contained but bloated file size
3. **External `/assets/`** — Clean separation but requires file management

### Current Decision
Text-only for tools. Screenshots in `docs/screenshots/` for documentation only (README, etc.).

---

## SEO & Archivability

### Search Engine Visibility

**Google Search Console:** https://search.google.com/search-console
- Property type: URL Prefix
- URL: `https://tni-toolkit.salvo.host`
- Verification: HTML file, meta tag, or DNS

**Bing Webmaster Tools:** https://www.bing.com/webmasters
- Also covers Yahoo and DuckDuckGo
- Can import from Google Search Console

**Sitemap:** `https://tni-toolkit.salvo.host/sitemap.xml`
- Auto-generated by GitHub Action on push
- Includes all HTML files and JSON data files

### Archive Preservation

**Internet Archive (Wayback Machine):**
- Manual: https://web.archive.org → Save Page Now
- Automated: `wayback-machine-archiver` Python CLI
- Use "Save outlinks" for full page capture

**Software Heritage:**
- Submit repos: https://archive.softwareheritage.org/save/
- Repos to archive:
  - `https://github.com/salvo-praxis/tni-toolkit`
  - `https://github.com/salvo-praxis/tni-seed-harvester`
- Auto-archive on release via GitHub Action

**GitHub Archive Program:**
- All public repos automatically eligible
- Arctic Code Vault snapshots (periodic)

---

## Version Workflow

### Commit Message Format

**Title line** uses PR-style prefixes:

| Prefix | Use For |
|--------|---------|
| `data:` | JSON data file changes |
| `tool:` | HTML tool changes |
| `fix:` | Bug fixes |
| `docs:` | Documentation updates |
| `ci:` | GitHub Actions / automation |
| `style:` | Style guide, CSS-only changes |
| `meta:` | CLAUDE.md, project config |
| `seo:` | SEO-related changes (sitemap, meta tags) |

**Full format:**
```
prefix: brief summary (file vX.Y.Z)

Changes:
- Change 1
- Change 2

Attribution:
- Suggested by @username (if applicable)
- Reported by @username (if applicable)

Files updated:
- source-file.html (vX.Y.Z)
- CONTRIBUTIONS.md
- contributions.html (vX.Y.Z)
- credits.html (vX.Y.Z)
```

### Context Recovery Protocol

When starting a new Claude session:

1. **Read CLAUDE.md** — Especially SESSION STATE and TODO sections
2. **Check file headers** — Note current versions of relevant files
3. **Review recent CONTRIBUTIONS.md** — See what was just completed
4. **Check for "Pending" in SESSION STATE** — Attributions that need handling
5. **Ask if unclear** — "What version is [file] at? What are we working on?"

### Session Handoff Template

When context is getting full or session is ending, output:

```
SESSION HANDOFF
===============
Working on: [file(s)]
Starting version: vX.Y.Z
Current version: vX.Y.Z (or "unpublished changes from vX.Y.Z")
Changes this session:
- Change 1
- Change 2
Pending attributions:
- @username for [feature] (or "None")
Next steps:
- Step 1
- Step 2
Files ready for commit:
- file1.html (in outputs)
- file2.md (in outputs)
```

### Internal Files (No Public Attribution)

These files are internal and should NOT appear in CONTRIBUTIONS.md or credits.html:
- `CLAUDE.md` — Project context for Claude
- Draft/WIP files not yet published
- Test files

### Greetz Count Rules

credits.html Greetz section tracks community contribution counts.

**Counts as 1 contribution:**
- Reporting a bug that gets fixed
- Suggesting a feature that gets implemented
- Submitting data corrections
- Direct code/data contributions (PRs)

**Does NOT count:**
- Multiple suggestions in one conversation (= 1 contribution)
- Suggestions not yet implemented
- General feedback without actionable items

**Display order:** Descending by count, then alphabetical for ties.

### Recent Contributions Table

credits.html Recent Contributions is a **highlight reel**, not a complete log.

**Keep ~10-12 entries max.** The full history lives in contributions.html and CONTRIBUTIONS.md.

**Prioritize community contributions:**
- Bug reports that got fixed
- Feature suggestions that got implemented
- External data contributions (AlinaNova, Chaotic Crumb, etc.)
- External sources (@tower-network wiki, etc.)

**Deprioritize Salvo-only work:**
- Internal refactors, style changes
- New features without community input
- Documentation-only updates

**When trimming:** Remove oldest Salvo-only entries first. Keep community contributions visible longer — they're the whole point of the Greetz system.

### Quick Reference Table

```
┌─────────────────────────────────────────────────────────────┐
│ CHANGE TYPE        │ VERSION │ FILES TO UPDATE              │
├────────────────────┼─────────┼──────────────────────────────┤
│ Bug fix (reported) │ PATCH   │ source + CONTRIB + credits   │
│ Feature (suggested)│ MINOR   │ source + CONTRIB + credits   │
│ Salvo's own work   │ *       │ source + CONTRIB + credits   │
│ External PR        │ *       │ source + CONTRIB + credits   │
│ Internal/docs only │ PATCH   │ source only (maybe)          │
└─────────────────────────────────────────────────────────────┘
* = PATCH or MINOR depending on scope

COMMIT PREFIX: data: | tool: | fix: | docs: | ci: | style: | meta: | seo:

SESSION START: Note version → Check TODO → Set scope
SESSION END:   Bump once → Update all files → Commit message → Handoff
```

---

## TODO

### Pending Attributions

| Who | Context | Status |
|-----|---------|--------|
| *(None pending)* | | |

### Data Files

- [x] **tni-proposals.json** — Complete proposals catalog (30 proposals, 7 categories)
  - Added by AlinaNova (PROPOSALS_REFERENCE.md), converted to JSON by Salvo Praxis

### Device Calculator

- [x] Config menu: auto-prune, refurb toggle, warranty/traversals/power display *(completed & committed)*

### Seed Finder

- [x] Paginate results *(completed & committed)*
- [x] Config menu: seeds per page *(completed & committed)*

### General

- [x] Relative links where applicable *(completed & committed)*
- [x] HTML counterparts should link to HTML versions *(completed & committed)*
- [x] `tni-toolkit.zip` download link should be relative *(completed & committed)*

### Automation

- [x] YAML workflow: Build ZIP and FTP deploy *(completed & committed)*
- [ ] YAML workflow: Auto-generate sitemap *(in progress this session)*
- [ ] YAML workflow: Archive to Software Heritage on release *(in progress this session)*

### SEO

- [ ] Add sitemap.xml *(in progress this session)*
- [ ] Add robots.txt *(in progress this session)*
- [ ] Add meta tags to all HTML files *(in progress this session)*
- [ ] Register with Google Search Console *(Salvo)*
- [ ] Register with Bing Webmaster Tools *(Salvo)*

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

### Completed
- [x] Server/Program Compatibility Calculator
- [x] Starting Proposal Seed Finder
- [x] Reference Pages (store, programs, CLI, traffic types, proposals)

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
