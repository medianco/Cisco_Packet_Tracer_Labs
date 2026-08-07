# Enterprise Campus Network Lab

## 📖 Overview

This project is a **full-scale Enterprise Campus Network Lab** designed to simulate a real-world enterprise infrastructure using Cisco technologies.

It follows the **Cisco Three-Tier Hierarchical Network Model (Core, Distribution, and Access Layers)** and demonstrates enterprise-grade Layer 2 and Layer 3 networking, redundancy, high availability, security, and data center connectivity.

The lab was built for learning, testing, and practicing advanced networking concepts commonly used in production enterprise environments.

---

# 🏗️ Network Architecture

The topology consists of four main sections:

- 🖥️ Data Center
- 🌐 Core Layer
- 🔀 Distribution Layer
- 💻 Access Layer

The entire infrastructure is interconnected using redundant links to eliminate single points of failure and provide high availability.

---

# ⚙️ Technologies Implemented

## Layer 2 Technologies

- VLAN Segmentation
- Trunk Links (802.1Q)
- Rapid PVST+
- STP Root Primary & Secondary
- EtherChannel
  - LACP
  - PAgP
- DTP
- VTP Version 3
- DHCP Snooping
- Broadcast Domain Management

---

## Layer 3 Technologies

- Inter-VLAN Routing
- HSRP (Gateway Redundancy)
- OSPF Routing
- Static Routing
- Default Route
- Layer 3 EtherChannel
- Redundant Layer 3 Links

---

# 🏢 Data Center Services

The Data Center hosts several enterprise services, including:

- DHCP Server
- DNS Server
- FTP Server
- Web Server
- Email Server
- Syslog Server
- Application Servers

Each service resides in its own dedicated VLAN to provide proper segmentation and security.

---

# 🗂️ VLAN Design

The network includes multiple VLANs for user groups and server infrastructure:

| VLAN | Purpose |
|------|---------|
| VLAN 10 | Users |
| VLAN 20 | Users |
| VLAN 30 | Users |
| VLAN 40 | Users |
| VLAN 50 | Users |
| VLAN 60 | Users |
| VLAN 70 | Users |
| VLAN 80 | Users |
| VLAN 130 | Infrastructure Services |
| VLAN 140 | Application Services |
| VLAN 150 | Enterprise Services |
| VLAN 160 | Server Farm |

---

# 🔒 Security Features

This lab demonstrates several enterprise security mechanisms:

- DHCP Snooping
- Trusted & Untrusted Ports
- DHCP Starvation Protection
- VLAN Isolation
- Secure Layer 2 Design

---

# ♻️ High Availability

To ensure maximum network availability, the lab implements:

- Dual Core Switches
- Dual Distribution Switches
- Redundant Access Uplinks
- HSRP Virtual Gateways
- OSPF Dynamic Routing
- STP Root Redundancy
- EtherChannel Link Aggregation

---

# 🎯 Learning Objectives

This project provides hands-on experience with:

- Enterprise Network Design
- Campus Network Architecture
- Cisco Switching
- Cisco Routing
- High Availability
- Redundancy
- Network Security
- Data Center Integration
- Layer 2 & Layer 3 Troubleshooting

---

# 🛠️ Skills Demonstrated

- Cisco Enterprise Networking
- OSPF
- HSRP
- Rapid PVST+
- EtherChannel
- VLAN Design
- Inter-VLAN Routing
- DHCP Snooping
- Enterprise Data Center Connectivity
- Three-Tier Campus Design

---

# 🚀 Purpose

This repository serves as a personal learning project and portfolio demonstrating practical experience in designing, implementing, and troubleshooting enterprise-scale Cisco campus networks.

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

### 🎯 Focus Areas

- Enterprise Networking
- Network Engineering
- Cybersecurity
- Network Automation
- AI in Networking

---

> **Designed for learning, practicing, and mastering Cisco Enterprise Networking technologies.**