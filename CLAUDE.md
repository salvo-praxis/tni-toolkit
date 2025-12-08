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
├── index.html             # Landing page (GitHub Pages)
├── contributing.html      # Contribution guide (styled)
├── credits.html           # Credits, sources, greetz
├── README.md              # GitHub readme
├── data/                  # Source JSON datasets
│   ├── tni-store.json     # Equipment catalog
│   ├── tni-programs.json  # Server programs
│   ├── tni-cli-commands.json
│   └── tni-traffic-types.json
├── tools/                 # Standalone HTML tools
│   ├── server-calculator.html
│   └── seed-finder.html
└── docs/
    └── STYLE_GUIDE.md     # Detailed styling reference
```

## When Building New Tools

1. **Read `docs/STYLE_GUIDE.md` first** — Contains complete CSS reference, component patterns, and copy-paste templates
2. **Single HTML file** — All CSS in `<style>`, all JS in `<script>`, data embedded as JS objects
3. **Match the NOC aesthetic** — Dark theme, monospace font, green/blue accents
4. **Include standard footer** — Links to TNI Toolkit and Steam page
5. **Test offline** — Tools must work without network access

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

## Data Files

Tools should embed data directly. Source files in `data/`:

| File | Use For |
|------|---------|
| `tni-store.json` | Equipment specs, prices, power draw |
| `tni-programs.json` | Program requirements, I/O, dependencies |
| `tni-cli-commands.json` | Terminal commands, syntax, examples |
| `tni-traffic-types.json` | Network traffic types for firewall/router rules |

### Data Attribution Standard

All JSON files should include source attribution in `_meta`:

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
- [x] Server/Program Compatibility Calculator
- [x] Starting Proposal Seed Finder

## Links

- [Style Guide](docs/STYLE_GUIDE.md) — Detailed CSS reference
- [Contributing](CONTRIBUTING.md) — How to contribute (markdown)
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

After each working chunk, commit. Git is your safety net.

### When Things Break

Don't say: *"It's broken, fix it"*

Say: *"The click handler on line 145 isn't firing. Check the event binding."*

Specific symptoms → faster fixes → less thrashing.

### Reset to Source of Truth

If confused: *"Stop. Read CLAUDE.md and docs/STYLE_GUIDE.md again. Then look at the current state of [file]."*
