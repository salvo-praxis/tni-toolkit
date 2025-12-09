# Contributing to TNI Toolkit

Thanks for your interest in contributing! This project thrives on community input.

## Ways to Contribute

### 🐛 Report Issues
- Data errors (wrong prices, specs, missing items)
- Tool bugs or UI problems
- Broken links or typos

### 📊 Add or Update Data
- New equipment from game updates
- Missing programs or CLI commands
- Traffic types or network mechanics
- Corrections to existing data

### 🛠️ Build Tools
- Pick something from the [roadmap](CLAUDE.md#roadmap)
- Follow the [style guide](docs/STYLE_GUIDE.md)
- Create standalone HTML files

### 📸 Contribute Assets
- Equipment screenshots/icons from the game
- UI reference images
- Workflow diagrams

---

## Data File Guidelines

### JSON Structure

All data files use this header format in `_meta`:

```json
{
  "_meta": {
    "game": "Tower Networking Inc.",
    "dataset": "dataset-name",
    "version": "1.0.0",
    "last_updated": "YYYY-MM-DD",
    "description": "What this dataset contains",
    "notes": "Optional general notes about the dataset",
    "sources": [
      {
        "name": "In-game observation",
        "notes": "Data collected directly from in-game interfaces"
      },
      {
        "name": "Discord Community",
        "notes": "Data additions, corrections, and suggestions made by members of the discord community"
      },
      {
        "name": "External Source Name",
        "url": "https://...",
        "author": "@handle",
        "retrieved": "YYYY-MM-DD",
        "notes": "Any relevant notes"
      }
    ],
    "contributors": [
      "Salvo Praxis",
      "Claude (Anthropic)",
      "Your Name or Handle"
    ],
    "corrections": [
      {
        "version": "1.0.1",
        "correction": "Description of what was fixed",
        "reported_by": "Who reported it",
        "corrected_by": "Who fixed it"
      }
    ],
    "future_additions": [
      {
        "suggestion": "Brief description of suggested addition",
        "details": "More context about the suggestion",
        "suggested_by": "Name or Handle"
      }
    ]
  }
}
```

### When Editing Data Files

1. **Maintain structure** — Don't change field names or nesting
2. **Update metadata**:
   - Bump `version` (patch for fixes, minor for additions)
   - Update `last_updated` to today
   - Add yourself to `contributors` if not already listed
3. **Add sources** — If data came from somewhere, credit it
4. **Log corrections** — Add to `corrections` array with structured entry
5. **Track suggestions** — Use `future_additions` for community ideas not yet implemented

### Version Numbering

| Change | Example |
|--------|---------|
| Corrections, typo fixes | `1.0.0` → `1.0.1` |
| New data additions | `1.0.1` → `1.1.0` |
| Structure changes (rare) | `1.1.0` → `2.0.0` |

---

## Tool Development Guidelines

### Architecture

All tools are **standalone HTML files**:
- Single `.html` file with embedded CSS and JS
- No external dependencies (works offline)
- Data embedded directly in the file
- Follows the [style guide](docs/STYLE_GUIDE.md)

### HTML Header Format

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

This mirrors the `_meta` format in JSON files — version tracking, attribution, and changelog in one place.

### Before Building

1. Read [CLAUDE.md](CLAUDE.md) for project context
2. Read [docs/STYLE_GUIDE.md](docs/STYLE_GUIDE.md) for styling
3. Look at existing tools for patterns (especially `device-calculator.html`)
4. Check if data files exist for what you need

### Checklist

- [ ] Single HTML file in `tools/` directory
- [ ] Includes HTML header comment (version, contributors, changelog)
- [ ] Matches NOC theme (dark, green/blue accents)
- [ ] Works offline (no fetch requests)
- [ ] Includes standardized header (`padding: 40px 0 30px`, h1 margin `0 0 8px 0`)
- [ ] Includes conditional back link (shows when launched from toolkit)
- [ ] Includes standardized footer (links, charm line, version/license badges)
- [ ] Mobile responsive
- [ ] Tested in multiple browsers

### Style Guide Highlights

- **Headers**: Use standardized header CSS from `STYLE_GUIDE.md` — consistent padding, spacing, color scheme
- **Back Link**: Conditional "← Back to Toolkit" button in header (see `STYLE_GUIDE.md` for CSS/JS pattern)
- **Footer**: Three rows — nav links (TNI Toolkit | GitHub | Contributions Log | TNI on Steam), charm line, version/license badges
- **Custom Dropdown**: Use the Custom Dropdown pattern instead of native `<select>` elements (they don't style well on dark themes)
- **Input padding**: Always `10px 12px`
- **Table headers**: Color `#58a6ff`, font-weight `600`
- **Buttons**: Use `.btn-primary` (green) or `.btn-secondary` (blue outline) patterns

### Pipeline-Generated Tools

If your tool needs its own build pipeline:

1. Create a separate repo for the pipeline
2. Output a standalone HTML file
3. Copy the artifact to `tni-toolkit/tools/`
4. Document in [CLAUDE.md](CLAUDE.md#tool-sources--pipelines)

Example: [tni-seed-harvester](https://github.com/salvo-praxis/tni-seed-harvester) → `seed-finder.html`

---

## Pull Request Process

1. **Fork** the repository
2. **Create a branch** (`feature/tool-name` or `data/update-store`)
3. **Make changes** following the guidelines above
4. **Test** your changes locally
5. **Submit PR** with a clear description of what changed

### PR Title Format

- `data: add traffic types for firewall rules`
- `tool: add power budget calculator`
- `fix: correct Blade10 power draw in store.json`
- `docs: update contributing guidelines`

---

## Toolkit Releases

The toolkit itself has a version number separate from individual tools and data files. Tools and data get frequent updates from the community; toolkit releases are periodic bundles.

### Versioning

Toolkit uses **semantic versioning**: `vMAJOR.MINOR.PATCH`

| Change Type | Version Bump | Example |
|-------------|--------------|---------|
| Bug fixes, typos, small tweaks | PATCH | `v1.2.0` → `v1.2.1` |
| New tools, features, data files | MINOR | `v1.2.1` → `v1.3.0` |
| Breaking changes, major redesign | MAJOR | `v1.3.0` → `v2.0.0` |

### What Triggers a Release?

- New tool added
- Significant feature additions to existing tools
- Major data file additions or schema changes
- Accumulation of multiple smaller changes

Not every commit needs a release. Day-to-day fixes and small additions stay on `main` until there's enough to bundle.

### Downloads

A `tni-toolkit.zip` file is maintained in the repo root for end users who want to download and run the toolkit locally. It contains user-facing files (tools, HTML pages, license) — no `.md` contributor documentation.

**Download**: [tni-toolkit.zip](https://github.com/salvo-praxis/tni-toolkit/raw/main/tni-toolkit.zip)

### For Maintainers

When updating the ZIP:

1. Update version in `index.html` header comment and footer badge
2. Run `.\build-zip.ps1` from repo root
3. Commit the updated ZIP

---

## Questions?

- Open an issue for questions or discussion
- Check existing issues for similar topics
- Reference the [style guide](docs/STYLE_GUIDE.md) for styling questions

---

## Credits

Contributors are recognized in:
- [Contributions Log](CONTRIBUTIONS.md) — running changelog of all contributions
- HTML file header comments
- JSON file `contributors` arrays
- [Credits page](credits.html) on the toolkit site
- This project's heart ❤️

Thank you for helping build tools for the TNI community!
