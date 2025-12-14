# Contribution History

Running log of all contributions to the TNI Toolkit. For guidelines on contributing, see [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 2025-12-13

### AlinaNova
- `tni-proposals.json` v1.0.0 — Created comprehensive proposals reference documentation (PROPOSALS_REFERENCE.md) with all 30 in-game proposals, prerequisites, costs, and effects

### Salvo Praxis
- `tni-proposals.json` v1.0.0 — Converted AlinaNova's proposals reference to JSON format with _meta headers
- `docs/proposals-reference.html` v1.0.0 — HTML proposals reference with ToC and navigation
- `docs/programs-reference.html` v1.0.0 — HTML programs reference (25 programs, 10 categories)
- `docs/cli-reference.html` v1.0.0 — HTML CLI commands reference (24 commands with syntax/examples)
- `docs/traffic-types-reference.html` v1.0.0 — HTML traffic types reference (14 types, firewall presets)
- `docs/store-reference.html` v1.0.0 — HTML store reference (101 items, 16 categories)
- `index.html` v1.5.0 — Expanded Quick Reference with all HTML reference pages
- `device-calculator.html` v1.8.0 — Program throughput metrics (output_uses, input_uses), Throughput Summary panel (Input/Output/Dynamic Capacity), dynamic capacity calculations, SATA behavior split (minimum vs maximize), config menu two-column layout, results panel visibility improvements
- `CLAUDE.md` — Restructured with volatile SESSION STATE section, preserved permanent documentation
- `README.md` — Updated Device Calculator description with v1.8 features, simplified JSON Structure section

---

## 2025-12-12

### Salvo Praxis
- `device-calculator.html` v1.7.0 — Config menu with granular toggles (vendor, warranty, power, T/s, TPT, TPS, tooltip, refurbs, auto-SATA), traversal metrics with calculations, comprehensive hover tooltip, colorized stats, localStorage persistence, clear buttons, Decentro Rigs category, refurbished devices data
- `tni-store.json` v1.2.0 — Added `compatible_programs` field to all 47 devices with placeholder examples
- `style-guide.html` v1.5.0 — Collapsible UI components, syntax highlighting, Master JS section, tooltip dependencies
- `credits.html` v1.6.1 — Updated contributor counts, consolidated entries
- `contributions.html` v1.2.1 — Consolidated entries, added attributions
- `CLAUDE.md` — Added versioning workflow, attribution pipeline, commit message format

### gamers2000
- `device-calculator.html` v1.7.0 — Suggested warranty display and refurbished devices features

### Singing Pot Beast
- `device-calculator.html` v1.7.0 — Suggested auto-prune/config menu feature

---

## 2025-12-10

### Salvo Praxis
- `device-calculator.html` v1.5.0 — SATA stepper control (−/+ buttons), auto-adjusts to program needs with manual override
- `device-calculator.html` v1.4.1 — Fixed SATA storage value
- `device-calculator.html` v1.4.0 — Smart SATA expansion (x/y slots, charges only what's needed), program type filter, device category dividers, needs/output on separate lines with ←/→ arrows, click-to-deselect, sharecode fixes, excluded refurbs

### Kurtchen
- `device-calculator.html` v1.4.1 — Reported SATA storage bug (was +6, should be +4)

---

## 2025-12-09

### Salvo Praxis
- `index.html` v1.3.0 — Header/footer standardization, launch opens same tab, download buttons
- `seed-finder.html` v1.1.0 — Renamed to "Starting Proposal Seed Finder", merged subtitle, header/footer standardization
- `device-calculator.html` v1.3.0 — Header/footer standardization, container max-width
- `credits.html` v1.4.0 — Footer standardization, table column width fix
- `contributing.html` v1.2.0 — Footer standardization with badges
- `contributions.html` v1.0.0 — New HTML version of CONTRIBUTIONS.md
- `docs/style-guide.html` v1.0.0 — New HTML version of STYLE_GUIDE.md
- `STYLE_GUIDE.md` v1.1 — Added Page Layout Patterns (header, footer, back link CSS)
- Conditional back button: moved inside header, query param detection
- Navigation: launch opens same tab, download native on salvo.host (fetch/blob on GitHub Pages)
- Custom scrollbars: NOC-themed scrollbars added to all HTML files
- Primary domain: tni-toolkit.salvo.host (github.io as vacation home)
- Site links updated to use HTML versions instead of GitHub MD links

---

## 2025-12-08

### AlinaNova
- `device-calculator.html` v1.2.0 — Device category filter, search boxes, sharecode system, file table display
- `tni-store.json` v1.1.0 — Added cpu, memory, storage, firmware fields to all network devices
- `tni-programs.json` v1.1.1 — Whitespace cleanup

### Salvo Praxis
- Renamed `server-calculator.html` → `device-calculator.html`
- Style guide alignment for device calculator (custom dropdown, button classes, colors)
- Added HTML header format to all HTML files
- Added Custom Dropdown pattern to `STYLE_GUIDE.md`
- Updated all documentation (CLAUDE.md, README.md, CONTRIBUTING.md, contributing.html)
- `credits.html` v1.3.0 — Redesigned greetz with contribution counts, added CONTRIBUTIONS.md link

### Блинчик
- Mentioned device calculator improvements in Discord

---

## 2025-12-07

### Salvo Praxis
- `tni-traffic-types.json` v1.0.0 — Converted 14 traffic types from HackMD @tower-network wiki
- `credits.html` v1.0.0 — Credits page with sources, greetz, contribution tracking
- `contributing.html` v1.0.0 — Styled contribution guide
- `STYLE_GUIDE.md` — Complete CSS reference with inline code styling
- Updated all JSON files with full `_meta` headers and attribution

### Chaotic Crumb
- `tni-programs.json` v1.1.0 — Added 8 firmware programs (rtkernel, hakernel, bladeos, vlanfirm, firewatcher, wirerat, netpeeker, dnsspam)

### gamers2000
- Suggested firmware programs addition

### Crona
- Suggested voip_provider and provider_firmware categories for future additions

---

## 2025-12-06 and earlier

### Salvo Praxis
- `tni-store.json` v1.0.0 — Initial equipment catalog
- `tni-programs.json` v1.0.0 — Initial programs dataset
- `tni-cli-commands.json` v1.0.0 — Terminal command reference
- `server-calculator.html` v1.0.0 — Initial server/program compatibility calculator
- `seed-finder.html` v1.0.0 — Starting proposal seed finder (3,794 seeds, 455 combinations)
- `index.html` — Landing page
- Project architecture and style guide foundation

### Chaotic Crumb
- `tni-store.json` v1.0.1 — ICC sata_slots corrected from 2 to 1

### Singing Pot Beast
- Reported ICC sata_slots error

---

## External Sources

| Source | Used For | Notes |
|--------|----------|-------|
| [HackMD @tower-network](https://hackmd.io/@tower-network) | Traffic types documentation | Converted to JSON by Salvo Praxis. Thorinbur confirmed usage. |
| [TNI Discord Community](https://discord.com/invite/nNKRMjDhf2) | Data corrections, suggestions, testing | |
| [TNI Seed Harvester](https://github.com/salvo-praxis/tni-seed-harvester) | Automated seed collection pipeline | |

---

## How This File Works

This is a simple changelog-style record of who contributed what and when. It complements:
- **credits.html** — Styled credits page on the toolkit site
- **JSON `_meta.contributors`** — Attribution embedded in data files
- **HTML header comments** — Attribution embedded in tool files

**Adding entries:**
- Group by date, then by contributor
- Version-bumped files: `` `filename` vX.Y.Z — Brief description ``
- General work: one-liner describing the change
- Keep it concise — details live in commit messages and file headers
