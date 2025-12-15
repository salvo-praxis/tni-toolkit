# Store Reference

> **Source:** [tni-store.json](../data/tni-store.json) v1.2.1  
> **HTML Version:** [store-reference.html](store-reference.html) v1.9.0  
> **Last Updated:** 2025-12-14

Complete catalog of purchasable items from D-Market2, Barracks and Sons, and other in-game vendors.

**Note:** Some warranty values may be inaccurate (recorded during LAB session). Corrections welcome via PR.

---

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| [Network Switches](#network-switches) | 10 | Layer 2 switches for network connectivity |
| [Routers](#routers) | 13 | Layer 3 routing devices |
| [Servers](#servers) | 16 | Compute servers for running programs |
| [Decentro Rigs](#decentro-rigs) | 1 | Cryptocurrency mining equipment |
| [Firewalls & TAPs](#firewalls--taps) | 4 | Security and monitoring devices |
| [Debuggers & Test Devices](#debuggers--test-devices) | 3 | Network debugging equipment |
| [Converters & Repeaters](#converters--repeaters) | 14 | Media conversion and signal repeating |
| [UPS & Surge Protection](#ups--surge-protection) | 5 | Power backup and protection |
| [Power Expanders](#power-expanders) | 6 | Power distribution strips |
| [Power Cables](#power-cables) | 5 | AC and DC power cables |
| [Peripherals](#peripherals) | 3 | Storage and utility accessories |
| [Monitoring Displays](#monitoring-displays) | 3 | Status monitoring screens |
| [Tower Link Sockets](#tower-link-sockets) | 2 | Inter-floor connectivity |
| [Cabling Tools](#cabling-tools) | 2 | Cable fabrication equipment |
| [Network Cables](#network-cables) | 9 | RJ45 and Fiber cables |
| [Racks & Shelving](#racks--shelving) | 13 | Equipment mounting solutions |

**Total: 104 items**

---

## Network Switches

| Model | Vendor | Ports | Media | VLAN | CPU | MEM | HDD | Firmware | Trav/tick | CPU Cycle | Power | Warranty | Price |
|-------|--------|-------|-------|------|-----|-----|-----|----------|-----------|-----------|-------|----------|-------|
| Blade5 | Blade Networking Inc | 5 | Ethernet | — | 2 | 1 | 1 | bladeos | 25 | 1 tick / 2.0s | 22W | 7d | $100 |
| Blade10 | Blade Networking Inc | 10 | Ethernet | — | 2 | 1 | 1 | bladeos | 50 | 1 tick / 2.0s | 41W | 7d | $450 |
| Blade4 | Blade Networking Inc | 4 | Fiber | — | 2 | 1 | 1 | bladeos | 36 | 1 tick / 2.0s | 30W | 7d | $100 |
| Blade12 | Blade Networking Inc | 12 | Fiber | ✓ | 2 | 2 | 2 | vlanfirm | 108 | 1 tick / 2.0s | 84W | 14d | $1,000 |
| Blade66 | Blade Networking Inc | 12 | Mixed | — | 2 | 1 | 1 | bladeos | 84 | 1 tick / 2.0s | 66W | 14d | $950 |
| Blade15 | Blade Networking Inc | 15 | Ethernet | ✓ | 2 | 2 | 2 | vlanfirm | 75 | 1 tick / 2.0s | 88W | 14d | $900 |
| Blade88 | Blade Networking Inc | 16 | Mixed | ✓ | 2 | 2 | 2 | vlanfirm | 112 | 1 tick / 2.0s | 87W | 18d | $1,600 |
| Blade88 (Refurb) | Refurb Hut | 16 | Mixed | ✓ | 2 | 2 | 2 | vlanfirm | 112 | 1 tick / 2.0s | 87W | 3d | $480 |
| Blade30 | Blade Networking Inc | 30 | Ethernet | ✓ | 2 | 2 | 2 | vlanfirm | 150 | 1 tick / 2.0s | 183W | 21d | $1,650 |
| Blade1515 | Blade Networking Inc | 30 | Mixed | ✓ | 2 | 2 | 2 | vlanfirm | 210 | 1 tick / 2.0s | 208W | 21d | $1,850 |

---

## Routers

| Model | Vendor | Ports | Media | CPU | MEM | HDD | Firmware | HA | Trav/tick | CPU Cycle | Power | Warranty | Price |
|-------|--------|-------|-------|-----|-----|-----|----------|-----|-----------|-----------|-------|----------|-------|
| Disco Nano 2G | Conduit Systems | 4 | Mixed | 4 | 1 | 2 | rtkernel | — | 65 | 1 tick / 2.0s | 23W | 21d | $180 |
| Disco Nano | AB compute Ltd. / Conduit | 5 | Mixed | 4 | 1 | 2 | rtkernel | — | 60 | 1 tick / 2.0s | 21W | 17d | $264 |
| Disco Milli | Conduit Systems | 8 | Ethernet | 4 | 1 | 2 | rtkernel | — | 80 | 1 tick / 2.0s | 27W | 16d | $325 |
| Disco Nano 3H | Conduit Systems | 4 | Mixed | 8 | 2 | 4 | hakernel | ✓ | 75 | 1 tick / 2.0s | 26W | 28d | $450 |
| Disco Milli 2G | Conduit Systems | 8 | Ethernet | 4 | 1 | 2 | rtkernel | — | 112 | 1 tick / 2.0s | 30W | 18d | $500 |
| Disco Micro | Conduit Systems | 10 | Mixed | 4 | 1 | 2 | rtkernel | — | 125 | 1 tick / 2.0s | 41W | 14d | $600 |
| Disco Milli 3G | Conduit Systems | 8 | Ethernet | 8 | 2 | 4 | hakernel | ✓ | 160 | 1 tick / 2.0s | 41W | 21d | $800 |
| Disco Micro 2G | Conduit Systems | 10 | Mixed | 4 | 1 | 2 | rtkernel | — | 162 | 1 tick / 2.0s | 47W | 19d | $950 |
| Disco Micro 2G (Refurb) | Refurb Hut | 10 | Mixed | 4 | 1 | 2 | rtkernel | — | 162 | 1 tick / 2.0s | 47W | 3d | $285 |
| Disco Milli 4G | Conduit Systems | 8 | Ethernet | 8 | 2 | 4 | hakernel | ✓ | 240 | 1 tick / 2.0s | 60W | 25d | $1,150 |
| Zodianet Spine Router | Zodiac Networks | 3 | Fiber | 4 | 1 | 2 | rtkernel | — | 250 | 1 tick / 2.0s | 78W | 14d | $1,200 |
| Disco Micro 3G | Conduit Systems | 10 | Mixed | 8 | 2 | 4 | hakernel | ✓ | 175 | 1 tick / 2.0s | 50W | 21d | $1,300 |
| Zodianet Beam Router | Zodiac Networks | 4 | Fiber | 4 | 1 | 2 | rtkernel | — | 450 | 1 tick / 2.0s | 138W | 17d | $3,700 |

---

## Servers

| Model | Vendor | Ports | CPU | MEM | HDD | SATA | Trav/tick | CPU Cycle | Power | Warranty | Price |
|-------|--------|-------|-----|-----|-----|------|-----------|-----------|-------|----------|-------|
| ICC1 | Interchange Compute | 1 | 1 | 2 | 2 | 1 | 6 | 1 tick / 2.0s | 19W | 8d | $160 |
| Golonys-Cinco | Golonys Ltd. | 1 | 1 | 1 | 1 | 5 | 6 | 1 tick / 2.0s | 13W | 17d | $400 |
| MacroHard NLB2 | The Server Shoppe | 3 | 2 | 1 | 1 | 0 | 80 | 1 tick / 2.0s | 83W | 73d | $437 |
| MacroHard Boulder SRV | AB compute Ltd. | 2 | 4 | 4 | 6 | 0 | 16 | 1 tick / 2.0s | 72W | 14d | $540 |
| MacroHard Boulder+ SRV | AB compute Ltd. | 2 | 6 | 8 | 8 | 0 | 28 | 1 tick / 2.0s | 161W | 14d | $1,020 |
| MacroHard Boulder+ SRV (Refurb) | Refurb Hut | 2 | 6 | 8 | 8 | 0 | 28 | 1 tick / 2.0s | 161W | 3d | $255 |
| MacroHard Boulder++ SRV | The Server Shoppe | 3 | 6 | 10 | 10 | 0 | 48 | 1 tick / 2.0s | 312W | 14d | $1,750 |
| Savannah Meerkat | Savannah Org. | 2 | 4 | 4 | 4 | 0 | 16 | 1 tick / 2.0s | 62W | 21d | $950 |
| MacroHard Monolith SRV | The Server Shoppe | 2 | 16 | 10 | 4 | 2 | 52 | 1 tick / 2.0s | 429W | 14d | $2,100 |
| Savannah Gazelle | Savannah Org. | 2 | 6 | 6 | 6 | 0 | 24 | 1 tick / 2.0s | 108W | 35d | $2,200 |
| Savannah Gazelle | AB compute Ltd. | 2 | 6 | 6 | 6 | 0 | 24 | 1 tick / 2.0s | 108W | 35d | $2,640 |
| MacroHard Ledge Two SRV | The Server Shoppe | 3 | 24 | 14 | 4 | 2 | 150 | 1 tick / 2.0s | 973W | 21d | $2,625 |
| MacroHard Ledge Three SRV | The Server Shoppe | 4 | 24 | 16 | 4 | 2 | 208 | 1 tick / 2.0s | 1,125W | 21d | $4,000 |
| Savannah Aardvark | Savannah Org. | 3 | 10 | 10 | 5 | 2 | 65 | 1 tick / 2.0s | 293W | 42d | $4,500 |
| MacroHard Megalith SRV | The Server Shoppe | 5 | 32 | 16 | 4 | 6 | 240 | 1 tick / 2.0s | 1,223W | 24d | $4,750 |
| Savannah Wildebeest | Savannah Org. | 3 | 16 | 16 | 8 | 2 | 104 | 1 tick / 2.0s | 423W | 49d | $6,800 |

---

## Decentro Rigs

| Model | Vendor | Ports | CPU | MEM | HDD | SATA | Software | Trav/tick | CPU Cycle | Power | Warranty | Price |
|-------|--------|-------|-----|-----|-----|------|----------|-----------|-----------|-------|----------|-------|
| Dvergar | AB compute Ltd. | 0 | 24 | 16 | 8 | 0 | decentro-node | 40 | 1 tick / 2.0s | 523W | 7d | $1,320 |

---

## Firewalls & TAPs

| Model | Vendor | Type | Ports | Media | CPU | MEM | HDD | Firmware | Trav/tick | CPU Cycle | Power | Warranty | Price |
|-------|--------|------|-------|-------|-----|-----|-----|----------|-----------|-----------|-------|----------|-------|
| EthTapper | Fortypoint Security | TAP | 3 | Ethernet | 2 | 2 | 1 | wirerat | 18 | 1 tick / 2.0s | 12W | 21d | $300 |
| FireWatch ES4A | Fortypoint Security | Firewall | 3 | Mixed | 6 | 3 | 3 | firewatcher, wirerat | 52 | 1 tick / 2.0s | 55W | 19d | $550 |
| FireWatch CP4E | Fortypoint Security | Firewall | 4 | Ethernet | 6 | 3 | 3 | firewatcher, wirerat | 160 | 1 tick / 2.0s | 163W | 16d | $1,500 |
| Bastion 5E | Fortypoint Security | Firewall | 4 | Ethernet | 6 | 3 | 3 | firewatcher, wirerat | 384 | 1 tick / 2.0s | 387W | 14d | $4,000 |

---

## Debuggers & Test Devices

| Model | Vendor | Ports | CPU | MEM | HDD | Firmware | Trav/tick | CPU Cycle | Power | Warranty | Notes | Price |
|-------|--------|-------|-----|-----|-----|----------|-----------|-----------|-------|----------|-------|-------|
| DNS Load Test Box | AB compute Ltd. | 1 | 1 | 1 | 1 | dnsspam | 6 | 5 tick(s) / 1.0s | 112W | 0d | LAB Mode only; pre-purchased | $0 |
| Debugger Alice | AB compute Ltd. | 2 | 1 | 1 | 1 | netpeeker | 12 | 1 tick / 2.0s | 72W | 21d | 2-port ethernet remote debugger | $1,200 |
| DNS UDP/53 Load Tester | AB compute Ltd. | 1 | 1 | 1 | 1 | dnsspam | 6 | 10 tick(s) / 1.0s | 202W | 7d | Commercial; 2× tick rate of LAB | $1,200 |

---

## Converters & Repeaters

| Model | Vendor | Type | Direction | Media In | Media Out | Trav/tick | CPU Cycle | Power | Warranty | Price |
|-------|--------|------|-----------|----------|-----------|-----------|-----------|-------|----------|-------|
| Simplex RJ45 1R | Data Liner Corp. | Repeater | Unidirectional | RJ45 | RJ45 | 20 | 1 tick / 2.0s | 7W | 21d | $30 |
| Simplex SC 1R | Data Liner Corp. | Repeater | Unidirectional | SC | SC | 40 | 1 tick / 2.0s | 11W | 21d | $30 |
| Simplex 452F 1C | Data Liner Corp. | Converter | Unidirectional | RJ45 | SC | 30 | 1 tick / 2.0s | 9W | 21d | $40 |
| Simplex SC245 1C | Data Liner Corp. | Converter | Unidirectional | SC | RJ45 | 30 | 1 tick / 2.0s | 9W | 21d | $40 |
| Duplex RJ45 1R | Data Liner Corp. | Repeater | Bidirectional | RJ45 | RJ45 | 12 | 1 tick / 2.0s | 6W | 21d | $50 |
| Duplex SC 1R | Data Liner Corp. | Repeater | Bidirectional | SC | SC | 24 | 1 tick / 2.0s | 8W | 21d | $50 |
| Duplex 1C | Data Liner Corp. | Converter | Bidirectional | RJ45 | SC | 18 | 1 tick / 2.0s | 7W | 21d | $60 |
| Simplex RJ45 3R | Data Liner Corp. | Repeater | Unidirectional | RJ45 | RJ45 | 60 | 1 tick / 2.0s | 9W | 28d | $120 |
| Simplex SC 3R | Data Liner Corp. | Repeater | Unidirectional | SC | SC | 120 | 1 tick / 2.0s | 15W | 28d | $120 |
| Simplex 452F 3C | Data Liner Corp. | Converter | Unidirectional | RJ45 | SC | 90 | 1 tick / 2.0s | 12W | 21d | $160 |
| Simplex SC245 3C | Data Liner Corp. | Converter | Unidirectional | SC | RJ45 | 90 | 1 tick / 2.0s | 12W | 21d | $160 |
| Duplex RJ45 3R | Data Liner Corp. | Repeater | Bidirectional | RJ45 | RJ45 | 36 | 1 tick / 2.0s | 7W | 28d | $200 |
| Duplex SC 3R | Data Liner Corp. | Repeater | Bidirectional | SC | SC | 72 | 1 tick / 2.0s | 10W | 28d | $200 |
| Duplex 3C | Data Liner Corp. | Converter | Bidirectional | RJ45 | SC | 54 | 1 tick / 2.0s | 8W | 21d | $240 |

---

## UPS & Surge Protection

| Model | Vendor | Capacity | Warranty | Notes | Price |
|-------|--------|----------|----------|-------|-------|
| Tenabolt AVR2 | Tenabolt Retail | 400W | 28d | AVR (surge protection) | $150 |
| Tenabolt UPS2 | Tenabolt Retail | 200W | 24d | UPS base unit | $750 |
| Tenabolt UPS2E | Tenabolt Retail | 800W | 28d | Expanded load UPS | $2,000 |
| Mountable Tenabolt UPS2E | Tenabolt Retail | 800W | 28d | Mountable UPS | $2,200 |
| Tenabolt UPS2X | Tenabolt Retail | 1500W | 28d | Extra-expanded load UPS | $5,000 |

---

## Power Expanders

| Model | Vendor | Outlets | Notes | Price |
|-------|--------|---------|-------|-------|
| Tenabolt Expander 1-2 | Tenabolt Retail / Mr Cable | 2 | Power distribution strip | $20 |
| Tenabolt Expander 1-5 | Tenabolt Retail | 5 | Power distribution strip | $100 |
| Mountable Tenabolt Expander 1-3 | Tenabolt Retail | 3 | Mountable strip | $100 |
| Mountable Tenabolt Expander 1-6 | Tenabolt Retail | 6 | Mountable strip | $180 |
| Mountable Tenabolt Expander 1-7 | Tenabolt Retail | 7 | Mountable strip | $200 |
| Tenabolt Expander 1-10 | Tenabolt Retail | 10 | Power distribution strip | $280 |

---

## Power Cables

| Model | Vendor | Type | Length | Price |
|-------|--------|------|--------|-------|
| Power UK-B 500 | Mr Cable | AC | 500px | $15 |
| Power UK-B 1000 | Tenabolt Retail | AC | 1000px | $40 |
| DC Adapter 200p | Mr Cable | DC | 200px | $50 |
| Power UK-B 1500 | Mr Cable | AC | 1500px | $80 |
| DC Adapter 500p | Mr Cable | DC | 500px | $120 |

---

## Peripherals

| Model | Vendor | Notes | Price |
|-------|--------|-------|-------|
| Cardboard Box | Mr Cable | 8 storage slots; cable/peripheral organization | $10 |
| Storage Extension | Interchange Compute | SATA 3.5"; +4 storage to attached device | $75 |
| Data Wiper | Fortypoint Security | Factory reset; wipes all data when plugged in | $399 |

---

## Monitoring Displays

| Model | Vendor | Power | Warranty | Notes | Price |
|-------|--------|-------|----------|-------|-------|
| Top Issue Monitor | Vision Grid | 13W | 14d | Displays top floor issues | $300 |
| Visitor Status Monitor | Vision Grid | 13W | 14d | Visitor count by domain name | $300 |
| Satiety Stats Monitor | Vision Grid | 13W | 14d | Resident satiety levels | $500 |

---

## Tower Link Sockets

| Model | Media | Requires | Price |
|-------|-------|----------|-------|
| RJ45 Copper Socket | Ethernet | Socketeer | $100 |
| SC Fiber | Fiber | Socketeer | $100 |

---

## Cabling Tools

| Model | Vendor | Cable Type | Capacity | Price |
|-------|--------|------------|----------|-------|
| Cable-O-Matic RJ45 20kPx | Cabler's Union | Ethernet RJ45 Cat5 | 20,000px | $1,500 |
| Cable-O-Matic Fiber SC 20kPx | Cabler's Union | Fiber SC Double Core | 20,000px | $1,500 |

---

## Network Cables

Available colors: Original, Yellow, Blue, Purple, Orange, Green, Red, Grey

### Ethernet (RJ45 Cat5)

| Vendor | Length | Price |
|--------|--------|-------|
| Mr Cable | 200px | $5 |
| Mr Cable | 500px | $15 |
| Mr Cable | 1000px | $40 |
| Mr Cable | 1500px | $75 |
| Mr Cable | 2000px | $150 |

### Fiber (SC)

| Vendor | Length | Price |
|--------|--------|-------|
| Mr Cable | 200px | $1 |
| Mr Cable | 500px | $5 |
| Mr Cable | 1500px | $25 |
| Mr Cable | 3000px | $60 |

---

## Racks & Shelving

| Model | Vendor | Size | Requires | Price |
|-------|--------|------|----------|-------|
| Wall Shelf (single) | Barracks and Sons | — | Barracks and Sons | $10 |
| Mounting Shelf Piece R500 | Barracks and Sons | Narrow | D-Market2 | $10 |
| Mounting Shelf Piece R930 | Barracks and Sons | Wide | D-Market2 | $20 |
| Pipe Shelf (3-tier) | Barracks and Sons | — | Barracks and Sons | $35 |
| Narrow Rack | Barracks and Sons | Short | Barracks and Sons | $40 |
| Wide Rack | Barracks and Sons | Short | Barracks and Sons | $45 |
| Narrow Rack | Barracks and Sons | Medium | Barracks and Sons | $60 |
| Wide Rack | Barracks and Sons | Medium | Barracks and Sons | $65 |
| Narrow Rack | Barracks and Sons | Tall | Barracks and Sons | $80 |
| Wide Rack | Barracks and Sons | Tall | Barracks and Sons | $85 |
| Narrow Rack | Barracks and Sons | X-Tall | Barracks and Sons | $95 |
| Wide Rack | Barracks and Sons | X-Tall | Barracks and Sons | $100 |
| Trolley 2C | Barracks and Sons | — | D-Market2 | $800 |

---

## Contributors

Salvo Praxis, Claude (Anthropic), Chaotic Crumb, Singing Pot Beast, AlinaNova, Блинчик, gamers2000

---

*[View styled HTML version](store-reference.html) · [Back to TNI Toolkit](../README.md)*
