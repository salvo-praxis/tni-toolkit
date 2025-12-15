# Traffic Types Reference

> **Source:** [tni-traffic-types.json](../data/tni-traffic-types.json) v1.0.1  
> **Last Updated:** 2025-12-14

Network traffic types for firewall rules, router configuration, and traffic analysis — 14 types across 10 categories.

---

## Table of Contents

- [Utility](#utility) (1)
- [Management](#management) (1)
- [Infrastructure](#infrastructure) (2)
- [Consumer](#consumer) (2)
- [Routing](#routing) (1)
- [Streaming](#streaming) (1)
- [VoIP](#voip) (1)
- [Database](#database) (2)
- [Decentro](#decentro) (1)
- [Malicious](#malicious) (2)

---

## Quick Reference

| Type | Port | Protocol | Name | Category |
|------|------|----------|------|----------|
| `icmp` | N/A | ICMP | ICMP | Utility |
| `tcp/23` | 23 | TCP | SSH | Management |
| `udp/53` | 53 | UDP | DNS | Infrastructure |
| `udp/67` | 67 | UDP | DHCP | Infrastructure |
| `tcp/80` | 80 | TCP | HTTP | Consumer |
| `tcp/443` | 443 | TCP | HTTPS | Consumer |
| `udp/520` | 520 | UDP | RIP | Routing |
| `udp/554` | 554 | UDP | RTSP | Streaming |
| `udp/5060` | 5060 | UDP | SIP | VoIP |
| `tcp/3306` | 3306 | TCP | Database (MySQL) | Database |
| `tcp/5432` | 5432 | TCP | Database (PostgreSQL) | Database |
| `tcp/8333` | 8333 | TCP | Decentro | Decentro |
| `tcp/510-519` | 510-519 | TCP | Worm Transmission | ⚠️ Malicious |
| `tcp/8000-8099` | 8000-8099 | TCP | Text Scraping | ⚠️ Malicious |

---

## Detailed Reference

### Utility

#### ICMP — Internet Control Message Protocol

| Property | Value |
|----------|-------|
| **Type** | `icmp` |
| **Protocol** | ICMP |
| **Port** | N/A |
| **Description** | Default type for ping routine. Used for network diagnostics. |
| **Used by** | `ping routine` |

---

### Management

#### SSH — Secure Shell / Debugger Access

| Property | Value |
|----------|-------|
| **Type** | `tcp/23` |
| **Protocol** | TCP |
| **Port** | 23 |
| **Description** | All debugger and netsh commands use this port for remote device access. |
| **Used by** | `debugger`, `netsh commands` |

---

### Infrastructure

#### DNS — Domain Name System

| Property | Value |
|----------|-------|
| **Type** | `udp/53` |
| **Protocol** | UDP |
| **Port** | 53 |
| **Description** | Required for any Consumer activity. Essential network service. |
| **Used by** | `dns-server`, `reply-dns-queries`, `consumer activity` |

#### DHCP — Dynamic Host Configuration Protocol

| Property | Value |
|----------|-------|
| **Type** | `udp/67` |
| **Protocol** | UDP |
| **Port** | 67 |
| **Description** | Any Client/Device with DHCP enabled uses this for auto-configuration. |
| **Used by** | `dhcp-server`, `reply-dhcp-request`, `DHCP clients` |

---

### Consumer

#### HTTP — Hypertext Transfer Protocol

| Property | Value |
|----------|-------|
| **Type** | `tcp/80` |
| **Protocol** | TCP |
| **Port** | 80 |
| **Description** | Consumer activities not otherwise covered. Standard web traffic. |
| **Used by** | `consumer activity`, `web traffic` |

#### HTTPS — HTTP Secure

| Property | Value |
|----------|-------|
| **Type** | `tcp/443` |
| **Protocol** | TCP |
| **Port** | 443 |
| **Description** | Consumer activities not otherwise covered. Encrypted web traffic. |
| **Used by** | `consumer activity`, `secure web traffic` |

---

### Routing

#### RIP — Routing Information Protocol

| Property | Value |
|----------|-------|
| **Type** | `udp/520` |
| **Protocol** | UDP |
| **Port** | 520 |
| **Description** | Used by rip routine for route advertisement between routers. |
| **Used by** | `rip routine`, `route advertisement` |

---

### Streaming

#### RTSP — Real Time Streaming Protocol

| Property | Value |
|----------|-------|
| **Type** | `udp/554` |
| **Protocol** | UDP |
| **Port** | 554 |
| **Description** | CCTV and video streaming. |
| **Used by** | `cctv-camera`, `cctv-monitor`, `stream-live-video` |

---

### VoIP

#### SIP — Session Initiation Protocol

| Property | Value |
|----------|-------|
| **Type** | `udp/5060` |
| **Protocol** | UDP |
| **Port** | 5060 |
| **Description** | VOIP phones and voice streaming. |
| **Used by** | `voip-phone`, `stream-voice consumers` |

---

### Database

#### Database (MySQL)

| Property | Value |
|----------|-------|
| **Type** | `tcp/3306` |
| **Protocol** | TCP |
| **Port** | 3306 |
| **Description** | Database queries - MySQL style. Used for store-text requests. |
| **Used by** | `store-text`, `dns-server` |

#### Database (PostgreSQL)

| Property | Value |
|----------|-------|
| **Type** | `tcp/5432` |
| **Protocol** | TCP |
| **Port** | 5432 |
| **Description** | Database queries - PostgreSQL style. Any store-* requests (possibly outdated). |
| **Used by** | `store-*`, `consumers`, `servers` |

---

### Decentro

#### Decentro — P2P Network

| Property | Value |
|----------|-------|
| **Type** | `tcp/8333` |
| **Protocol** | TCP |
| **Port** | 8333 |
| **Description** | All P2P/Decentro activities for cryptocurrency operations. |
| **Used by** | `decentro rigs`, `p2p activities` |

---

### Malicious

> ⚠️ **Warning:** Block these traffic types to prevent attacks on your network.

#### Worm Transmission

| Property | Value |
|----------|-------|
| **Type** | `tcp/510-519` |
| **Protocol** | TCP |
| **Port Range** | 510-519 |
| **Description** | Malicious worm propagation. Block this range to prevent worm spread. |
| **Used by** | `malware`, `worm propagation` |

#### Text Scraping

| Property | Value |
|----------|-------|
| **Type** | `tcp/8000-8099` |
| **Protocol** | TCP |
| **Port Range** | 8000-8099 |
| **Description** | Malicious text scraping. Block this range to prevent scraping attacks. |
| **Used by** | `malware`, `scraping attacks` |

---

## Category Summary

| Category | Description | Types |
|----------|-------------|-------|
| Utility | Basic network utilities (ping, traceroute) | 1 |
| Management | Device management and remote access | 1 |
| Infrastructure | Core network services (DNS, DHCP) | 2 |
| Consumer | End-user web traffic | 2 |
| Routing | Router-to-router communication | 1 |
| Streaming | Audio/video streaming | 1 |
| VoIP | Voice over IP | 1 |
| Database | Database connections | 2 |
| Decentro | Decentro cryptocurrency network | 1 |
| Malicious | Known malicious traffic — **block these** | 2 |

---

## Sources

- [HackMD - Network Traffic Types](https://hackmd.io/@tower-network/network-traffic-types) by @tower-network

## Contributors

Salvo Praxis, Claude (Anthropic), Thorinbur

---

*[View styled HTML version](traffic-types-reference.html) · [Back to TNI Toolkit](../README.md)*
