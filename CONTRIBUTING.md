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

## File Header Standards

All project files include standardized headers for version tracking, attribution, and changelog.

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

**JSON `_meta` Fields:**

| Field | Required | Description |
|-------|----------|-------------|
| game | Yes | Always "Tower Networking Inc." |
| dataset | Yes | Identifier for the dataset (e.g., "programs", "store") |
| version | Yes | Semantic version (X.Y.Z) |
| last_updated | Yes | Last modified date (YYYY-MM-DD) |
| description | Yes | What this dataset contains |
| sources | No | Array of data sources (in-game, wiki, etc.) |
| contributors | Yes | Array of contributor names/handles |
| corrections | No | Array of data corrections made |
| future_additions | No | Array of planned additions |

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

**HTML Header Fields:**

| Field | Required | Description |
|-------|----------|-------------|
| Tool Name | Yes | Human-readable name of the tool |
| Version | Yes | Semantic version (X.Y.Z) |
| Updated | Yes | Last modified date (YYYY-MM-DD) |
| Part of | Yes | Always "TNI Toolkit" with GitHub URL |
| Description | Yes | What the tool does |
| Contributors | Yes | List of contributors with roles |
| Changelog | Yes | Version history with descriptions |

### YAML Header Format

YAML configuration files (GitHub Actions, CI/CD, etc.) use comment headers:

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

### Python Header Format

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

**Python Header Fields:**

| Field | Required | Description |
|-------|----------|-------------|
| Shebang | Yes | `#!/usr/bin/env python3` |
| Script Name | Yes | Human-readable name of the script |
| File | Yes | Path relative to repo root |
| Version | Yes | Semantic version (X.Y.Z) |
| Updated | Yes | Last modified date (YYYY-MM-DD) |
| Description | Yes | What the script does |
| Contributors | Yes | List of contributors with @handles and roles |
| Changelog | Yes | Version history with descriptions |

### Shell Scripts (Bash/PowerShell)

Shell scripts use comment headers:

**Bash:**
```bash
#!/bin/bash
# ============================================================================
# TNI Toolkit - [Script Name]
# File: [path/to/script.sh]
# Version: X.Y.Z
# Updated: YYYY-MM-DD
# Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
# Description:
#   Brief description of what this script does.
# Contributors:
#   - Name (@handle) - contribution type
# Changelog:
#   X.Y.Z - Description of changes
# ============================================================================
```

**PowerShell:**
```powershell
<#
============================================================================
TNI Toolkit - [Script Name]
File: [path/to/script.ps1]
Version: X.Y.Z
Updated: YYYY-MM-DD
Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
Description:
    Brief description of what this script does.
Contributors:
    - Name (@handle) - contribution type
Changelog:
    X.Y.Z - Description of changes
============================================================================
#>
```

**Shell Script Header Fields:**

| Field | Required | Description |
|-------|----------|-------------|
| Shebang | Yes | `#!/bin/bash` for Bash; none for PowerShell |
| Script Name | Yes | Human-readable name of the script |
| File | Yes | Path relative to repo root |
| Version | Yes | Semantic version (X.Y.Z) |
| Updated | Yes | Last modified date (YYYY-MM-DD) |
| Description | Yes | What the script does |
| Contributors | Yes | List of contributors with @handles and roles |
| Changelog | Yes | Version history with descriptions |

---

## When Editing Data Files

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
- [ ] Includes standard footer with links
- [ ] Mobile responsive
- [ ] Tested in multiple browsers

### Style Guide Highlights

- **Custom Dropdown**: Use the Custom Dropdown pattern from `STYLE_GUIDE.md` instead of native `<select>` elements (they don't style well on dark themes)
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
- `ci: add GitHub Actions workflow for deployment`

---

## Questions?

- Open an issue for questions or discussion
- Check existing issues for similar topics
- Reference the [style guide](docs/STYLE_GUIDE.md) for styling questions

---

## Credits

Contributors are recognized in:
- HTML file header comments
- YAML file header comments
- JSON file `contributors` arrays
- [Credits page](credits.html) on the toolkit site
- This project's heart ❤️

Thank you for helping build tools for the TNI community!
