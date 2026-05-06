# Network Project

Course project report for **CEN-431: Computer Networks Lab** at the University of Tabuk.

## Project Title

**Design and Implementation of a Multi-Service Network Using Cisco Packet Tracer**

## Overview

This project designs, configures, and validates a scalable enterprise network in Cisco Packet Tracer. The network includes wired and wireless connectivity, VLAN segmentation, dynamic routing, inter-VLAN routing, DHCP, DNS, NAT, and a simulated internet connection.

The network is divided into three main areas:

- **Main Office:** Uses EIGRP and includes routers, switches, PCs, laptops, a wireless access point, DHCP server, and DNS server.
- **Branch Office:** Uses RIP and includes a router, switch, and PCs.
- **Core/WAN:** Connects the main office, branch office, and simulated external internet.

## Main Features

- VLAN segmentation for HR, Finance, IT, and Wireless devices.
- Inter-VLAN routing using Router-on-a-Stick.
- EIGRP routing in the main office network.
- RIP v2 routing in the branch office network.
- Route redistribution between EIGRP and RIP.
- DHCP server with multiple address pools.
- DHCP relay using `ip helper-address`.
- DNS server support.
- Wireless network secured with WPA2-PSK.
- NAT overload/PAT for simulated internet access.
- Connectivity testing using ping and IP configuration checks.

## VLANs

| VLAN | Department / Purpose |
| --- | --- |
| 10 | HR |
| 20 | Finance |
| 30 | IT |
| 40 | Wireless Devices |

## Included Files

| File | Description |
| --- | --- |
| `Network project.pdf` | Final project report with design, configuration summary, testing, challenges, and conclusion. |

## Tools Used

- Cisco Packet Tracer
- Cisco IOS configuration commands
- PDF report generated with LaTeX

## Testing Summary

The project report confirms the following tests:

- Devices in different VLANs can communicate through inter-VLAN routing.
- End devices receive correct IP settings from the DHCP server.
- Branch office devices can reach main office servers.
- Internal devices can reach the simulated internet loopback address `1.1.1.1`.
- EIGRP and RIP route redistribution works after adding the required EIGRP seed metric.

## Known Issues and Fixes

### DHCP Broadcasts Across Subnets

Devices in some VLANs could not receive DHCP addresses because DHCP broadcasts do not pass through routers by default.

**Fix:** Added `ip helper-address 192.168.50.50` on the router subinterfaces.

### EIGRP and RIP Redistribution

Routes were not exchanged correctly between RIP and EIGRP at first.

**Fix:** Added an EIGRP seed metric when redistributing RIP routes:

```text
redistribute rip metric 1000 1 255 1 1500
```

## Recommended Additional Files

The folder currently contains only the PDF report. For a stronger and more complete submission, add these files if you have them:

- Cisco Packet Tracer project file, usually ending in `.pkt`.
- Router and switch configuration files, for example `main-router-config.txt`, `branch-router-config.txt`, and `switch-config.txt`.
- Network topology image or screenshot, for example `topology.png`.
- Testing screenshots showing successful pings, DHCP allocation, routing tables, and NAT verification.
- A short `team-members.txt` file if the instructor wants names and student IDs separately from the report.

## Team Members

- Abdulmohsen Mashaan Al-Mutairi
- Faisal Ali Al-Kathiri
- Faisal Fahad Al-Shehri
- Rakan Saeed Al-Shahrani
