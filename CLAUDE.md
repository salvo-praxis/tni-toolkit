# TNI Toolkit - Claude Code Context

## Project Overview

Community-built data files and planning tools for **Tower Networking Inc.** by Pocosia Studios.

**Repository:** https://github.com/salvo-praxis/tni-toolkit  
**Live Site:** https://salvo-praxis.github.io/tni-toolkit/

## Architecture

All tools are **standalone HTML files** with embedded CSS/JS. No build process, no external dependencies, works offline. Each tool embeds its own data.

```
tni-toolkit/
├── CLAUDE.md              # You are here
├── CONTRIBUTING.md        # Contribution guidelines
├── CONTRIBUTIONS.md       # Running contribution history
├── index.html             # Landing page (GitHub Pages)
├── contributing.html      # Contribution guide (styled)
├── credits.html           # Credits, sources, greetz
├── README.md              # GitHub readme
├── LICENSE                # MIT License
├── build-zip.ps1          # ZIP build script (PowerShell)
├── tni-toolkit.zip        # Downloadable toolkit bundle
├── data/                  # Source JSON datasets
│   ├── tni-store.json     # Equipment catalog (v1.1.0)
│   ├── tni-programs.json  # Server programs (v1.1.1)
│   ├── tni-cli-commands.json
│   └── tni-traffic-types.json
├── tools/                 # Standalone HTML tools
│   ├── device-calculator.html  # Device compatibility calculator (v1.2.1)
│   └── seed-finder.html        # Seed finder (v1.1.0)
└── docs/
    └── STYLE_GUIDE.md     # Detailed styling reference
```

## When Building New Tools

1. **Read `docs/STYLE_GUIDE.md` first** — Contains complete CSS reference, component patterns, and copy-paste templates
2. **Single HTML file** — All CSS in `<style>`, all JS in `<script>`, data embedded as JS objects
3. **Include HTML header comment** — Version, contributors, changelog (see format below)
4. **Match the NOC aesthetic** — Dark theme, monospace font, green/blue accents
5. **Include standard footer** — Links to TNI Toolkit (.io site), GitHub, and Steam page
6. **Include conditional back link** — See pattern below
7. **Test offline** — Tools must work without network access

## Tool Navigation Patterns

### index.html Tool Cards

Each tool card has three buttons:
- **▶ Launch** — Opens tool in same tab (users can right-click or ctrl+click for new tab)
- **📄 Source** — Links to GitHub file view (`target="_blank"`)
- **💾 Download** — Uses fetch/blob workaround for forced download

Section header includes **🗂️ Download Toolkit** button linking to GitHub ZIP archive.

### Conditional Back Link

Tools include a "← Back to Toolkit" button that shows only when appropriate:

**index.html Launch links include `?from=toolkit`:**
```html
<a href="tools/device-calculator.html?from=toolkit" class="btn btn-primary">▶ Launch</a>
```

**Tool script checks for the param:**
```javascript
(function() {
    const backLink = document.getElementById('back-to-toolkit');
    const isGitHubPages = window.location.hostname.includes('github.io');
    const fromToolkit = new URLSearchParams(window.location.search).get('from') === 'toolkit';
    const hasIndexReferrer = document.referrer.includes('index.html') || 
                             document.referrer.includes('tni-toolkit');
    const isHttp = window.location.protocol.startsWith('http');
    
    if (isGitHubPages) {
        backLink.classList.add('visible');
        backLink.href = 'https://salvo-praxis.github.io/tni-toolkit/';
    } else if (fromToolkit || hasIndexReferrer) {
        backLink.classList.add('visible');
        backLink.href = '../index.html';
    } else if (isHttp) {
        fetch('../index.html', { method: 'HEAD' })
            .then(response => {
                if (response.ok) {
                    backLink.classList.add('visible');
                    backLink.href = '../index.html';
                }
            })
            .catch(() => {});
    }
})();
```

**Behavior:**

| Scenario | Back Link |
|----------|-----------|
| GitHub Pages (any access) | ✅ Shows (absolute URL) |
| Launched from index.html (local/hosted) | ✅ Shows (query param) |
| Bookmarked on hosted site | ✅ Shows (fetch succeeds) |
| Standalone downloaded file | ❌ Hidden (no param, fetch blocked) |

CSS for back link (styled as secondary button, centered in header):
```css
.back-link {
    display: none;  /* or inline-block for static pages */
    margin-top: 16px;
    color: #58a6ff;
    text-decoration: none;
    font-size: 11px;
    padding: 6px 12px;
    border: 1px solid #30363d;
    border-radius: 4px;
    transition: all 0.15s;
}
.back-link:hover {
    border-color: #58a6ff;
    background: rgba(88, 166, 255, 0.1);
}
.back-link.visible {
    display: inline-block;
}
```

### Standardized Header CSS

All pages use this header format for visual consistency:

```css
.header {
    text-align: center;
    padding: 40px 0 30px;
    border-bottom: 1px solid #30363d;
    margin-bottom: 30px;  /* or 0 for index */
}

h1 {
    color: #00ff88;
    text-shadow: 0 0 20px rgba(0, 255, 136, 0.3);
    margin: 0 0 8px 0;
    font-size: 20px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
}

h1 span { color: #58a6ff; }

.tagline, .subtitle {
    color: #8b949e;
    font-size: 12px;
    margin: 0;
}
```

**Header spacing breakdown:**
```
40px ─── padding-top
TITLE
8px ─── h1 margin-bottom  
Subtitle
16px ─── back-link margin-top
[← Back to Toolkit]
30px ─── padding-bottom
─────── border-bottom
```

**Color scheme:**
- Index/Credits/Contributing: TNI (green `#00ff88`) + TOOLKIT (blue `#58a6ff`)
- Tools: TNI (blue `#58a6ff`) + APP NAME (green `#00ff88`)

HTML placement (inside header, after subtitle):
```html
<div class="header">
    <h1><span>TNI</span> APP NAME</h1>
    <p class="subtitle">Subtitle text</p>
    <a href="../index.html" class="back-link" id="back-to-toolkit">← Back to Toolkit</a>
</div>
```

### Standardized Footer

**Structure:**
```
[Row 1: Navigation Links]
[Row 2: Charm Line - unique per page]
[Row 3: Version & License Badges]
```

**Pages (index, credits, contributing):**
```html
<footer class="footer">
    <div class="footer-links">
        <a href="https://github.com/salvo-praxis/tni-toolkit" target="_blank">GitHub</a>
        <span class="footer-sep">|</span>
        <a href="https://github.com/salvo-praxis/tni-toolkit/blob/main/CONTRIBUTIONS.md" target="_blank">Contributions Log</a>
        <span class="footer-sep">|</span>
        <!-- Hide current page link -->
        <a href="credits.html">Credits & Sources</a>
        <span class="footer-sep">|</span>
        <a href="contributing.html">Contributing</a>
        <span class="footer-sep">|</span>
        <a href="https://store.steampowered.com/app/2939600/Tower_Networking_Inc/" target="_blank">TNI on Steam</a>
    </div>
    <p class="footer-note">Charm line here</p>
    <div class="footer-badges">
        <span class="version-badge">v1.2.0</span>
        <a href="https://github.com/salvo-praxis/tni-toolkit/blob/main/LICENSE" target="_blank" class="license-badge">MIT License — Free to use, modify, and share</a>
    </div>
</footer>
```

**Tools:**
```html
<footer class="site-footer">
    <div class="footer-links">
        <a href="https://salvo-praxis.github.io/tni-toolkit/" target="_blank">TNI Toolkit</a>
        <span class="sep">|</span>
        <a href="https://github.com/salvo-praxis/tni-toolkit" target="_blank">GitHub</a>
        <span class="sep">|</span>
        <a href="https://github.com/salvo-praxis/tni-toolkit/blob/main/CONTRIBUTIONS.md" target="_blank">Contributions Log</a>
        <span class="sep">|</span>
        <a href="https://store.steampowered.com/app/2939600/Tower_Networking_Inc/" target="_blank">TNI on Steam</a>
    </div>
    <p class="footer-note">Made with ❤️ for the TNI community</p>
    <div class="footer-badges">
        <span class="version-badge">v1.2.0</span>
        <a href="https://github.com/salvo-praxis/tni-toolkit/blob/main/LICENSE" target="_blank" class="license-badge">MIT License — Free to use, modify, and share</a>
    </div>
</footer>
```

**Charm lines by page:**
- Index: "Fan project • Tower Networking Inc. by Pocosia Studios" + shoutout
- Credits: (none - badges cover it)
- Contributing: "Made with ❤️ for the TNI community"
- Tools: "Made with ❤️ for the TNI community"

**Badge CSS:**
```css
.footer-badges { margin-top: 12px; }

.version-badge {
    display: inline-block;
    background: rgba(0, 255, 136, 0.1);
    border: 1px solid #30363d;
    color: #8b949e;
    padding: 4px 10px;
    border-radius: 4px;
    font-size: 10px;
    margin-right: 8px;
}

.license-badge {
    display: inline-block;
    background: rgba(88, 166, 255, 0.1);
    border: 1px solid #30363d;
    color: #8b949e;
    padding: 4px 10px;
    border-radius: 4px;
    font-size: 10px;
    text-decoration: none;
    transition: all 0.15s;
}

.license-badge:hover {
    border-color: #58a6ff;
    color: #58a6ff;
}
```

## File Header Formats

### HTML Files

All HTML tools include a comment header **before** `<!DOCTYPE html>`:

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

### JSON Data Files

All JSON files include `_meta` object with attribution:

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

### UI Components

**Native `<select>` elements** don't style well on dark themes. Use the **Custom Dropdown** pattern from `STYLE_GUIDE.md` for category filters and styled dropdowns.

**Input padding**: Always `10px 12px`

**Table headers**: Color `#58a6ff`, font-weight `600`

**Buttons**: Use `.btn-primary` (green) or `.btn-secondary` (blue outline) patterns

## Data Files

Tools should embed data directly. Source files in `data/`:

| File | Version | Use For |
|------|---------|---------|
| `tni-store.json` | 1.1.0 | Equipment specs, prices, power draw, firmware |
| `tni-programs.json` | 1.1.1 | Program requirements, I/O, dependencies |
| `tni-cli-commands.json` | 1.0.0 | Terminal commands, syntax, examples |
| `tni-traffic-types.json` | 1.0.0 | Network traffic types for firewall/router rules |

### Recent Data Updates

**tni-store.json v1.1.0** (2025-12-08)
- Added `cpu`, `memory`, `storage`, `firmware` fields to all network devices
- Switches: bladeos/vlanfirm firmware
- Routers: rtkernel/hakernel firmware  
- Firewalls: firewatcher firmware
- TAPs: wirerat firmware
- Debuggers: netpeeker/dnsspam firmware
- Contributor: AlinaNova21

**tni-programs.json v1.1.1** (2025-12-08)
- Whitespace cleanup
- Contributor: AlinaNova21

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

## Roadmap

### In Progress
- [ ] **CLI Command Builder** — Form-based command generator for NetShell
  - *Blocker: Traffic types data* ✓ Created `tni-traffic-types.json`

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
- [x] **Device Compatibility Calculator** (v1.2.0) — Servers, switches, routers, firewalls, debuggers with category filter, search, sharecode, file table
- [x] **Starting Proposal Seed Finder** — 3,794 seeds, 455 combinations, 100% coverage

## Contributors

| Contributor | Contributions |
|-------------|---------------|
| Salvo Praxis | Project lead, original tools, data collection |
| Claude (Anthropic) | AI development partner, code generation |
| Chaotic Crumb | ICC sata_slots fix, firmware data |
| Singing Pot Beast | ICC sata_slots report |
| gamers2000 | Firmware programs suggestion |
| Crona | Future additions suggestions |
| AlinaNova21 | Device calculator overhaul, network device data |
| Блинчик | Community contributions |

## Links

- [Style Guide](docs/STYLE_GUIDE.md) — Detailed CSS reference (includes Custom Dropdown pattern)
- [Contributing](CONTRIBUTING.md) — How to contribute (markdown)
- [Contributions](CONTRIBUTIONS.md) — Running contribution history
- [Contributing Guide](contributing.html) — How to contribute (styled)
- [Credits](credits.html) — Sources, contributors, greetz
- [TNI on Steam](https://store.steampowered.com/app/2939600/Tower_Networking_Inc/)
- [Pocosia Studios](https://pocosia.com/)
- [TNI Discord](https://discord.com/invite/nNKRMjDhf2) — Community

---

## Change Pipeline

When making changes to the toolkit, follow this pipeline to keep everything consistent.

### Files That Need Updates

| Change Type | Files to Update |
|-------------|-----------------|
| **Tool HTML change** | Tool file, CONTRIBUTIONS.md, COMMIT_MESSAGE.txt |
| **Page HTML change** | Page file, CONTRIBUTIONS.md, COMMIT_MESSAGE.txt |
| **New feature/pattern** | Affected files, STYLE_GUIDE.md, CONTRIBUTIONS.md, COMMIT_MESSAGE.txt |
| **Data file change** | JSON file (`_meta`), CONTRIBUTIONS.md, COMMIT_MESSAGE.txt |
| **Version bump** | HTML header (Version, Updated, Changelog), CONTRIBUTIONS.md |

### Version Bump Rules

**File versions** (in HTML header comments):
- Patch (1.0.0 → 1.0.1): Bug fixes, typos, minor CSS tweaks
- Minor (1.0.1 → 1.1.0): New features, significant changes
- Major (1.1.0 → 2.0.0): Breaking changes, major redesign

**Toolkit version** (footer badges): Only bump on releases, stays consistent across all files.

### HTML File Header Updates

When changing an HTML file, update these fields in the header comment:
```
║  Version: X.Y.Z        ← bump appropriately
║  Updated: YYYY-MM-DD   ← today's date
...
║  Changelog:
║    X.Y.Z - Brief description of changes   ← add new entry at top
```

### Documentation Chain

1. **CONTRIBUTIONS.md** — Add entry under current date/contributor:
   - Version-bumped files: `` `filename` vX.Y.Z — description ``
   - General changes: one-liner description

2. **COMMIT_MESSAGE.txt** — Summarize all changes for git commit

3. **STYLE_GUIDE.md** — If adding new CSS patterns, document them

4. **CLAUDE.md** — Update if:
   - File structure changes
   - New tools added
   - Workflow/pipeline changes
   - Session notes (temporary, consolidate later)

### Pre-Commit Checklist

```
□ HTML header Version matches changelog top entry
□ HTML header Updated is today's date
□ HTML header Changelog has new entry
□ CONTRIBUTIONS.md has entry for all version bumps
□ COMMIT_MESSAGE.txt summarizes changes
□ No version gaps (1.0 → 1.2 without 1.1)
□ No duplicate version entries
□ Footer toolkit version unchanged (unless release)
```

### Starting a Fresh Session

Provide Claude with:
1. **CLAUDE.md** — Project context, file structure, patterns
2. **CONTRIBUTIONS.md** — Recent change history
3. **Specific files** being modified

Claude can then:
- Understand project architecture
- Follow established patterns
- Update all required documentation
- Maintain version consistency

---

## Working with Claude Code

Tips for effective development sessions:

### Be Specific About Scope

Instead of: *"Build a power calculator"*

Say: *"Create `tools/power-calculator.html` following the style guide. It should let users select equipment from tni-store.json and sum up power draw. Use the same panel/card structure as device-calculator."*

### Iterate in Small Chunks

1. "Create the basic HTML structure with header and one panel"
2. "Add the equipment selection grid"
3. "Add the calculation logic"
4. "Add the results display"

If something breaks, you know exactly which step caused it.

### Reference Existing Files

*"Look at `tools/device-calculator.html` and use the same card hover pattern"*

Point to concrete examples rather than abstract descriptions.

### Checkpoint Often

After each working chunk, commit. Git is your safety net.

### When Things Break

Don't say: *"It's broken, fix it"*

Say: *"The click handler on line 145 isn't firing. Check the event binding."*

Specific symptoms → faster fixes → less thrashing.

### Reset to Source of Truth

If confused: *"Stop. Read CLAUDE.md and docs/STYLE_GUIDE.md again. Then look at the current state of [file]."*

---

## Building the Toolkit ZIP

A `tni-toolkit.zip` is maintained in the repo root for users who want to download everything at once.

### Build Script

Run from repo root:
```powershell
.\build-zip.ps1
```

This creates `tni-toolkit.zip` containing only user-facing files:
- `tools/` — all standalone tools
- `index.html` — landing page
- `contributing.html` — contribution guide
- `credits.html` — attribution
- `LICENSE`

**Excluded:** Everything else — `data/`, `docs/`, all `.md` files, build scripts, IDE files. These are for contributors who clone the repo, not end users.

### When to Update

Rebuild the ZIP when:
- Adding new tools
- Significant feature additions
- Before announcing updates to the community

Don't forget to update the version badge in `index.html` footer.

---

## Recent Session Notes

### 2025-12-08: AlinaNova21 PR Integration

**Merged contributions:**
- `device-calculator.html` v1.2.0 — Major overhaul adding all device types, category filter, search, sharecode system, file table display
- `tni-store.json` v1.1.0 — Added firmware/cpu/memory/storage to all network devices
- `tni-programs.json` v1.1.1 — Whitespace cleanup

**Style guide alignment applied:**
- Replaced native `<select>` with Custom Dropdown pattern
- Standardized input padding to `10px 12px`
- Updated table headers to `#58a6ff` with font-weight 600
- Added `.btn-secondary` button styling

**File renamed:** `server-calculator.html` → `device-calculator.html`

### 2025-12-09: UX Polish & Standardization

**Header standardization (all pages):**
- Consistent padding: `40px 0 30px`
- H1 margin: `0 0 8px 0`, subtitle margin: `0`
- Back button: `margin-top: 16px`, matches credits/contributing styling
- Color scheme: Tools use TNI (blue) + APP NAME (green); Pages use TNI (green) + TOOLKIT (blue)

**Footer standardization (all pages):**
- Row 1: GitHub | Contributions Log | [page links] | TNI on Steam
- Row 2: Charm line (unique per page)
- Row 3: Version badge + MIT License badge (links to LICENSE file)

**Navigation:**
- Launch buttons open in same tab (removed `target="_blank"`)
- `?from=toolkit` param enables conditional back button
- Download buttons use fetch/blob workaround for forced download

**Tool updates:**
- Seed Finder renamed to "Starting Proposal Seed Finder"
- Subtitle merged: "Select Proposals • 455 Combinations • 3794 Seeds"
- Both tools: `max-width: 1200px` container, `line-height: 1.6` on body

**Build system:**
- Added `build-zip.ps1` PowerShell script
- ZIP contains: `tools/`, `index.html`, `contributing.html`, `credits.html`, `LICENSE`

**Pending:**
- Update `tni-seed-harvester` Python generator to match new seed-finder template
