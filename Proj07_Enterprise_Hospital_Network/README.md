# Enterprise Hospital Network Design & Implementation

A comprehensive Cisco Packet Tracer project that demonstrates the design and implementation of a secure, scalable enterprise hospital network connecting the headquarters and a branch hospital.

---

## Project Overview

This lab simulates a real-world enterprise network for a hospital environment. The design includes multiple departments, VLAN segmentation, Layer 3 routing, WAN connectivity, VPN, NAT, and redundant Internet connections.

The project focuses on building a secure, highly available, and scalable network using Cisco best practices.

---

## Objectives

By completing this lab, you will learn how to:

- Design a multi-site enterprise network.
- Implement VLAN segmentation for different departments.
- Configure Inter-VLAN Routing using Layer 3 Switches (SVI).
- Configure VLSM IP addressing.
- Implement Static Routing and Floating Static Routes.
- Configure NAT for Internet access.
- Establish Site-to-Site VPN connectivity.
- Deploy DHCP, DNS, Web, and Email servers.
- Apply route summarization.
- Verify end-to-end network connectivity.

---

## Prerequisites

Before starting this lab, you should have knowledge of:

- CCNA Routing and Switching
- IPv4 Addressing & VLSM
- VLANs and Trunking
- Layer 2 Switching
- Layer 3 Switching
- Inter-VLAN Routing
- Static Routing
- Floating Static Routes
- NAT
- DHCP
- DNS
- VPN Fundamentals

---

## Network Topology

The topology consists of:

### Headquarters

- Medical Legal Operations (MLOCS)
- Medical Emergency (MER)
- Medical Records (MRM)
- IT Department
- Customer Service
- Guest Waiting Area

### Branch Hospital

- Nurses & Surgery Operations
- Hospital Labs
- Human Resources
- Marketing
- Finance
- Guest Waiting Area

### Server Farm

- DHCP Server
- DNS Server
- Web Server
- Email Server

---

## Technologies Used

- Cisco Packet Tracer
- Layer 2 Switches
- Layer 3 Switches
- Cisco Routers
- VLANs
- VLSM
- Static Routing
- Floating Static Routing
- NAT
- Site-to-Site VPN
- DHCP
- DNS

---

## Configuration Tasks

This lab includes the following configurations:

- VLAN Creation
- Access & Trunk Ports
- Inter-VLAN Routing (SVI)
- VLSM Addressing
- Static Routing
- Floating Static Route
- Route Summarization
- NAT Configuration
- DHCP Configuration
- Server Configuration
- Site-to-Site VPN
- Internet Connectivity Testing

---

## Verification

Verify the configuration using commands such as:

```bash
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show arp
show mac address-table
show running-config
show ip nat translations
show crypto isakmp sa
show crypto ipsec sa
ping
traceroute
```

---

## Expected Results

After completing this lab:

- All VLANs can communicate through Inter-VLAN Routing.
- End devices obtain IP addresses automatically from the DHCP server.
- Internal users can access Internet resources through NAT.
- Headquarters and Branch communicate securely through the VPN tunnel.
- Floating Static Routes provide backup connectivity in case of WAN failure.
- All servers are reachable from authorized VLANs.
- End-to-end connectivity is successfully verified.

---

## Repository Contents

```
Proj07_Enterprise_Hospital_Network/
│
├── Enterprise_Hospital_Network.pkt
├── topology.png
├── README.md
├── configurations/
│   ├── HQ-Router.txt
│   ├── Branch-Router.txt
│   ├── MLS-HQ.txt
│   └── MLS-Branch.txt
└── screenshots/
```

---

## Skills Demonstrated

- Enterprise Network Design
- IP Address Planning (VLSM)
- Layer 2 Switching
- Layer 3 Routing
- Network Segmentation
- WAN Connectivity
- VPN Deployment
- NAT Configuration
- Network Troubleshooting
- Cisco CLI

---

## Author

**Mohammed AL-Dubai**
