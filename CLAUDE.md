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

**Status:** READY TO COMMIT  
**Session Date:** 2025-12-16 / 2025-12-17  
**Last Commit:** (pending) — Backlink config, OG image workflow, archive workflow updates, per-page og:image + GitHub SVG for all pages

---

### Completed This Session

| File | Version | Changes |
|------|---------|---------|
| `index.html` | v1.5.2 | Local download link; clean launch links; GitHub SVG in ToC & footer; og:image updated |
| `tools/device-calculator.html` | v1.9.0 | Backlink config toggle in General section; simplified backlink logic; og:image updated; GitHub SVG footer |
| `tools/seed-finder.html` | v1.4.0 | Backlink config toggle; reordered config menu; simplified backlink logic; og:image updated; GitHub SVG footer |
| `generate-sitemap.yml` | v1.2.0 | Adds tni-toolkit.zip for archive.org; removed obsolete ?from=toolkit URLs |
| `generate-og-images.yml` | v1.0.1 | **NEW** — Auto-screenshots all pages (1200x630); hides backlink for cleaner capture |
| `build-zip.yml` | v1.0.0 | **NEW** — Split from combined workflow; builds & commits zip |
| `ftp-deploy.yml` | v1.0.0 | **NEW** — Split from combined workflow; deploys repo to FTP |
| `archive-wayback-machine.yml` | v1.1.1 | Renamed "Submit To Wayback Machine"; daily schedule + manual |
| `archive-software-heritage.yml` | v1.1.0 | Renamed "Submit To Software Heritage"; manual only (removed release trigger) |
| ~~`build-zip-and-ftp-deploy-full-repo.yml`~~ | — | **DELETE** — Replaced by build-zip.yml + ftp-deploy.yml |
| `credits.html` | — | og:image updated; GitHub SVG footer |
| `contributions.html` | — | og:image updated; GitHub SVG footer |
| `contributing.html` | — | og:image updated; GitHub SVG footer |
| `docs/style-guide.html` | — | og:image updated; GitHub SVG footer |
| `docs/proposals-reference.html` | — | og:image updated; GitHub SVG footer |
| `docs/programs-reference.html` | — | og:image updated; GitHub SVG footer |
| `docs/cli-reference.html` | — | og:image updated; GitHub SVG footer |
| `docs/traffic-types-reference.html` | — | og:image updated; GitHub SVG footer |
| `docs/store-reference.html` | — | og:image updated; GitHub SVG footer |

---

### Deployment Chain (Updated)

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

### Files Ready for Commit

**HTML Files (place in repo root and subdirectories):**
- `index.html` → repo root
- `credits.html` → repo root
- `contributions.html` → repo root
- `contributing.html` → repo root
- `tools/device-calculator.html` → tools/
- `tools/seed-finder.html` → tools/
- `docs/style-guide.html` → docs/
- `docs/proposals-reference.html` → docs/
- `docs/programs-reference.html` → docs/
- `docs/cli-reference.html` → docs/
- `docs/traffic-types-reference.html` → docs/
- `docs/store-reference.html` → docs/

**Workflows (place in `.github/workflows/`):**
- `generate-sitemap.yml`
- `generate-og-images.yml`
- `build-zip.yml` *(replaces build-zip-and-ftp-deploy-full-repo.yml)*
- `ftp-deploy.yml` *(replaces build-zip-and-ftp-deploy-full-repo.yml)*
- `archive-wayback-machine.yml`
- `archive-software-heritage.yml`

**Delete from `.github/workflows/`:**
- `build-zip-and-ftp-deploy-full-repo.yml` *(replaced by build-zip.yml + ftp-deploy.yml)*

**This file:**
- `CLAUDE.md` → repo root

---

### Commit Message

```
feat: Backlink config toggle, OG image automation, archive scheduling

Tools:
- device-calculator.html v1.9.0: Backlink toggle in Settings → General;
  simplified archive.org-compatible logic; GitHub SVG footer; per-page og:image
- seed-finder.html v1.4.0: Backlink toggle; reordered config menu
  (Spoiler Prevention first); GitHub SVG footer; per-page og:image

Index:
- index.html v1.5.2: Local download link (./tni-toolkit.zip); removed
  ?from=toolkit params; GitHub SVG in ToC & footer; per-page og:image

All Pages (og:image + GitHub SVG):
- credits.html, contributions.html, contributing.html
- docs/style-guide.html, docs/proposals-reference.html
- docs/programs-reference.html, docs/cli-reference.html
- docs/traffic-types-reference.html, docs/store-reference.html

Workflows:
- generate-og-images.yml v1.0.1: NEW — Auto-screenshots all pages (1200x630)
  using headless Chromium; hides backlink during capture
- generate-sitemap.yml v1.2.0: Adds tni-toolkit.zip for archive.org
- build-zip.yml v1.0.0: NEW — Split from combined; builds & commits zip
- ftp-deploy.yml v1.0.0: NEW — Split from combined; deploys to FTP
- archive-wayback-machine.yml v1.1.1: Renamed; daily cron + manual (decoupled)
- archive-software-heritage.yml v1.1.0: Renamed; manual only
- DELETED: build-zip-and-ftp-deploy-full-repo.yml (replaced by split workflows)

Deployment chain: Sitemap → OG Images → Build ZIP → Deploy to FTP
Archive chain: Wayback (daily 00:00 UTC), Software Heritage (manual)
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
║    X.Y.Z - Change description                                                ║
╚══════════════════════════════════════════════════════════════════════════════╝
-->
```

### YAML Workflow Files

```yaml
# ============================================================================
# TNI Toolkit - GitHub Actions Workflow
# File: .github/workflows/workflow-name.yml
# Name: Workflow Display Name
# Version: X.Y.Z
# Updated: YYYY-MM-DD
# Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
#
# Description:
#   What this workflow does and when it runs.
#
# Contributors:
#   - name (@handle) - contribution
#
# Changelog:
#   X.Y.Z - Change description
# ============================================================================
```

---

## Meta Tags

All HTML files should include these meta tags in `<head>`:

```html
<!-- SEO Meta Tags -->
<meta name="description" content="[Page-specific description, ~155 chars]">
<meta name="author" content="Salvo Praxis">
<meta name="robots" content="index, follow">

<!-- Open Graph (Facebook, Discord, etc.) -->
<meta property="og:title" content="[Page Title] - TNI Toolkit">
<meta property="og:description" content="[Same as meta description]">
<meta property="og:type" content="website">
<meta property="og:url" content="https://tni-toolkit.salvo.host/[path]">
<meta property="og:site_name" content="TNI Toolkit">
<meta property="og:image" content="https://tni-toolkit.salvo.host/images/og-preview.png">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="[Page Title] - TNI Toolkit">
<meta name="twitter:description" content="[Shorter description, ~100 chars]">

<!-- Canonical URL -->
<link rel="canonical" href="https://tni-toolkit.salvo.host/[path]">
```

---

## Versioning & Attribution

### Version Number Format

**MAJOR.MINOR.PATCH** (SemVer-style)

- **PATCH** (X.Y.Z → X.Y.Z+1): Bug fixes, typo corrections, data fixes
- **MINOR** (X.Y.Z → X.Y+1.0): New features, new data fields, UI additions
- **MAJOR** (X.Y.Z → X+1.0.0): Breaking changes, major redesigns

### When to Bump Versions

| Change Type | Version Bump | Example |
|-------------|--------------|---------|
| Typo fix | PATCH | 1.2.0 → 1.2.1 |
| Data correction | PATCH | 1.2.1 → 1.2.2 |
| Bug fix | PATCH | 1.2.2 → 1.2.3 |
| New feature | MINOR | 1.2.3 → 1.3.0 |
| New data field | MINOR | 1.3.0 → 1.4.0 |
| UI addition | MINOR | 1.4.0 → 1.5.0 |
| Major redesign | MAJOR | 1.5.0 → 2.0.0 |

### Commit Message Format

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

**Types:** `feat`, `fix`, `data`, `docs`, `style`, `refactor`, `ci`, `meta`, `seo`

**Examples:**
```
feat(device-calc): Add SATA expansion support
fix(seed-finder): Correct pagination edge case
data(store): Add missing router specs (gamers2000)
docs: Update CLAUDE.md session state
ci: Add sitemap generation workflow
seo: Add meta tags to all HTML files
```

### Attribution Pipeline

When community members contribute:

1. **Credit in file header** — Add to Contributors or Bug Reports section
2. **Credit in CONTRIBUTIONS.md** — Add dated entry with details
3. **Credit in credits.html** — Update Greetz count, add to Recent Contributions if notable
4. **Credit in JSON `_meta`** — If data file was modified

### Greetz Counting Rules

**Each of these counts as 1 contribution:**
- Bug report that gets fixed
- Feature suggestion that gets implemented
- Data correction (single item or batch)
- External data contribution (JSON, documentation, etc.)
- Pull request merged

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

### Data Projects

- [ ] **Store Reference Tooltips** — Hover tooltips showing item details + in-game images
  - Requires: 101 screenshots from game, cropped to item images
  - Process: Capture → crop → embed/reference in store-reference.html
  - Blocker: Screenshots not yet captured

- [ ] **In-Game Wiki Mirror** *(moved to [tni-wiki-harvester](https://github.com/salvo-praxis/tni-wiki-harvester))*
  - Goal: Extract wiki text for Claude context when building tools
  - Problem: Wiki text is not copy-able, entries require scrolling
  - Process:
    1. Manually screenshot each wiki entry (scroll, screenshot, repeat)
    2. Save screenshots in folders named by entry (e.g., `screenshots/Firewalls/`)
    3. Run `stitch.bat` to vertically stitch images per folder → one long image per entry
    4. Upload stitched images to Claude for transcription (see `CLAUDE.md` in tni-wiki-harvester)
    5. Output: Markdown files with `[IMAGE:]` and `[ANIMATED:]` placeholders
  - Blocker: Screenshots not yet captured

### Data Files

- [x] **tni-proposals.json** — Complete proposals catalog (30 proposals, 7 categories)
  - Added by AlinaNova (PROPOSALS_REFERENCE.md), converted to JSON by Salvo Praxis

### Device Calculator

- [x] Config menu: auto-prune, refurb toggle, warranty/traversals/power display *(completed & committed)*

### Seed Finder

- [x] Paginate results *(completed & committed)*
- [x] Config menu: seeds per page *(completed & committed)*
- [x] Spoiler Prevention mode *(completed 2025-12-15, v1.3.0)*

### General

- [x] Relative links where applicable *(completed & committed)*
- [x] HTML counterparts should link to HTML versions *(completed & committed)*
- [x] `tni-toolkit.zip` download link should be local `./tni-toolkit.zip` *(completed 2025-12-16)*
- [x] Fix conditional backlinks for archive.org *(completed 2025-12-16 — config toggle, simplified logic)*
- [x] Standardize GitHub icon (SVG) in index.html, device-calculator, seed-finder *(completed 2025-12-16)*
- [x] Standardize GitHub icon (SVG) in remaining 9 files *(completed 2025-12-17)*
- [x] Update og:image meta tags in remaining 9 files *(completed 2025-12-17)*

### Automation

- [x] YAML workflow: Build ZIP and FTP deploy *(completed & committed)*
- [x] YAML workflow: Auto-generate sitemap *(completed 2025-12-15, updated 2025-12-16 v1.2.0)*
- [x] YAML workflow: Archive to Software Heritage *(completed 2025-12-15, updated 2025-12-16 — manual only)*
- [x] YAML workflow: Archive to Wayback Machine *(completed 2025-12-15, updated 2025-12-16 — daily + manual)*
- [x] YAML workflow: Generate OG preview images *(completed 2025-12-16, v1.0.1)*
- [x] Sitemap includes tni-toolkit.zip for archive.org *(completed 2025-12-16)*

### SEO

- [x] Add sitemap.xml *(completed 2025-12-15)*
- [x] Add robots.txt *(completed 2025-12-15)*
- [x] Add meta tags to all HTML files *(completed 2025-12-15)*
- [x] Register with Google Search Console *(completed 2025-12-15)*
- [x] Register with Bing Webmaster Tools *(completed 2025-12-15)*
- [x] Archive.org Wayback Machine *(completed 2025-12-15)*
- [x] Submit to Software Heritage *(completed 2025-12-15 — both repos verified)*
- [x] Add Software Heritage badge to README *(completed 2025-12-15)*
- [x] Auto-archive to Wayback Machine workflow *(completed 2025-12-15, updated 2025-12-16 — daily schedule)*
- [x] Auto-generate OG preview images workflow *(completed 2025-12-16)*
- [x] Per-page og:image in index.html, device-calculator, seed-finder *(completed 2025-12-16)*
- [x] Per-page og:image in remaining 9 files *(completed 2025-12-17)*
- [ ] Add Schema markup (JSON-LD) to HTML files *(optional enhancement — requires new session)*
- [ ] Write Steam Guide *(future — high-value backlink, wiki transcription will help)*

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
