# CLI Commands Reference

> **Source:** [tni-cli-commands.json](../data/tni-cli-commands.json) v1.1.0  
> **Last Updated:** 2025-12-14

Complete NetShell (netsh) command reference — 24 commands with syntax and examples.

**Note:** Commands require a debugger device connected to the network. Use `man <command>` in-game for help.

---

## Table of Contents

**Shell Shortcuts**
- [Shell Shortcuts](#shell-shortcuts)

**Commands**
- [alias](#alias)
- [always](#always)
- [botconf](#botconf)
- [cron](#cron)
- [dhcp](#dhcp)
- [dns](#dns)
- [dstat](#dstat)
- [firewall](#firewall)
- [haconf](#haconf)
- [net](#net)
- [pcap](#pcap)
- [power](#power)
- [program](#program)
- [rip](#rip)
- [route](#route)
- [scan](#scan)
- [sftp](#sftp)
- [try](#try)
- [vlan](#vlan)
- [vmconf](#vmconf)
- [watch](#watch)

**Utility Commands**
- [clear](#clear)
- [echo](#echo)
- [lstdbg](#lstdbg)
- [man](#man)
- [notify](#notify)
- [quit](#quit)

---

## Shell Shortcuts

| Key | Action |
|-----|--------|
| `↑` (Up Arrow) | Cycle previous executed command |
| `Tab` | Try auto-complete word |
| `Ctrl+W` | Erase previous word from cursor |
| `Ctrl+A` | Go to start of command |
| `Ctrl+E` | Go to end of command |
| `Ctrl+C` | Halt/exit/clear |
| `Ctrl+D` | Exit terminal |
| `Ctrl+V` | Paste from clipboard |
| `~` (Tilde) | Toggle terminal |

---

## Commands

### program

Program management - install, start, stop, and manage programs on servers.

**Syntax:**
```
program <action> [program_name] on <device_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `list` | List available programs to install |
| `describe` | Get program description |
| `view installed` | View installed programs on device |
| `view running` | View running programs on device |
| `install` | Install program on device |
| `start` | Start program on device |
| `stop` | Stop program on device |
| `uninstall` | Uninstall program from device (* for all) |

**Examples:**
```
program list
program describe dns-server
program view installed on 123 using 456
program view running on 123 using 456
program install dns-lite on 123 using 456
program start dns-lite on 123 using 456
program stop dns-lite on 123 using 456
program uninstall dns-lite on 123 using 456
program uninstall * on 123 using 456
```

---

### dns

DNS management - lookup, map, and unmap domain names.

**Syntax:**
```
dns <action> <domain> [as <address>] [on <dns_addr>] using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `lookup` | Test resolving a domain |
| `map` | Map a domain to an address |
| `unmap` | Clear DNS record for domain |

**Examples:**
```
dns lookup abc.xyz using 456
dns map readnews.com as 123 using 456
dns map readnews.com as @foobar using 456
dns unmap readnews.com using 456
```

---

### dhcp

DHCP management - configure DHCP server options.

**Syntax:**
```
dhcp <action> [options] on <dhcp_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show DHCP options on server |
| `option dns` | Auto designate DNS servers |
| `option prefix` | Auto assign network addresses with prefix |
| `option bind` | Assign specific network address based on hardware address |
| `option unbind` | Remove hardware address binding |

**Examples:**
```
dhcp show on @mydhcp using @mydebug
dhcp option dns @mydns on @mydhcp using @mydebug
dhcp option prefix @net1/ on @mydhcp using 456
dhcp option bind 1234 as @fixed on @dhcp using 456
dhcp option unbind 1234 on @dhcp using 456
```

---

### firewall

Manage rules on firewalls - allow/deny traffic by type, source, destination.

**Syntax:**
```
firewall <action> [traffic_type] [from <src>] [to <dst>] on <fw_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show firewall policies and their numbers |
| `default allow` | Set default policy to allow |
| `default deny` | Set default policy to deny |
| `allow` | Add allow policy |
| `deny` | Add deny policy |
| `remove` | Remove policy by number (#N) |
| `clear` | Clear all policies |

**Traffic Types:**
```
tcp/<port>, udp/<port>, tcp/*<wildcard>, udp/*<wildcard>
```

**Examples:**
```
firewall show on 123 using 456
firewall default allow on 123 using 456
firewall default deny on 123 using 456
firewall allow from @alice to @bob on 123 using 456
firewall allow udp/53 to @dns on 123 using 456
firewall deny from @alice to @bob on 123 using 456
firewall deny tcp/22 from @hacker on 123 using 456
firewall deny tcp/7*9 on 123 using 456
firewall remove #0 on 123 using 456
firewall remove #2 #3 #5 on 123 using 456
firewall clear on 123 using 456
```

---

### route

Manage routes on routers - add, remove, and configure routing rules.

**Syntax:**
```
route <action> [dst_addr] [traffic <type>] [from <port:src>] via <port> on <router_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show routes and their numbers |
| `default` | Set default route (via port or drop) |
| `add` | Append a route |
| `remove` | Remove route by number (#N) |
| `clear` | Clear all routes |
| `enable broadcast` | Forward all broadcast requests |
| `drop broadcast` | Drop all broadcast requests |

**Examples:**
```
route show on 123 using 456
route default via port0 on 123 using 456
route default drop on 123 using 456
route add @abc via port1 on 123 using 456
route add @abc traffic tcp/80 via port2 on 123 using 456
route add traffic udp/5060 from @voip via port2 on 123 using 456
route add traffic udp/67 from port1 via port2 on 123 using 456
route add from port1:98712 via port2 on 123 using 456
route remove #0 on 123 using 456
route remove #2 #3 #5 on 123 using 456
route clear on 123 using 456
route enable broadcast on 123 using 456
route drop broadcast on 123 using 456
```

---

### rip

Configure auto route discovery on routers (RIP protocol).

**Syntax:**
```
rip <action> [via <port>] on <router_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show RIP configuration |
| `advertise` | Start advertising routing information |
| `stop advertise` | Stop advertising routing information |
| `listen` | Listen to advertised routing information |
| `ignore` | Ignore advertised routing information |

**Examples:**
```
rip show on 123 using 456
rip advertise on 123 using 456
rip advertise via port0 on 123 using 456
rip stop advertise on 123 using 456
rip listen on 123 using 456
rip ignore on 123 using 456
```

---

### vlan

Manage virtual local area networks on managed switches.

**Syntax:**
```
vlan <action> <port(s)> [with #<tag>] on <switch_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show VLAN setup on managed switch |
| `tag` | Tag VLAN ID to port(s) |
| `untag` | Untag VLAN ID from port(s) |
| `clear` | Clear VLAN configuration |

**Examples:**
```
vlan show on @mysw1 using @mydebug
vlan tag port1 with #vlan1 on @mysw using @mydebug
vlan tag port1 port2 with #vlan2 on @mysw using @mydebug
vlan tag port3 with #vlan1 #vlan2 on @mysw using @mydebug
vlan untag port2 with #vlan2 on @mysw using @mydebug
vlan untag port2 port1 on @mysw using @mydebug
vlan clear on @mysw using @mydebug
```

---

### net

Manage network configuration on devices/users.

**Syntax:**
```
net <action> [value] on <target_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show network configuration |
| `address set` | Set network address |
| `address clear` | Clear network address |
| `dns set` | Designate DNS server address |
| `dns clear` | Clear designated DNS server |
| `dhcp boot` | Request DHCP on boot only |
| `dhcp periodic` | Request DHCP periodically |
| `dhcp disable` | Disable DHCP requests |
| `dhcp request` | Perform DHCP request now |

**Aliases:** `address` → `addr` → `a`

**Examples:**
```
net show on 123 using 456
net address set @235-013 on 123 using 456
net addr set @debug1 on 123 using 456
net a set @mybox on 123 using 456
net dns set 789 on 123 using 456
net dns set 789 790 on 123 using 456
net dns clear on 456
net addr clear on 456
net dhcp boot on 456
net dhcp periodic on 456
net dhcp disable on 456
net dhcp request on 456
```

---

### scan

Scan and list devices accessible through a debugger.

**Syntax:**
```
scan [device_type] [from <source>] [with <traffic_type>] using <debugger_addr>
```

**Device Types:**

| Short | Long | Description |
|-------|------|-------------|
| `a` | `all` | All device types |
| `d` | `devices` | All devices |
| `u` | `users` | User devices |
| `S` | `switches` | Network switches |
| `r` | `routers` | Network routers |
| `t` | `taps` | Network taps |
| `f` | `firewalls` | Network firewalls |
| `dns` | `dns-servers` | DNS servers |
| `dhcp` | `dhcp-servers` | DHCP servers |
| `link` | `tower-links` | Tower links |
| `vm` | `virt.-machines` | Virtual machines |

**Examples:**
```
scan devices using 123
scan d using 123
scan dhcp from 123 with udp/67 using 456
scan routers using 123
```

---

### dstat

View device status through a remote debugger.

**Syntax:**
```
dstat [clear] <address> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| (default) | Get status of specified device |
| `clear` | Clear port tx/rx statistics |

**Examples:**
```
dstat 123 using 456
dstat clear 123 using 456
```

---

### watch

Watch device information/programs through a debugger.

**Syntax:**
```
watch [address] using <debugger_addr>
```

**Examples:**
```
watch using 123
watch 123 using 456
```

---

### pcap

Start traffic capture on a network tap.

**Syntax:**
```
pcap [exclude] [=<traffic_type>...] on <tap_addr> using <debugger_addr>
```

**Examples:**
```
pcap on 123 using 456
pcap =udp/520 on 123 using 456
pcap exclude =tcp/23 =udp/23 on 123 using 456
```

---

### vmconf

Manage virtual machines on servers.

**Syntax:**
```
vmconf <action> [cpu memory storage] [netaddr <addr>] on <server_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show virtual machines on server |
| `create` | Create a virtual machine |

**Examples:**
```
vmconf show on @mysrv using @mydebug
vmconf create 2 1 1 on @mysrv using @mydebug
vmconf create 2 1 1 netaddr @myvm on @mysrv using @mydebug
```

---

### botconf

Manage bots on devices.

**Syntax:**
```
botconf <action> [to <visit_addr>] on <target_addr> using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show bots and their configuration |
| `create visitor` | Create a bot to generate visit traffic |

**Examples:**
```
botconf show on 123 using 456
botconf create visitor to 789 on 123 using 456
```

---

### haconf

Manage high-availability setup on devices.

**Syntax:**
```
haconf show on <device_addr> using <debugger_addr>
```

**Examples:**
```
haconf show on @mydevice using @mydebug
```

---

### sftp

Remote tool for file backup/migration.

**Syntax:**
```
sftp <action> [file_name] on <src_addr> [to <dst_addr>] [rename <new_name>] using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `ls` | Show data and configuration files |
| `cp` | Copy file from source to destination |
| `rm` | Remove file from source |

**Examples:**
```
sftp ls on 123 using 456
sftp cp /etc/routes.conf on 123 to 789 using 456
sftp cp /etc/routes.conf on 123 to 789 rename backup1 using 456
sftp rm myfile on 1337 using 456
```

---

### power

Remote device power management.

**Syntax:**
```
power <wake|suspend> [on <device_addr>|broadcast] using <debugger_addr>
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `wake` | Power on device(s) |
| `suspend` | Power off device(s) |

**Examples:**
```
power suspend on 123 using 456
power wake on 123 using 456
power wake broadcast using 456
```

---

### alias

Create command aliases for convenience.

**Syntax:**
```
alias [alias_name] [command]
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| (no args) | List command aliases |
| `set` | Set command alias |
| `unset` | Unset command alias |

**Note:** Use `${1}`, `${2}`, etc. for parameters in aliases.

**Examples:**
```
alias
alias apt program
alias telnet always using
alias apt
alias tr trace ${1} from @dbg; tr 123
```

---

### always

Shell quality-of-life enhancements - set default debugger/device.

**Syntax:**
```
always <using|on> [address]
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `using` | Set default debugger to always use |
| `using` (no arg) | Cycle default debugger |
| `not using` | Clear always helper settings |
| `on` | Set default device to always be on |

**Examples:**
```
always using 123
always using
always not using
always on 456
```

---

### cron

Schedule commands to run automatically.

**Syntax:**
```
cron <action> [schedule] [command]
```

**Subcommands:**

| Subcommand | Description |
|------------|-------------|
| `show` | Show scheduled commands |
| `add` | Add a new cron schedule |
| `remove` | Remove cron schedules (#N) |
| `clear` | Clear cron logs |
| `clear all` | Clear all schedules and logs |

**Schedules:** `hourly`, specific time (e.g., `1200`)

**Examples:**
```
cron show
cron add hourly ping 123
cron add 1200 program start dns-server on @noon
cron remove #0 #2
cron clear
cron clear all
```

---

### try

Try a command, run another if it succeeds or fails.

**Syntax:**
```
try <cmd1> [then <cmd2>] [else <cmd3>]
```

**Examples:**
```
try ping 1234 else notify 1234 is down
try ping 1234 then notify up else notify down
```

---

## Utility Commands

### lstdbg

List debuggers for remote access.

**Note:** Only lists debuggers that are RUNNING - make sure to power them up.

**Syntax:**
```
lstdbg
```

---

### notify

Send an on-screen notification.

**Syntax:**
```
notify <message>
```

**Examples:**
```
notify Server is down!
```

---

### man

Usage manual/help routine.

**Syntax:**
```
man [command]
```

**Examples:**
```
man
man firewall
man route
```

---

### clear

Clear the terminal screen.

**Syntax:**
```
clear
```

---

### echo

Print text to terminal.

**Syntax:**
```
echo <message>
```

---

### quit

Exit netsh terminal.

**Syntax:**
```
quit
```

---

## Contributors

Salvo Praxis, Claude (Anthropic)

---

*[View styled HTML version](cli-reference.html) · [Back to TNI Toolkit](../README.md)*
