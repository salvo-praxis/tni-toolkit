# Contribution History

Running log of all contributions to the TNI Toolkit. For guidelines on contributing, see [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 2025-12-08

### AlinaNova21
- `device-calculator.html` v1.2.0 — Device category filter, search boxes, sharecode system, file table display
- `tni-store.json` v1.1.0 — Added cpu, memory, storage, firmware fields to all network devices
- `tni-programs.json` v1.1.1 — Whitespace cleanup

### Salvo Praxis
- Renamed `server-calculator.html` → `device-calculator.html`
- Style guide alignment for device calculator (custom dropdown, button classes, colors)
- Added HTML header format to all HTML files
- Added Custom Dropdown pattern to `STYLE_GUIDE.md`
- Updated all documentation (CLAUDE.md, README.md, CONTRIBUTING.md, contributing.html)
- Added contribution tracking to credits.html

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

When you contribute, add your entry here with a one-liner describing what you did.
