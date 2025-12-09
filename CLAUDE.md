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
├── data/                  # Source JSON datasets
│   ├── tni-store.json     # Equipment catalog (v1.1.0)
│   ├── tni-programs.json  # Server programs (v1.1.1)
│   ├── tni-cli-commands.json
│   └── tni-traffic-types.json
├── tools/                 # Standalone HTML tools
│   ├── device-calculator.html  # Device compatibility calculator (v1.2.0)
│   └── seed-finder.html
└── docs/
    └── STYLE_GUIDE.md     # Detailed styling reference
```

## When Building New Tools

1. **Read `docs/STYLE_GUIDE.md` first** — Contains complete CSS reference, component patterns, and copy-paste templates
2. **Single HTML file** — All CSS in `<style>`, all JS in `<script>`, data embedded as JS objects
3. **Include HTML header comment** — Version, contributors, changelog (see format below)
4. **Match the NOC aesthetic** — Dark theme, monospace font, green/blue accents
5. **Include standard footer** — Links to TNI Toolkit and Steam page
6. **Test offline** — Tools must work without network access

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

**Documentation updated:**
- All HTML files now have box-drawing header comments
- `contributing.html` documents HTML header format
- `STYLE_GUIDE.md` includes Custom Dropdown pattern
- `README.md` updated with new tool name and contributors
