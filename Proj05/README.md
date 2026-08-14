# Enterprise Campus & Data Center Network Architecture

## 📌 Project Overview

This project presents a comprehensive **Enterprise Network Infrastructure and Security Architecture** designed to simulate a modern enterprise environment.

The architecture integrates a **Three-Tier Campus Network**, **Data Center**, **DMZ**, **WAN/Internet connectivity**, **network segmentation**, **redundancy**, and **security zones** into a unified enterprise network design.

The project demonstrates practical network engineering concepts including **VLAN segmentation, Layer 2/Layer 3 architecture, redundancy, routing, firewall security, server infrastructure, network management, and high availability**.

---

## 🏗️ Network Architecture

The infrastructure is divided into several major architectural domains:

### 1. Enterprise Campus Network

The campus network follows the traditional **Three-Tier Hierarchical Model**:

```text
                    ┌───────────────────┐
                    │     Core Layer    │
                    │   CORE-SW1/CORE-SW2│
                    └─────────┬─────────┘
                              │
                    ┌─────────┴─────────┐
                    │ Distribution Layer│
                    │     DIST-SW1/2    │
                    └─────────┬─────────┘
                              │
                    ┌─────────┴─────────┐
                    │    Access Layer   │
                    │   Access Switches │
                    └─────────┬─────────┘
                              │
                     End Devices / Users
```

The campus network provides connectivity for:

* Corporate users
* Departmental networks
* Voice/VoIP
* Printers
* Wireless clients
* Guest users
* Network management
* Internal services

---

## 🗂️ VLAN & Network Segmentation

The network uses VLAN-based segmentation to separate different business functions and security domains.

Example VLAN categories include:

| VLAN    | Purpose                       |
| ------- | ----------------------------- |
| VLAN 5  | Management                    |
| VLAN 10 | Corporate Users               |
| VLAN 15 | Finance / Business Department |
| VLAN 20 | Corporate Users               |
| VLAN 25 | Additional User Network       |
| VLAN 30 | Printers                      |
| VLAN 35 | Voice                         |
| VLAN 40 | Corporate Users               |
| VLAN 45 | Corporate Users               |
| VLAN 50 | Corporate Users               |
| VLAN 55 | Corporate Users               |
| VLAN 60 | Guest / Special Services      |

> VLAN numbers and IP addressing are documented according to the topology and addressing plan included in this project.

---

# 🏢 Data Center

The Data Center provides centralized infrastructure for critical enterprise services.

The design separates infrastructure into multiple functional zones.

### Management & Monitoring Zone

Includes services such as:

* Network Management System
* System Monitoring
* Security Monitoring
* NOC infrastructure
* Administrative management

### Application & Financial Services Zone

Designed for critical business applications such as:

* Core Banking Systems
* Payment Systems
* Financial Databases
* Internet Banking Services

### Server & Storage Zone

Provides infrastructure for:

* Physical Servers
* Virtualized Servers
* Application Servers
* Database Servers
* Storage Area Network (SAN)
* Network Attached Storage (NAS)
* Backup Systems

---

# 🔐 Security Architecture

Security is implemented through multiple levels of network segmentation and controlled traffic flows.

## Security Zones

The architecture includes:

* **Inside Zone**
* **DMZ Zone**
* **Guest Zone**
* **Management & Monitoring Zone**
* **Voice Zone**
* **Data Center Zones**

This approach helps isolate critical resources and reduce the potential impact of security incidents.

---

# 🛡️ DMZ Architecture

The DMZ provides a controlled environment for services that require external access.

Example DMZ services include:

* Web Server
* Email Server
* Online Banking
* External DNS
* Proxy Server

The DMZ is isolated from the internal enterprise network through perimeter security controls.

```text
                  Internet / WAN
                       │
                ┌──────┴──────┐
                │ Perimeter FW│
                └──────┬──────┘
                       │
                 ┌─────┴─────┐
                 │    DMZ    │
                 ├───────────┤
                 │ Web Server│
                 │ Mail      │
                 │ DNS       │
                 │ Proxy     │
                 │ Banking   │
                 └───────────┘
```

---

# 🌐 WAN & Internet Connectivity

The architecture includes redundant WAN/Internet paths to improve availability and resilience.

Multiple upstream connections provide alternative paths toward external networks and Internet services.

The design demonstrates concepts such as:

* WAN redundancy
* Multiple uplinks
* Failover
* Perimeter routing
* Internet connectivity
* Firewall-based traffic control

---

# 🔄 High Availability & Redundancy

High availability is an important design objective of this project.

Redundant components are used across multiple network layers, including:

* Dual Core switches
* Redundant Distribution switches
* Multiple Access Layer uplinks
* Redundant perimeter firewalls
* Multiple WAN paths
* Redundant network connections
* Alternative traffic paths

The objective is to minimize single points of failure and maintain network connectivity during infrastructure failures.

---

# 📡 Wireless & Voice Infrastructure

The architecture also includes dedicated infrastructure for wireless and voice services.

### Wireless

The design includes:

* Wireless LAN Controller
* Lightweight Access Points
* Wireless user networks
* Guest wireless connectivity
* Dedicated wireless VLANs

### Voice

Voice infrastructure is separated from normal user traffic through dedicated VLANs.

Components include:

* IP Phones
* Voice VLAN
* VoIP Gateway
* Voice services

This separation improves traffic management, security, and Quality of Service (QoS) implementation.

---

# 🖥️ Network Services

The infrastructure can support a range of enterprise services, including:

* DHCP
* DNS
* NTP
* AAA
* Network Monitoring
* Syslog
* Wireless Management
* VoIP
* Application Services
* Database Services
* Backup Services

---

# 🧩 Technologies & Concepts

This project demonstrates practical knowledge of:

### Network Architecture

* Enterprise Network Design
* Three-Tier Hierarchical Architecture
* Core / Distribution / Access
* Data Center Networking
* WAN Architecture
* DMZ Architecture

### Switching

* VLANs
* Trunking
* Access Ports
* Layer 2 Switching
* Layer 3 Switching
* EtherChannel
* Link Redundancy

### Routing

* Inter-VLAN Routing
* Dynamic Routing
* Default Routing
* Route Redundancy
* WAN Routing

### High Availability

* Redundant Core
* Redundant Distribution
* Redundant Firewalls
* Multiple Uplinks
* Network Failover

### Security

* Network Segmentation
* Security Zones
* DMZ
* Firewall Policies
* Management Network Isolation
* Guest Network Isolation
* Defense in Depth

### Infrastructure Services

* DHCP
* DNS
* NTP
* AAA
* Syslog
* Monitoring
* Wireless
* VoIP

---

# 📊 IP Addressing Design

The network uses structured private IPv4 addressing to provide logical separation between different network segments.

The addressing plan follows a predictable structure based on VLAN and network function.

Example:

```text
192.168.x.0/24
172.16.x.0/24
10.x.x.0/24
```

Detailed addressing information can be found in the network documentation and topology diagram.

---

# 🗺️ Network Topology

The complete network topology is available in:

```text
diagrams/
└── enterprise-network-topology.png
```

The topology illustrates:

* Campus Network
* Data Center
* Core Layer
* Distribution Layer
* Access Layer
* Perimeter Firewalls
* WAN/Internet
* DMZ
* Security Zones
* VLAN Segmentation
* Servers
* End Devices

---

# 📁 Project Structure

```text
enterprise-campus-datacenter-network/
│
├── README.md
│
├── diagrams/
│   └── enterprise-network-topology.png
│
├── documentation/
│   ├── network-architecture.md
│   ├── vlan-design.md
│   ├── ip-addressing.md
│   ├── security-design.md
│   └── high-availability.md
│
├── configurations/
│   ├── core/
│   ├── distribution/
│   ├── access/
│   ├── firewall/
│   └── wan/
│
└── labs/
    └── packet-tracer/
```

---

# 🎯 Project Objectives

The primary objectives of this project are to demonstrate the ability to:

* Design an enterprise-scale network
* Apply hierarchical network architecture
* Implement logical network segmentation
* Design redundant network infrastructure
* Separate internal and external services
* Design a secure DMZ
* Integrate Data Center infrastructure
* Design WAN and Internet connectivity
* Apply security zoning principles
* Document enterprise network architecture
* Develop a scalable and maintainable network design

---

# 🚀 Future Improvements

Future versions of this project may include:

* OSPF Multi-Area
* BGP Internet Edge
* HSRP / VRRP
* Advanced QoS
* DHCP Snooping
* Dynamic ARP Inspection
* IP Source Guard
* Network Access Control (NAC)
* Zero Trust Network Access (ZTNA)
* Micro-Segmentation
* IDS/IPS
* SIEM Integration
* Network Automation with Python
* Ansible-based configuration management
* NetBox IPAM integration
* Zabbix monitoring
* Centralized Syslog
* Infrastructure as Code

---

# 📚 Learning Outcomes

This project provides practical experience in designing and documenting enterprise network infrastructure.

It demonstrates how different technologies can be integrated into a single architecture while considering:

**Scalability → Availability → Security → Performance → Manageability**

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

**Next Generation Network Engineer**

Focused on:

* Enterprise Networking
* Network Security
* Data Center Networking
* Network Automation
* Python for Network Engineers
* AI & Networking

---

## ⭐ Portfolio

This repository is part of my practical networking portfolio and is continuously evolving as new technologies, security controls, automation capabilities, and architectural concepts are added.

If you find this project useful, feel free to ⭐ star the repository and explore the other networking projects in my portfolio.
