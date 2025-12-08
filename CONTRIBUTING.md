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

All data files use this header format:

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
      "v1.0.1: Description of what was fixed"
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
4. **Log corrections** — Add to `corrections` array with version prefix
5. **Track suggestions** — Use `future_additions` for community ideas not yet implemented

### Version Numbering

- `1.0.0` → `1.0.1` — Corrections, typo fixes
- `1.0.1` → `1.1.0` — New data additions
- `1.1.0` → `2.0.0` — Structure changes (rare, coordinate first)

---

## Tool Development Guidelines

### Architecture

All tools are **standalone HTML files**:
- Single `.html` file with embedded CSS and JS
- No external dependencies (works offline)
- Data embedded directly in the file
- Follows the [style guide](docs/STYLE_GUIDE.md)

### Before Building

1. Read [CLAUDE.md](CLAUDE.md) for project context
2. Read [docs/STYLE_GUIDE.md](docs/STYLE_GUIDE.md) for styling
3. Look at existing tools for patterns
4. Check if data files exist for what you need

### Checklist

- [ ] Single HTML file in `tools/` directory
- [ ] Matches NOC theme (dark, green/blue accents)
- [ ] Works offline (no fetch requests)
- [ ] Includes standard footer with links
- [ ] Mobile responsive
- [ ] Tested in multiple browsers

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

## Questions?

- Open an issue for questions or discussion
- Check existing issues for similar topics
- Reference the [style guide](docs/STYLE_GUIDE.md) for styling questions

---

## Credits

Contributors are recognized in:
- JSON file `contributors` arrays
- [Credits page](credits.html) on the toolkit site
- This project's heart ❤️

Thank you for helping build tools for the TNI community!
