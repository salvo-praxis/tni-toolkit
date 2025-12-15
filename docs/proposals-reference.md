# Proposals Reference

> **Source:** [tni-proposals.json](../data/tni-proposals.json) v1.0.0  
> **Last Updated:** 2025-12-14

Complete guide to all in-game proposals — 30 proposals across 7 categories.

---

## Table of Contents

- [Technology & Research](#technology--research) (9)
- [Infrastructure](#infrastructure) (4)
- [Financial](#financial) (2)
- [Merchant](#merchant) (4)
- [Tenabolt Corporation](#tenabolt-corporation) (4)
- [Power Grid Directives](#power-grid-directives) (2)
- [Software Funding](#software-funding) (4)

---

## Quick Reference

| Proposal | Category | Cost | Repeatable | Key Effect |
|----------|----------|------|------------|------------|
| Remote Backups | Technology | 450 | No | Unlocks `sftp` routine |
| Botnets Research | Technology | 665 | No | Unlocks `botconf` routine |
| High Availability Research | Technology | 600 | No | Unlocks `haconf` routine |
| Jailbreaker | Technology | 1,000 | No | `sftp` can install programs |
| NetOps Research | Technology | 330 | No | Unlocks `cron`, `try`, `notify` |
| Power Management Research | Technology | 225 | No | Unlocks `power` routine |
| RIP | Technology | 1,500 | No | Unlocks `rip` routine |
| Scanning Exploit | Technology | 1,200 | No | Scans bypass router rules |
| Virtual Machines Research | Technology | 999 | No | Unlocks `vmconf` routine |
| Elevator Upgrade | Infrastructure | 1,250→5,000 | Yes (8) | -50% elevator wait per level |
| Second Monitor | Infrastructure | 2,500 | No | Use second monitor (right-alt) |
| New Data Center | Infrastructure | +10% fees | Yes (4) | New floor, more space |
| Internet Exchange Point | Infrastructure | TBD | No | Cross-tower connection (WIP) |
| Liability Insurance | Financial | 300/day | No | SLA breach → $3,000 penalty |
| Lean Administration | Financial | 600→1,100 | Yes (6) | -30% admin costs per level |
| RefurbHut Investment | Merchant | 555 | No | Opens RefurbHut merchant |
| Cabler's Union (Basic) | Merchant | 300 | No | Unlocks more CU proposals |
| Cabler's Union (Discounts) | Merchant | 300 | No | Cheaper cable prices |
| Cabler's Union (Merchant) | Merchant | 300 | No | CU sells prototypes |
| Fusion Plant Phase 1 | Tenabolt | 1,000 | No | -20% power cost |
| Fusion Plant Phase 2 | Tenabolt | 2,000 | No | -50% power, -10% outages |
| Legal Retaliation | Tenabolt | FREE | No | Tenabolt pays outage penalties |
| Lobby Against Tenabolt | Tenabolt | FREE | No | No fines for non-DC power |
| Overvoltage Directive | Power Grid | 200→300 | Yes (3) | +30% surge, -30% outage |
| Undervoltage Directive | Power Grid | 200→300 | Yes (3) | -30% surge, +30% outage |
| PADU Development Funding | Software | 300 | No | Unlocks padu_v3 |
| Poems DB | Software | 200 | No | Unlocks poems-db |
| Sun DNS | Software | 400 | No | Unlocks sun-dns |
| KEA DHCP Server | Software | 200 | No | Unlocks kea |

---

## Starting Proposals

These 15 proposals can appear when starting a new game:

| Proposal | Cost |
|----------|------|
| Cabler's Union (Basic) | 300 |
| Fusion Plant Phase 1 | 1,000 |
| Lean Administration | 600 |
| Legal Retaliation | — |
| Lobby Against Tenabolt | — |
| NetOps Research | 330 |
| Overvoltage Directive | 200 |
| PADU Development Funding | 300 |
| Poems DB | 200 |
| Power Management Research | 225 |
| RefurbHut Investment | 555 |
| Remote Backups | 450 |
| Scanning Exploit | 1,200 |
| Second Monitor | 2,500 |
| Undervoltage Directive | 200 |

*Use the [Seed Finder](../tools/seed-finder.html) to find seeds with specific starting proposal combinations.*

---

## Proposals by Category

### Technology & Research

#### Remote Backups

| Property | Value |
|----------|-------|
| **Cost** | 450 |
| **Lore** | *"3-2-1, let's back it up!"* |
| **Unlocks** | `sftp` routine |
| **Prerequisites** | Technology must not already be acquired |
| **Description** | Adds a new "sftp" routine to netshell. Allows backup of configs/files on remote devices. The routine can also be used to remove malware when regular program uninstalls do not work. |

---

#### Botnets Research

| Property | Value |
|----------|-------|
| **Cost** | 665 |
| **Lore** | *"Not enough users?"* |
| **Unlocks** | `botconf` routine |
| **Prerequisites** | Technology not acquired; 5+ compute servers (increases chance) |
| **Description** | Adds a new "botconf" routine to netshell. Allow configuration of bots that can generate visitor traffic to enterprises. |

---

#### High Availability Research

| Property | Value |
|----------|-------|
| **Cost** | 600 |
| **Lore** | *"HA HA HA, no DR!"* |
| **Unlocks** | `haconf` routine |
| **Prerequisites** | Technology not acquired; 7+ network routers (increases chance) |
| **Description** | Adds a new "haconf" routine to netshell. Allow configuration of high-availability setup on ha-enabled routers. |

---

#### Jailbreaker

| Property | Value |
|----------|-------|
| **Cost** | 1,000 |
| **Lore** | *"Hardware liberation day"* |
| **Unlocks** | sftp can install extracted programs |
| **Prerequisites** | Technology not acquired; **Remote Backups** must be submitted |
| **Description** | The "sftp" routine can now be used to install programs extracted from devices. |

---

#### NetOps Research

| Property | Value |
|----------|-------|
| **Cost** | 330 |
| **Lore** | *"Improvise, adapt, overcome"* |
| **Unlocks** | `cron`, `try`, `notify` routines |
| **Prerequisites** | Technology must not already be acquired |
| **Description** | Adds automation utility for managing and monitoring your network. |

---

#### Power Management Research

| Property | Value |
|----------|-------|
| **Cost** | 225 |
| **Lore** | *"Keep bills low and reliability high."* |
| **Unlocks** | `power` routine |
| **Prerequisites** | Technology must not already be acquired |
| **Description** | Adds power management utility for managing device power state. |

---

#### Route Discovery Protocol v1 (RIP)

| Property | Value |
|----------|-------|
| **Cost** | 1,500 |
| **Lore** | *"State of the art in 1988"* |
| **Unlocks** | `rip` routine |
| **Prerequisites** | Technology not acquired; 7+ network routers (increases chance) |
| **Description** | Adds a new "rip" routine to netshell. Allow configuration of automated route discoveries on routers. |

---

#### Scanning Exploit

| Property | Value |
|----------|-------|
| **Cost** | 1,200 |
| **Lore** | *"Scans too shall pass."* |
| **Unlocks** | Scans bypass router rules (toggleable) |
| **Prerequisites** | Technology must not already be acquired |
| **Description** | Allows netsh and autograph scans to bypass all router rules. The exploit can be optionally turned on/off. |

---

#### Virtual Machines Research

| Property | Value |
|----------|-------|
| **Cost** | 999 |
| **Lore** | *"carrier has arrived."* |
| **Unlocks** | `vmconf` routine |
| **Prerequisites** | Technology not acquired; 5+ compute servers (increases chance) |
| **Description** | Adds a new "vmconf" routine to netshell. Allow configuration of virtual machines on servers. |

---

### Infrastructure

#### Elevator Upgrade

| Property | Value |
|----------|-------|
| **Cost** | 1,250 → 2,000 → 2,500 → 3,000 → 3,500 → 4,000 → 4,500 → 5,000 |
| **Repeatable** | Yes (8 levels) |
| **Lore** | *"Faster travels for those emergencies"* |
| **Effect** | Decrease elevator wait time by 50.0% per level |
| **Prerequisites** | Level 1 guaranteed on day 9; each level requires previous |

**Cost per Level:**

| Level | Cost |
|-------|------|
| 1 | 1,250 |
| 2 | 2,000 |
| 3 | 2,500 |
| 4 | 3,000 |
| 5 | 3,500 |
| 6 | 4,000 |
| 7 | 4,500 |
| 8 | 5,000 |

---

#### Second Monitor

| Property | Value |
|----------|-------|
| **Cost** | 2,500 |
| **Lore** | *"Screen too small?"* |
| **Unlocks** | Second monitor (right-alt to toggle) |
| **Prerequisites** | Technology must not already be acquired |
| **Description** | Allows use of a second monitor by pressing right-alt. |

---

#### New Data Center

| Property | Value |
|----------|-------|
| **Cost** | FREE (+10% admin fees each) |
| **Repeatable** | Yes (4 instances) |
| **Lore** | *"It's free (?) real-estate baby!"* |
| **Unlocks** | New data center floor |
| **Guaranteed Days** | 6, 15, 24, 30 |
| **Description** | Request for a new data center. Adds new location and expands available space. Increases administrative fees by 10.0%. |

---

#### Internet Exchange Point One

| Property | Value |
|----------|-------|
| **Status** | ⚠️ Work in Progress |
| **Cost** | TBD |
| **Lore** | *"Now the whole world had one language and a common speech."* |
| **Unlocks** | Internet exchange point floor, cross-tower connectivity |
| **Description** | Request an internet exchange point with another tower. Allowing cross-tower internet pays handsomely but is risky due to the strict SLA requirements. |

---

### Financial

#### Liability Insurance

| Property | Value |
|----------|-------|
| **Cost** | 300/day recurring premium |
| **Lore** | *"Money solves problems"* |
| **Available** | From day 5 |
| **Description** | SLA breaches no longer ends the game, but comes with a financial penalty of 3000 per breach. Adds a recurring premium cost of 300 per day. |

**Effects:**
- SLA breaches don't end game
- 3,000 penalty per breach
- 300/day recurring premium

---

#### Lean Administration

| Property | Value |
|----------|-------|
| **Cost** | 600 → 700 → 800 → 900 → 1,000 → 1,100 |
| **Repeatable** | Yes (6 levels) |
| **Lore** | *"Pain now for gain later"* |
| **Effect** | -30% admin expenses per level |
| **Description** | Permanently reduce daily admin expenses by 30.0% at the cost of upfront payment. Each level provides the same 30% reduction benefit. |

**Cost per Level:**

| Level | Cost |
|-------|------|
| 1 | 600 |
| 2 | 700 |
| 3 | 800 |
| 4 | 900 |
| 5 | 1,000 |
| 6 | 1,100 |

---

### Merchant

#### RefurbHut Investment

| Property | Value |
|----------|-------|
| **Cost** | 555 |
| **Lore** | *"As long as it works..."* |
| **Unlocks** | RefurbHut merchant |
| **Prerequisites** | Merchant must not already exist |
| **Description** | Fund 555 to support the opening of the RefurbHut merchant, which provides cheap refurbished (no warranty) devices. |

---

#### Support the Cabler's Union (Basic)

| Property | Value |
|----------|-------|
| **Cost** | 300 |
| **Lore** | *"R&D - Rewire and Distribute equally"* |
| **Unlocks** | Cabler's Union Discounts and Merchant proposals |
| **Prerequisites** | None |
| **Description** | Fund 300 to support the Cabler's Union, an R&D institute for the benefit of cabling workers. This unlocks more proposals for the Cabler's Union (merchant and discounts). |

---

#### Support the Cabler's Union (Discounts)

| Property | Value |
|----------|-------|
| **Cost** | 300 |
| **Lore** | *"R&D - Rewire and Distribute equally"* |
| **Unlocks** | Cable price discounts on D-Market |
| **Prerequisites** | **Support the Cabler's Union (Basic)** must be submitted |
| **Description** | Fund 300 to support the Cabler's Union. In return, they promise to lobby for cheaper cable prices (discount %) from the merchants on the DMarket. |

---

#### Support the Cabler's Union (Merchant)

| Property | Value |
|----------|-------|
| **Cost** | 300 |
| **Lore** | *"R&D - Rewire and Distribute equally"* |
| **Unlocks** | Cabler's Union Prototypes on D-Market |
| **Prerequisites** | **Support the Cabler's Union (Basic)** submitted; Merchant must not already exist |
| **Description** | Fund 300 to support the Cabler's Union. This lets them sell their prototypes on the D-Market. |

---

### Tenabolt Corporation

> ⚠️ **Mutual Exclusivity:** Choosing Legal Retaliation or Lobby Against blocks Fusion Plant proposals (these are hostile actions against Tenabolt and end collaboration). However, Legal Retaliation and Lobby Against do NOT block each other — both are hostile actions, so they can stack.

#### Fusion Plant Funding (Phase 1)

| Property | Value |
|----------|-------|
| **Cost** | 1,000 |
| **Lore** | *"Let's make a Sun."* |
| **Effect** | -20% Data Center power cost |
| **Prerequisites** | Must NOT have chosen Legal Retaliation or Lobby Against |
| **Description** | Support Tenabolt Corporation's effort in building a fusion power plant. Reduce all Data Center power cost by 20.0%. |

---

#### Fusion Plant Funding (Phase 2)

| Property | Value |
|----------|-------|
| **Cost** | 2,000 |
| **Lore** | *"Let's make it brighter."* |
| **Prerequisites** | **Fusion Plant Phase 1** submitted; NOT Legal Retaliation or Lobby Against |
| **Description** | Support Tenabolt Corporation's effort in building a fusion power plant. Reduce all Data Center power cost by 50.0%. Reduces probability of power outage/surge by 10.0%. |

**Effects:**
- -50% Data Center power cost
- -10% outage/surge probability

---

#### Legal Retaliation

| Property | Value |
|----------|-------|
| **Cost** | FREE (pricing increase) |
| **Lore** | *"Another power outage? See you in court!"* |
| **Prerequisites** | None |
| **Description** | Lawyer up against Tenabolt Corporation. This proposal eliminates future collaboration with Tenabolt Corporation. Tenabolt Corporation now pays penalties per outage/surge events. All items sold by Tenabolt reseller become more expensive. |

**Effects:**
- Tenabolt pays you per outage/surge
- Tenabolt items more expensive
- No future Tenabolt collaboration

> ℹ️ **Note:** Blocks Fusion Plant proposals (collaboration). Does NOT block Lobby Against — both are hostile actions against Tenabolt, so they can stack.

---

#### Lobby Against Tenabolt Corporation

| Property | Value |
|----------|-------|
| **Cost** | FREE (pricing increase) |
| **Lore** | *"Power to the people."* |
| **Prerequisites** | None |
| **Description** | Lobby for new law against Tenabolt Corporation. This proposal eliminates future collaboration with Tenabolt Corporation. Tenabolt Corporation can no longer issue fines against non Data Center power use. All items sold by Tenabolt reseller become more expensive. |

**Effects:**
- No non-DC power use fines
- Tenabolt items more expensive
- No future Tenabolt collaboration

> ℹ️ **Note:** Blocks Fusion Plant proposals (collaboration). Does NOT block Legal Retaliation — both are hostile actions against Tenabolt, so they can stack.

---

### Power Grid Directives

> **Prerequisites:** Both power surge and outage controllers must be configured.

#### Overvoltage Directive

| Property | Value |
|----------|-------|
| **Cost** | 200 → 250 → 300 |
| **Repeatable** | Yes (3 levels) |
| **Lore** | *"POWER OVERWHELMING!"* |
| **Prerequisites** | Power surge controller configured; Power outage controller configured; Each level requires previous |
| **Description** | +30.0% of power surge occurring, -30.0% of power outage occurring. Trade-off: More surges (damage risk) but fewer blackouts. |

**Effect per Level:**
- +30% power surge ⚡
- -30% power outage 🔋

---

#### Undervoltage Directive

| Property | Value |
|----------|-------|
| **Cost** | 200 → 250 → 300 |
| **Repeatable** | Yes (3 levels) |
| **Lore** | *"Better dark than magic smoke"* |
| **Prerequisites** | Power surge controller configured; Power outage controller configured; Each level requires previous |
| **Description** | -30.0% of power surge occurring, +30.0% of power outage occurring. Trade-off: More blackouts (downtime) but fewer surges (less hardware damage). |

**Effect per Level:**
- -30% power surge ⚡
- +30% power outage 🔋

---

### Software Funding

#### PADU Development Funding

| Property | Value |
|----------|-------|
| **Cost** | 300 |
| **Lore** | *"Everyone's favorite database."* |
| **Unlocks** | PADU v3 database program |
| **Prerequisites** | Program not already unlocked |
| **Description** | Fund the development of PADU v3 database software. |

---

#### Poems DB

| Property | Value |
|----------|-------|
| **Cost** | 200 |
| **Lore** | *"A DB just for the text chads."* |
| **Unlocks** | Poems DB database program |
| **Prerequisites** | Program not already unlocked |
| **Description** | Fund the development of Poems DB database software. |

---

#### Sun DNS

| Property | Value |
|----------|-------|
| **Cost** | 400 |
| **Lore** | *"We've got names for everyone."* |
| **Unlocks** | Sun DNS server program |
| **Prerequisites** | Program not already unlocked; Available from day 5 |
| **Description** | Fund the development of Sun DNS server software. |

---

#### KEA DHCP Server

| Property | Value |
|----------|-------|
| **Cost** | 200 |
| **Lore** | *"Mass host configurations, made easy."* |
| **Unlocks** | KEA DHCP server program |
| **Prerequisites** | Program not already unlocked; Available from day 5 |
| **Description** | Fund the development of KEA DHCP Server software. |

---

## Contributors

AlinaNova, Salvo Praxis, Claude (Anthropic), gamers2000

---

*[View styled HTML version](proposals-reference.html) · [Back to TNI Toolkit](../README.md)*
