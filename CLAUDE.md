# TNI Toolkit - Claude Code Context

## Project Overview

Community-built data files and planning tools for **Tower Networking Inc.** by Pocosia Studios.

**Repository:** https://github.com/salvo-praxis/tni-toolkit  
**Live Site:** https://tni-toolkit.salvo.host/

---

## ⚡ SESSION STATE (VOLATILE)

> **This section tracks current work and is cleared after each successful commit.**

### Current Work

**File:** device-calculator.html  
**Starting Version:** v1.7.0  
**Target Version:** v1.8.0  
**Last Commit:** YAML workflow fix (build-zip-and-ftp-deploy-full-repo.yml v1.0.3)

### Changes This Session

- Program throughput metrics (output_uses array, input_uses field)
- Throughput Summary panel (Input/Output/Dynamic Capacity boxes)
- Dynamic capacity calculations (decentro-wallet, decentro-collector)
- SATA behavior split (minimum vs maximize toggles)
- Config menu two-column layout
- Results panel visibility improvements
- File table headers: CPU MEM HDD
- Formula labels: "free mem" / "free hdd"
- Column alignment (42px tick, 16px sep, 40px sec)

### Files Ready for Commit

- `device-calculator.html` (v1.8.0)
- `CLAUDE.md`

### Pending Attributions

| Who | Context | Status |
|-----|---------|--------|
| *(None this session)* | | |

### Next Steps

1. Version bump device-calculator header → v1.8.0
2. Update CONTRIBUTIONS.md
3. Commit: `tool: add program throughput metrics (device-calculator v1.8.0)`

---

## Architecture

All tools are **standalone HTML files** with embedded CSS/JS. No build process, no external dependencies, works offline. Each tool embeds its own data.

```
tni-toolkit/
├── .github/
│   └── workflows/
│       └── build-zip-and-ftp-deploy-full-repo.yml  # CI/CD automation
├── CLAUDE.md              # You are here
├── CONTRIBUTING.md        # Contribution guidelines
├── CONTRIBUTIONS.md       # Contribution history log
├── index.html             # Landing page
├── contributing.html      # Contribution guide (styled)
├── contributions.html     # Contribution history (styled)
├── credits.html           # Credits, sources, greetz
├── README.md              # GitHub readme
├── data/                  # Source JSON datasets
│   ├── tni-store.json     # Equipment catalog
│   ├── tni-programs.json  # Server programs
│   ├── tni-cli-commands.json
│   └── tni-traffic-types.json
├── tools/                 # Standalone HTML tools
│   ├── device-calculator.html
│   └── seed-finder.html
└── docs/
    ├── STYLE_GUIDE.md     # Detailed styling reference
    └── style-guide.html   # HTML version of style guide
```

### When Building New Tools

1. **Read `docs/STYLE_GUIDE.md` first** — Contains complete CSS reference, component patterns, and copy-paste templates
2. **Single HTML file** — All CSS in `<style>`, all JS in `<script>`, data embedded as JS objects
3. **Match the NOC aesthetic** — Dark theme, monospace font, green/blue accents
4. **Include standard footer** — Links to TNI Toolkit and Steam page
5. **Test offline** — Tools must work without network access

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

**YAML Header Fields:**

| Field | Required | Description |
|-------|----------|-------------|
| File | Yes | Path relative to repo root |
| Name | Yes | Human-readable name (for workflows: matches `name:` key) |
| Version | Yes | Semantic version (X.Y.Z) |
| Updated | Yes | Last modified date (YYYY-MM-DD) |
| Part of | Yes | Project name and repo URL |
| Description | Yes | What the file does |
| Contributors | Yes | List of contributors with roles |
| Changelog | Yes | Version history with descriptions |

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
| `tni-cli-commands.json` | Terminal commands, syntax, examples |
| `tni-traffic-types.json` | Network traffic types for firewall/router rules |

---

## Asset Strategy (Images)

### Problem
Some tools (like Store Browser) need item images. Embedding all images as base64 would bloat files to megabytes.

### Solution: Category Placeholders with Graceful Fallback

1. **Create 16 SVG placeholder images** — one per store category, NOC-styled (dark, glowy, minimal)
2. **Embed placeholders as base64** — ~2-3KB each, ~48KB total (acceptable)
3. **Real images in external folder** — `images/store/item-name.png`
4. **Graceful fallback** — if real image fails, show category placeholder

### Store Categories (16 total)

| Category | Placeholder Style |
|----------|------------------|
| `network_switches` | Switch icon with ports |
| `servers` | Server/rack unit |
| `routers` | Globe/routing icon |
| `firewalls_and_taps` | Shield icon |
| `media_converters_and_repeaters` | Converter/arrows |
| `decentro_rigs` | Mining rig |
| `peripherals` | Generic device |
| `ups_and_surge_protection` | Battery/power |
| `power_expanders` | Lightning bolt |
| `power_cables` | Power plug |
| `network_cables` | Cable/connector |
| `cabling_tools` | Wrench/tool |
| `racks_and_shelving` | Rack frame |
| `tower_link_sockets` | Tower/signal |
| `debuggers_and_test_devices` | Magnifier/probe |
| `monitoring_displays` | Monitor/screen |

### Implementation Pattern

```javascript
// Embedded category placeholders (base64 SVG)
const PLACEHOLDERS = {
    network_switches: "data:image/svg+xml;base64,PHN2Zy...",
    servers: "data:image/svg+xml;base64,PHN2Zy...",
    routers: "data:image/svg+xml;base64,PHN2Zy...",
    // ... all 16 categories
};

// Fallback handler
function handleImageError(img) {
    const category = img.dataset.category;
    img.src = PLACEHOLDERS[category] || PLACEHOLDERS.peripherals;
}
```

```html
<img src="../images/store/blade5.png" 
     alt="Blade5"
     data-category="network_switches"
     onerror="handleImageError(this)">
```

### Placeholder SVG Style

- 64×64px viewBox
- Dark background: `#161b22` or transparent
- Stroke color: `#58a6ff` (blue) or `#00ff88` (green)
- Minimal, iconic, NOC aesthetic
- No fine detail (looks good at small sizes)

### File Structure for Image-Dependent Tools

```
tni-toolkit/
├── tools/
│   └── store-browser.html    # Placeholders embedded, refs external images
└── images/
    └── store/
        ├── blade5.png
        ├── blade10.png
        └── ... (added over time)
```

Tools work fully without images — placeholders provide visual structure. Real images are progressive enhancement.

---

## Tool Sources & Pipelines

Some tools in this toolkit are **outputs** of external projects with their own development pipelines. These should be traceable to their source repos.

| Tool | Source Repo | Pipeline |
|------|-------------|----------|
| `seed-finder.html` | [tni-seed-harvester](https://github.com/salvo-praxis/tni-seed-harvester) | AHK automation → Tesseract OCR → Python processing → HTML generation |

### Pattern for Pipeline-Generated Tools

If a tool requires its own repo/pipeline:

1. **Create a separate repo** for the pipeline (e.g., `tni-seed-harvester`)
2. **Pipeline produces** the final HTML artifact
3. **Artifact gets copied** to `tni-toolkit/tools/`
4. **Document the source** in this table above
5. **Link back** from the tool's source repo to tni-toolkit

This keeps complex tooling isolated while the toolkit remains a clean collection of standalone HTML files.

---

## Versioning & Attribution Workflow

This section defines how Claude and contributors manage versions, attributions, and file synchronization across work sessions.

### Version Bump Rules

Semantic versioning: `MAJOR.MINOR.PATCH`

| Bump | When | Examples |
|------|------|----------|
| **PATCH** (x.y.Z) | Bug fixes, typos, small corrections, config tweaks | "Fixed SATA value", "Typo in label" |
| **MINOR** (x.Y.0) | New features, significant UI changes, new data fields | "Added config menu", "New device category" |
| **MAJOR** (X.0.0) | Breaking changes, complete rewrites, architecture changes | "Redesigned from scratch" |

**Session consolidation**: Multiple changes in one session = one version bump at the highest applicable level.

### Session Management

#### Starting a Session

1. **Declare working version**: State current version from file header (e.g., "Starting from device-calculator v1.5.0")
2. **Review TODO**: Check for pending attributions or work items
3. **Set session scope**: What features/fixes are we targeting?

#### During a Session

- **DO NOT bump version on every edit** — All work is "in progress" on the starting version
- **Track changes** — Update SESSION STATE section as you go
- **Intermediate downloads** — Files downloaded mid-session keep the starting version
- **Note attributions** — If implementing a community suggestion, add to Pending Attributions

#### Ending a Session (Publishing)

When session ends (context limit, natural stopping point, or explicit wrap-up):

1. **Bump version ONCE** based on total scope of changes
2. **Update ALL required files** (see File Update Checklist)
3. **Move attributions** from SESSION STATE → CONTRIBUTIONS.md/credits.html
4. **Generate commit message** following standard format
5. **Clear SESSION STATE** after successful commit

### Attribution Pipeline

#### Stage 1: Suggestion Received
Add to `SESSION STATE > Pending Attributions`:
```markdown
| **@username** | Brief context of what they suggested | Pending |
```

#### Stage 2: Suggestion Implemented  
Update status:
```markdown
| **@username** | Brief context | ✓ Implemented |
```

#### Stage 3: Attribution Applied (End of Session)
Update files in this order:
1. **Source file header** — Add to Contributors, update changelog
2. **CONTRIBUTIONS.md** — Add entry under date/contributor  
3. **contributions.html** — Mirror the MD entry
4. **credits.html** — Update Greetz count + Recent Contributions table

#### Stage 4: Cleanup
After confirming commit, clear completed rows from SESSION STATE.

### File Update Checklist

#### For Bug Fixes (reported by community)
- [ ] Source file: Fix bug, bump PATCH, add reporter to Contributors, update changelog
- [ ] CONTRIBUTIONS.md: Add "Reported: @name / Fixed: Salvo Praxis"
- [ ] contributions.html: Mirror entry
- [ ] credits.html: Update Greetz count, add to Recent Contributions

#### For Feature Suggestions (implemented)
- [ ] Source file: Implement feature, bump MINOR, add suggester to Contributors, update changelog
- [ ] CONTRIBUTIONS.md: Add "Suggested: @name"
- [ ] contributions.html: Mirror entry
- [ ] credits.html: Update Greetz count, add to Recent Contributions

#### For Salvo Praxis Work (via Claude sessions)
- [ ] Source file: Implement changes, bump version, update changelog
- [ ] CONTRIBUTIONS.md: Add entry under Salvo Praxis
- [ ] contributions.html: Mirror entry
- [ ] credits.html: Add to Recent Contributions (no Greetz change)

#### For External PRs/Direct Contributions
- [ ] Source file: Merge changes, bump version, add contributor, update changelog
- [ ] CONTRIBUTIONS.md: Add entry under contributor with "Added:" prefix
- [ ] contributions.html: Mirror entry
- [ ] credits.html: Add/update Greetz count, add to Recent Contributions

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

**Example:**
```
tool: add config menu with warranty/refurbs display (device-calculator v1.7.0)

Changes:
- Config menu with localStorage persistence
- Clear buttons for device/program selection
- Colorized stats (CPU/MEM/HDD/W)
- Warranty and vendor display

Attribution:
- Suggested by @gamers2000 (warranty, refurbs)
- Suggested by @SingingPotBeast (config menu)

Files updated:
- device-calculator.html (v1.7.0)
- CONTRIBUTIONS.md
- contributions.html (v1.2.1)
- credits.html (v1.6.1)
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

COMMIT PREFIX: data: | tool: | fix: | docs: | ci: | style: | meta:

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

- [ ] **tni-proposals.json** — Proposal prerequisites data:
  - `rip` command: 7 routers before chance of proposal
  - `vmconf` command: 5 servers before chance of proposal

### Seed Finder

- [ ] Paginate results
- [ ] Config menu: seeds per page (increments of 25)

### General

- [ ] Relative links where applicable
- [ ] HTML counterparts should link to HTML versions (not GitHub MD)
- [ ] `tni-toolkit.zip` download link should be relative

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
