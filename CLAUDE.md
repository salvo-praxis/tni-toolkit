# TNI Toolkit - Claude Code Context

## Project Overview

Community-built data files and planning tools for **Tower Networking Inc.** by Pocosia Studios.

**Repository:** https://github.com/salvo-praxis/tni-toolkit  
**Live Site:** https://tni-toolkit.salvo.host/

## Architecture

All tools are **standalone HTML files** with embedded CSS/JS. No build process, no external dependencies, works offline. Each tool embeds its own data.

```
tni-toolkit/
├── CLAUDE.md              # You are here
├── CONTRIBUTING.md        # Contribution guidelines (MD for GitHub)
├── CONTRIBUTIONS.md       # Running contribution history (MD for GitHub)
├── index.html             # Landing page (v1.3.0)
├── contributing.html      # Contribution guide (v1.2.0)
├── contributions.html     # Contribution history (v1.1.0, pairs with CONTRIBUTIONS.md)
├── credits.html           # Credits, sources, greetz (v1.5.0)
├── README.md              # GitHub readme
├── LICENSE                # MIT License
├── data/                  # Source JSON datasets
│   ├── tni-store.json         # Equipment catalog (v1.1.0)
│   ├── tni-programs.json      # Server programs (v1.1.1)
│   ├── tni-cli-commands.json  # CLI commands (v1.1.0)
│   └── tni-traffic-types.json # Traffic types (v1.0.0)
├── tools/                 # Standalone HTML tools
│   ├── device-calculator.html  # Device compatibility calculator (v1.5.0)
│   └── seed-finder.html        # Starting proposal seed finder (v1.1.0)
└── docs/
    ├── STYLE_GUIDE.md     # Detailed styling reference (MD for GitHub)
    └── style-guide.html   # Style guide (styled, pairs with STYLE_GUIDE.md)
```

## When Building New Tools

1. **Read `docs/STYLE_GUIDE.md` first** — Contains complete CSS reference, component patterns, and copy-paste templates
2. **Single HTML file** — All CSS in `<style>`, all JS in `<script>`, data embedded as JS objects
3. **Include HTML header comment** — Version, contributors, changelog (see format below)
4. **Match the NOC aesthetic** — Dark theme, monospace font, green/blue accents
5. **Include standard footer** — Links to TNI Toolkit (.io site), GitHub, and Steam page
6. **Include conditional back link** — See pattern below
7. **Test offline** — Tools must work without network access

## HTML File Header Format

Every HTML file includes a standardized header comment:

```html
<!--
╔══════════════════════════════════════════════════════════════════════════════╗
║  TNI Toolkit - [Page/Tool Name]                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  Version: X.Y.Z                                                              ║
║  Updated: YYYY-MM-DD                                                         ║
║  Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)          ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  Description:                                                                ║
║    Brief description of the file's purpose.                                  ║
║                                                                              ║
║  Contributors:                                                               ║
║    - Salvo Praxis (original author)                                          ║
║    - Claude (Anthropic)                                                      ║
║    - [Other contributors as appropriate]                                     ║
║                                                                              ║
║  Changelog:                                                                  ║
║    X.Y.Z - Most recent change description                                    ║
║    X.Y.Z - Previous change description                                       ║
╚══════════════════════════════════════════════════════════════════════════════╝
-->
```

## Tool Navigation Patterns

### index.html Tool Cards

Each tool card has three buttons:
- **▶ Launch** — Opens tool in same tab (users can right-click or ctrl+click for new tab)
- **📄 Source** — Links to GitHub file view (`target="_blank"`)
- **💾 Download** — Native `<a download>` on salvo.host; fetch/blob workaround on GitHub Pages

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
    const hostname = window.location.hostname;
    const isSalvoHost = hostname.includes('salvo.host');
    const isGitHubPages = hostname.includes('github.io');
    const fromToolkit = new URLSearchParams(window.location.search).get('from') === 'toolkit';
    const hasIndexReferrer = document.referrer.includes('index.html') || 
                             document.referrer.includes('tni-toolkit');
    const isHttp = window.location.protocol.startsWith('http');
    
    if (isSalvoHost || fromToolkit || hasIndexReferrer) {
        backLink.classList.add('visible');
        backLink.href = '../index.html';
    } else if (isGitHubPages) {
        backLink.classList.add('visible');
        backLink.href = 'https://salvo-praxis.github.io/tni-toolkit/';
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
| tni-toolkit.salvo.host (primary) | ✅ Shows (relative URL) |
| GitHub Pages (vacation home) | ✅ Shows (absolute URL) |
| Launched from index.html (local/hosted) | ✅ Shows (query param) |
| Bookmarked on hosted site | ✅ Shows (fetch succeeds) |
| Standalone downloaded file | ❌ Hidden (no param, fetch blocked) |

CSS for back link:
```css
.back-link {
    display: none;
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

```css
.header {
    text-align: center;
    padding: 40px 0 30px;
    border-bottom: 1px solid #30363d;
    margin-bottom: 30px;
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

**Color scheme:**
- Index/Credits/Contributing: TNI (green `#00ff88`) + TOOLKIT (blue `#58a6ff`)
- Tools: TNI (blue `#58a6ff`) + APP NAME (green `#00ff88`)

---

## Change Pipeline

### Files That Need Updates

| Change Type | Files to Update |
|-------------|-----------------|
| **Tool HTML change** | Tool file header, CONTRIBUTIONS.md, contributions.html, credits.html (if notable), COMMIT_MESSAGE.txt |
| **Page HTML change** | Page file header, CONTRIBUTIONS.md, contributions.html, COMMIT_MESSAGE.txt |
| **New contributor** | credits.html (Contributors list + Recent Contributions table), CONTRIBUTIONS.md, contributions.html |
| **Bug fix (reporter + fixer)** | credits.html (split credit in table), CONTRIBUTIONS.md (both names), tool changelog ("thanks [reporter]!") |
| **Data file change** | JSON file (`_meta`), CONTRIBUTIONS.md, COMMIT_MESSAGE.txt |

### Version Bump Rules

**File versions** (in HTML header comments):
- Patch (1.0.0 → 1.0.1): Bug fixes, typos, minor CSS tweaks
- Minor (1.0.1 → 1.1.0): New features, significant changes
- Major (1.1.0 → 2.0.0): Breaking changes, major redesign

**Toolkit version** (footer badges): Only bump on releases, stays consistent across all files.

### HTML File Header Updates

When changing an HTML file, update:
```
║  Version: X.Y.Z        ← bump appropriately
║  Updated: YYYY-MM-DD   ← today's date
...
║  Changelog:
║    X.Y.Z - Brief description   ← add new entry at top
```

### Attribution Pipeline

When adding contributions:

1. **CONTRIBUTIONS.md** — Add entry under current date:
   ```markdown
   ## YYYY-MM-DD
   
   ### Contributor Name
   - `filename` vX.Y.Z — Description
   ```
   - Order: Primary contributor first, then others alphabetically
   - For bug fixes: Reporter and Fixer get separate entries

2. **contributions.html** — Mirror the MD structure exactly

3. **credits.html** — Two places to update:
   - **Contributors list**: Add name with count badge (or increment existing)
   - **Recent Contributions table**: Add row with version, description, credit
   - For bug fixes: `Reported: <strong>Name</strong><br>Fixed: <strong>Name</strong>`

4. **Tool changelog** (in header): For bug fixes, add "(thanks [reporter]!)"

### Pre-Commit Checklist

```
□ HTML header Version matches changelog top entry
□ HTML header Updated is today's date
□ HTML header Changelog has new entry
□ CONTRIBUTIONS.md has entry for all changes
□ contributions.html mirrors CONTRIBUTIONS.md
□ credits.html updated (Contributors list + Recent Contributions table)
□ credits.html table in correct order (newest first)
□ COMMIT_MESSAGE.txt summarizes changes
□ No version gaps (1.0 → 1.2 without 1.1)
□ Footer toolkit version unchanged (unless release)
```

---

## Contributors

| Contributor | Contributions |
|-------------|---------------|
| Salvo Praxis | Project lead, original tools, data collection |
| Claude (Anthropic) | AI development partner, code generation |
| AlinaNova21 | Device calculator overhaul, network device data |
| Chaotic Crumb | ICC sata_slots fix, firmware data |
| Singing Pot Beast | ICC sata_slots report |
| gamers2000 | Firmware programs suggestion |
| Crona | Future additions suggestions |
| Kurtchen | SATA storage bug report |
| Блинчик | Community contributions |

---

## Links

- [Style Guide](docs/STYLE_GUIDE.md) — Detailed CSS reference
- [Contributing](CONTRIBUTING.md) — How to contribute
- [Contributions](CONTRIBUTIONS.md) — Running contribution history
- [Credits](credits.html) — Sources, contributors, greetz
- [TNI on Steam](https://store.steampowered.com/app/2939600/Tower_Networking_Inc/)
- [TNI Discord](https://discord.com/invite/nNKRMjDhf2) — Community

---

## Working with Claude

### Starting a Fresh Session

Provide Claude with:
1. **CLAUDE.md** — Project context, file structure, patterns
2. **CONTRIBUTIONS.md** — Recent change history
3. **Specific files** being modified
4. **Link to GitHub repo** — For fetching latest if needed

### Tips

- **Be specific** — Reference exact files and line numbers
- **Iterate small** — One feature at a time, commit often
- **Reference existing files** — "Use the same pattern as device-calculator"
- **End-of-session cleanup** — Verify all headers, contributions, and credits updated

---

## Recent Session Notes

### 2025-12-10: Device Calculator v1.4.0 → v1.5.0

**v1.4.0:**
- Program type filter dropdown (All/Producers/Converters/Storage/Firmware)
- Device category dividers when "All Devices" selected
- Program output/needs on separate lines with ←/→ arrows
- Click-to-deselect on devices, excluded refurb devices

**v1.4.1 bugfix:**
- Fixed SATA storage: +6 → +4 (Reported: Kurtchen, Fixed: Salvo Praxis)

**v1.5.0:**
- SATA stepper control (−/+ buttons)
- Auto-adjusts to program needs with manual override
- NOC-themed button styling

**Also:** Removed build-zip.ps1 and all references

### 2025-12-09: UX Polish & Standardization

- Header/footer standardization across all pages
- Conditional back link with `?from=toolkit` param
- Download button fixes for GitHub Pages

### 2025-12-08: AlinaNova21 PR Integration

- Device calculator v1.2.0 overhaul
- Network device data added to tni-store.json
- File renamed: server-calculator → device-calculator
