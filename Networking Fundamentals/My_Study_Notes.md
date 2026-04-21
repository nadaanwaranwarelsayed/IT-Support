## 📝 My Networking Study Notes

## 🔌 Connections & Cables

Copper Cross-over: Used to connect two devices of the same type (PC to PC, Router to Router).

Copper Straight-through: Used to connect different devices (PC to Switch, Router to Switch).

Console cable: Used to program a new Router or Switch from a PC via the RS232 port.

Single fiber: For long-distance connections (between cities/countries). Thin, fast, and expensive.

Multi fiber: For local devices (inside buildings). Thicker and more affordable than single-mode.

FastEthernet0: The standard network port found on most devices.

## 💡 General Notes

IP address: The logical address used to identify a device on a network.

Subnet mask: Defines which part of the IP is for the Network and which is for the host. It determines the network range.

Server: It is considered an End Device (just like a PC).

Static IP: Servers must have a Static IP because other devices need to find them at a fixed address.

DNS (Domain Name System): Translates names we remember (nada.com) into IP addresses that machines understand.

Router: Connects different networks. Each port on the router acts as the Default Gateway for that specific network.

## 🛣 Dynamic Routing Protocols

RIPv2: Depends on Hops (how many routers are in the way).

Maximum hops = 15. If it's more than 15, the router considers the destination "Lost."

OSPF: Depends on Speed (Cost).

Fiber link (Fast) = Very low cost (e.g., 1).

Old link (Slow) = Very high cost (e.g., 100).

Rule: OSPF always picks the fastest path, while RIPv2 always picks the path with the fewest routers—even if it's much slower.

## 🔢 Subnetting & OSPF Tricks

VLSM /30: We use the mask 255.255.255.252 for point-to-point links (between routers) to save IPs. It gives only 2 usable hosts.

Wildcard Mask: Used in OSPF configuration. For a /30 subnet, the wildcard is 0.0.0.3.

## 💻 CLI Quick Guide

To configure the router:

en (enable)

conf t (configure terminal)

int g0/0 (choose the interface)

ip add [IP] [Mask] (assign the IP and Subnet Mask)

no shut (The most important command to turn the port on!)

do wr (to save your work so it doesn't get deleted after a restart)

## 🎯 IP Planning (Technical Tips)

.1 --> .10: Reserved for infrastructure (Routers, Switches).

.50 --> .100: Reserved for static devices (Servers, Printers).

.101 --> .254: Reserved for the DHCP Pool (User devices).

## 🔍 Verification Tools

ping: To check if two devices can "see" each other.

tracert: To see the exact path the data took and find where a connection failed.











