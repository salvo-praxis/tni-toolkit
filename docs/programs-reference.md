# Programs Reference

> **Source:** [tni-programs.json](../data/tni-programs.json) v1.1.1  
> **Last Updated:** 2025-12-14

Complete guide to all installable programs — 25 programs across 10 categories.

**Program Types:**

| Type | Description |
|------|-------------|
| **Producer** | Generates uses directly |
| **Converter** | Transforms inputs to outputs |
| **Data Storage** | Persists data across reboots |
| **Firmware** | Device operating systems |

---

## Table of Contents

- [DNS](#dns-programs) (3)
- [DHCP](#dhcp-programs) (2)
- [Storage](#storage-programs) (4)
- [Services](#service-programs) (4)
- [Decentro](#decentro-programs) (3)
- [Botnet](#botnet-programs) (1)
- [Router Firmware](#router-firmware) (2)
- [Switch Firmware](#switch-firmware) (2)
- [Firewall Firmware](#firewall-firmware) (1)
- [Debugging Firmware](#debugging-firmware) (3)

---

## Quick Reference

### Server Programs

| Program | Type | CPU | MEM | HDD | Stack | Output/Input |
|---------|------|-----|-----|-----|-------|--------------|
| dns-lite | Producer | 1 | 1 | 2 | 3 | 3× reply-dns-queries |
| dns-server | Converter | 4 | 3 | 3 | 20 | 1× store-text → 20× reply-dns-queries |
| sun-dns | Converter | 10 | 6 | 9 | 40 | 3× store-text → 40× reply-dns-queries |
| dnsmasq | Producer | 1 | 1 | 2 | 3 | 3× reply-dhcp-request |
| kea | Converter | 6 | 5 | 7 | 15 | 1× store-text → 15× reply-dhcp-request |
| padu_v1 | Producer | 1 | 2 | 4 | 2 | 1× store-text/image |
| padu_v2 | Producer | 2 | 4 | 8 | 2 | 2× store-text/image/audio |
| padu_v3 | Producer | 4 | 6 | 12 | 4 | 4× store-text/image/audio/video |
| poems-db | Producer | 4 | 4 | 6 | 4 | 4× store-text |
| gitcoffee | Converter | 4 | 2 | 4 | 16 | 2× store-text → 16× read-text/update-software |
| mailer | Converter | 5 | 6 | 3 | 15 | 3× store-text+image → 15× read/post-text/verify |
| voip-server | Producer | 5 | 2 | 5 | 10 | 10× accept-voip-phone-connection |
| rtsp-diva-r | Producer | 6 | 4 | 10 | 13 | 13× accept-cctv-camera/monitor |
| decentro-node | Producer | 24 | 12 | 6 | 10 | 10× facilitate-p2p-transaction |
| decentro-wallet | Data Storage | 1 | 2 | 2 | — | 10/free HDD access-p2p-currency |
| decentro-collector | Converter | 1 | 1 | 1 | 6/MEM | 1× access-p2p → 1× access-p2p |
| ubbt | Converter | 4 | 4 | 6 | 4 | 4× inspect-user-packets → 4× support-bots |

### Firmware Programs

| Program | Type | CPU | MEM | HDD | Requires |
|---------|------|-----|-----|-----|----------|
| rtkernel | Firmware | 4 | 1 | 2 | /etc/routes.conf |
| hakernel | Firmware | 8 | 2 | 4 | /etc/routes.conf |
| bladeos | Firmware | 2 | 1 | 1 | — |
| vlanfirm | Firmware | 2 | 2 | 2 | /etc/vlan.tags |
| firewatcher | Firmware | 4 | 1 | 2 | /etc/nftables.conf |
| wirerat | Firmware | 2 | 2 | 1 | — |
| netpeeker | Firmware | 1 | 1 | 1 | — |
| dnsspam | Firmware | 1 | 1 | 1 | — |

---

## Programs by Category

### DNS Programs

#### dns-lite

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 1 |
| **MEM** | 1 |
| **HDD** | 2 |
| **Stack Limit** | 3 |
| **Output** | `reply-dns-queries` × 3/tick |
| **Description** | Replies network-addresses to DNS queries. Production is limited to 3 compatible uses on the device's use stack. |

#### dns-server

| Property | Value |
|----------|-------|
| **Type** | Converter |
| **CPU** | 4 |
| **MEM** | 3 |
| **HDD** | 3 |
| **Stack Limit** | 20 |
| **Input** | `store-text` × 1/tick |
| **Output** | `reply-dns-queries` × 20/tick |
| **Requires** | Running text storage program |
| **Description** | Replies network-addresses to DNS queries. Requires access to a running text storage program. |

#### sun-dns

| Property | Value |
|----------|-------|
| **Type** | Converter |
| **CPU** | 10 |
| **MEM** | 6 |
| **HDD** | 9 |
| **Stack Limit** | 40 |
| **Input** | `store-text` × 3/tick |
| **Output** | `reply-dns-queries` × 40/tick |
| **Requires** | Running text storage program |
| **Description** | Enterprise grade DNS server. Requires access to a running text storage program. |

---

### DHCP Programs

#### dnsmasq

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 1 |
| **MEM** | 1 |
| **HDD** | 2 |
| **Stack Limit** | 3 |
| **Output** | `reply-dhcp-request` × 3/tick |
| **Description** | Automatically assigns network addresses and designated DNS server to network devices. |

#### kea

| Property | Value |
|----------|-------|
| **Type** | Converter |
| **CPU** | 6 |
| **MEM** | 5 |
| **HDD** | 7 |
| **Stack Limit** | 15 |
| **Input** | `store-text` × 1/tick |
| **Output** | `reply-dhcp-request` × 15/tick |
| **Requires** | Running text storage program |
| **Description** | Automatically assigns network addresses and designated DNS server to network devices. Requires access to a running text storage program. |

---

### Storage Programs

#### padu_v1

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 1 |
| **MEM** | 2 |
| **HDD** | 4 |
| **Stack Limit** | 2 |
| **Output** | `store-text`, `store-image` × 1/tick |
| **Description** | Primary aggregation data unit. Supports text and image storage. Production is limited to 2 compatible uses on the device's use stack. |

#### padu_v2

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 2 |
| **MEM** | 4 |
| **HDD** | 8 |
| **Stack Limit** | 2 |
| **Output** | `store-text`, `store-image`, `store-audio` × 2/tick |
| **Description** | Primary aggregation data unit. Supports text, image and audio storage. Improved disk handling algorithm. |

#### padu_v3

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 4 |
| **MEM** | 6 |
| **HDD** | 12 |
| **Stack Limit** | 4 |
| **Output** | `store-text`, `store-image`, `store-audio`, `store-video` × 4/tick |
| **Description** | Primary aggregation data unit. Supports text, image, audio and video storage. Improved disk handling algorithm. |

#### poems-db

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 4 |
| **MEM** | 4 |
| **HDD** | 6 |
| **Stack Limit** | 4 |
| **Output** | `store-text` × 4/tick |
| **Description** | Text-based database. Supports text storage usage. |

---

### Service Programs

#### gitcoffee

| Property | Value |
|----------|-------|
| **Type** | Converter |
| **CPU** | 4 |
| **MEM** | 2 |
| **HDD** | 4 |
| **Stack Limit** | 16 |
| **Input** | `store-text` × 2/tick |
| **Output** | `read-text`, `update-software` × 16/tick |
| **Requires** | Running text storage program |
| **Description** | Open-source software repository. Supports software-updates requests. |

#### mailer

| Property | Value |
|----------|-------|
| **Type** | Converter |
| **CPU** | 5 |
| **MEM** | 6 |
| **HDD** | 3 |
| **Stack Limit** | 15 |
| **Input** | `store-text` AND `store-image` × 3/tick |
| **Output** | `read-text`, `post-text`, `verify-user` × 15/tick |
| **Requires** | Running text AND image storage program |
| **Description** | Provides exchange email usages to users. |

#### voip-server

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 5 |
| **MEM** | 2 |
| **HDD** | 5 |
| **Stack Limit** | 10 |
| **Output** | `accept-voip-phone-connection` × 10/tick |
| **Description** | Supports Voice over Internet Protocol for streaming voice messages to phones. Allows voip phones to be connected to produce stream-voice uses. |

#### rtsp-diva-r

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 6 |
| **MEM** | 4 |
| **HDD** | 10 |
| **Stack Limit** | 13 |
| **Output** | `accept-cctv-camera-connection`, `accept-cctv-monitor-connection` × 13/tick |
| **Description** | Support surveillance monitoring services. Allows surveillance accessories to be connected to produce stream-live-video uses. |

---

### Decentro Programs

#### decentro-node

| Property | Value |
|----------|-------|
| **Type** | Producer |
| **CPU** | 24 |
| **MEM** | 12 |
| **HDD** | 6 |
| **Stack Limit** | 10 |
| **Output** | `facilitate-p2p-transaction` × 10/tick |
| **Description** | Authenticate Decentro transactions. Decentro peers can connect to this program to perform peer-to-peer transactions. You may only spend decentro currencies that are accessible by decentro nodes. |

#### decentro-wallet

| Property | Value |
|----------|-------|
| **Type** | Data Storage |
| **CPU** | 1 |
| **MEM** | 2 |
| **HDD** | 2 |
| **Stores** | `access-p2p-currency` — 10 per free HDD |
| **Description** | Safeguards your decentro currencies from power loss or unscheduled shutdown events. Stored uses persist across device reboots. |

#### decentro-collector

| Property | Value |
|----------|-------|
| **Type** | Converter (Transfer) |
| **CPU** | 1 |
| **MEM** | 1 |
| **HDD** | 1 |
| **Stack Limit** | 6 per free MEM |
| **Input (network)** | `access-p2p-currency` × 1/tick |
| **Output (local)** | `access-p2p-currency` × 1/tick |
| **Description** | Collects decentro currencies over the network and accumulates them on the installed device. |

---

### Botnet Programs

#### ubbt

| Property | Value |
|----------|-------|
| **Type** | Converter |
| **CPU** | 4 |
| **MEM** | 4 |
| **HDD** | 6 |
| **Stack Limit** | 4 |
| **Input** | `inspect-user-packets` × 4/tick |
| **Output** | `support-bots` × 4/tick |
| **Requires** | Network tap with user traffic |
| **Description** | Analyzes user traffic behavior from a network tap to support botnet operations. |

---

### Router Firmware

#### rtkernel

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 4 |
| **MEM** | 1 |
| **HDD** | 2 |
| **Requires** | /etc/routes.conf |
| **Description** | Normal capacity router firmware. |

#### hakernel

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 8 |
| **MEM** | 2 |
| **HDD** | 4 |
| **Requires** | /etc/routes.conf |
| **Description** | High capacity router firmware. |

---

### Switch Firmware

#### bladeos

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 2 |
| **MEM** | 1 |
| **HDD** | 1 |
| **Description** | Normal capacity switch firmware. |

#### vlanfirm

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 2 |
| **MEM** | 2 |
| **HDD** | 2 |
| **Requires** | /etc/vlan.tags |
| **Description** | High capacity switch firmware that supports VLAN port tagging. |

---

### Firewall Firmware

#### firewatcher

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 4 |
| **MEM** | 1 |
| **HDD** | 2 |
| **Requires** | /etc/nftables.conf |
| **Description** | Basic Firewall firmware. |

---

### Debugging Firmware

#### wirerat

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 2 |
| **MEM** | 2 |
| **HDD** | 1 |
| **Stack Limit** | 12 |
| **Output** | `inspect-user-packets` × 4/tick |
| **Description** | Network tap firmware that produces inspect-user-packets use stack. |

#### netpeeker

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 1 |
| **MEM** | 1 |
| **HDD** | 1 |
| **Description** | Basic Debugger firmware. |

#### dnsspam

| Property | Value |
|----------|-------|
| **Type** | Firmware |
| **CPU** | 1 |
| **MEM** | 1 |
| **HDD** | 1 |
| **Description** | DNS blasting firmware that rapidly sends out udp/53 requests. |

---

## Use Types

| Category | Uses |
|----------|------|
| Storage | `store-text`, `store-image`, `store-audio`, `store-video` |
| DNS | `reply-dns-queries` |
| DHCP | `reply-dhcp-request` |
| Services | `read-text`, `post-text`, `update-software`, `verify-user` |
| Connections | `accept-voip-phone-connection`, `accept-cctv-camera-connection`, `accept-cctv-monitor-connection` |
| Decentro | `facilitate-p2p-transaction`, `access-p2p-currency` |
| Network | `inspect-user-packets`, `support-bots` |

---

## Contributors

Salvo Praxis, Claude (Anthropic), Chaotic Crumb, gamers2000, Crona, AlinaNova21

---

*[View styled HTML version](programs-reference.html) · [Back to TNI Toolkit](../README.md)*
