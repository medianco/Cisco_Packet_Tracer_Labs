# Enterprise Campus & Branch Network with High Availability, DMZ, VPN & Cloud Integration

## 📌 Project Overview

This project is a comprehensive **Enterprise Network Infrastructure Lab** designed to simulate a real-world organization with a **Main Campus, Branch Campus, Internet Edge, DMZ, Cloud Services, High Availability, Network Redundancy, and Site-to-Site VPN connectivity**.

The architecture demonstrates how enterprise network components can be integrated into a scalable and resilient infrastructure while maintaining network segmentation, service availability, and secure communication between sites.

The project was designed and implemented in **Cisco Packet Tracer** as part of a practical networking portfolio.

---

# 🏗️ High-Level Architecture

The network is divided into several major infrastructure domains:

```text
                         ┌─────────────────┐
                         │   Cloud / DC    │
                         │ Oracle VM       │
                         │ Oracle Server   │
                         └────────┬────────┘
                                  │
                               Internet
                                  │
                         ┌────────┴────────┐
                         │   ISP Network   │
                         └───────┬─────────┘
                                 │
                    ┌────────────┴────────────┐
                    │                         │
              Main Campus                Branch Campus
                    │                         │
              ┌─────┴─────┐             ┌────┴─────┐
              │ Perimeter  │             │ Perimeter│
              │ Firewalls  │             │ Firewalls│
              └─────┬─────┘             └────┬─────┘
                    │                         │
              ┌─────┴─────┐             ┌─────┴─────┐
              │ Core/Dist.│             │ Core/Dist.│
              │   Layer   │             │   Layer   │
              └─────┬─────┘             └─────┬─────┘
                    │                         │
              Access Layer              Access Layer
                    │                         │
              End Devices                End Devices
```

---

# 🌐 Main Campus Network

The Main Campus contains the organization's primary enterprise infrastructure.

The campus network is divided into multiple functional VLANs and departments.

### Main Campus Departments

* Health & Sciences
* Business
* Engineering
* Arts & Design
* IT
* Administrative Room
* Network Security / Management

Each department has dedicated network resources and is logically separated using VLANs.

---

# 🏢 Branch Campus Network

The Branch Campus provides a separate enterprise network connected to the Main Campus through a secure WAN connection.

The branch contains dedicated networks for:

* Health
* Business
* Engineering
* Arts

Each branch department has its own VLAN and IP subnet.

The branch architecture also includes redundant infrastructure to improve network availability.

---

# 🔀 VLAN Segmentation

Network segmentation is implemented using VLANs to separate users and departments.

Example VLAN design:

| VLAN    | Function                    |
| ------- | --------------------------- |
| VLAN 10 | Health & Sciences           |
| VLAN 20 | Business                    |
| VLAN 30 | Engineering                 |
| VLAN 40 | Arts & Design               |
| VLAN 50 | IT                          |
| VLAN 60 | Administrative / Management |

The actual VLAN IDs and IP addressing are documented in the topology and configuration files.

---

# 🧭 IP Addressing

The network uses structured private IPv4 addressing.

### Main Campus

```text
LAN: 172.16.0.0/16
WAN: 10.10.0.0/16
```

### Branch Campus

```text
LAN: 172.17.0.0/16
WAN: 10.11.0.0/16
```

### Infrastructure / Transit Networks

```text
10.x.x.x
```

The addressing scheme provides logical separation between:

* User networks
* Infrastructure networks
* WAN links
* Security zones
* Management networks

---

# 🔐 Security Architecture

Security is implemented through multiple network layers.

The architecture includes:

* Perimeter Firewalls
* DMZ
* Internal Network Segmentation
* Management Network
* Guest / Security Network
* Site-to-Site VPN
* Controlled Internet Access

The design follows a **Defense-in-Depth** approach.

---

# 🛡️ DMZ Architecture

The Main Campus includes a dedicated **Demilitarized Zone (DMZ)** for publicly accessible services.

The DMZ contains services such as:

* DNS Server
* DHCP Server
* Web Server
* Email Server
* TFTP Server

```text
                    Internet
                       │
                 ┌─────┴─────┐
                 │ Perimeter  │
                 │ Firewall   │
                 └─────┬─────┘
                       │
                    DMZ Zone
                       │
        ┌──────────────┼──────────────┐
        │              │              │
      DNS            WEB           EMAIL
     Server          Server         Server
        │
      DHCP
     Server
        │
      TFTP
     Server
```

The DMZ separates externally accessible services from the internal enterprise network.

---

# 🔥 Perimeter Firewall Design

Both the Main Campus and Branch Campus use perimeter firewall infrastructure.

The design includes redundant firewall devices to reduce single points of failure.

The firewalls provide logical separation between:

```text
Internet
   │
   ▼
Outside Zone
   │
Firewall
   │
Inside / DMZ
```

This architecture allows security policies to be applied between different trust zones.

---

# 🔄 High Availability

High Availability is a major design component of this project.

The Main Campus includes redundant network infrastructure using:

* Dual Core / Multilayer Switches
* Redundant Distribution Paths
* Redundant Firewall Connectivity
* Multiple Uplinks
* HSRP
* LACP
* Parallel Network Paths

The Branch Campus also uses redundant Layer 3 infrastructure.

---

# ⚡ HSRP

**Hot Standby Router Protocol (HSRP)** is used to provide gateway redundancy.

The architecture includes:

```text
                 Virtual Gateway
                      │
              ┌───────┴───────┐
              │               │
          HSRP Active     HSRP Standby
              │               │
           Core/MLS        Core/MLS
```

If the active device becomes unavailable, the standby device can assume the virtual gateway role.

This improves:

* Gateway availability
* Network resilience
* Fault tolerance

---

# 🔗 Link Aggregation

**LACP (Link Aggregation Control Protocol)** is implemented to combine multiple physical links into logical connections.

Benefits include:

* Increased bandwidth
* Link redundancy
* Improved availability
* Reduced impact of individual link failures

The topology demonstrates redundant links between network infrastructure devices.

---

# 🌉 Site-to-Site VPN

A secure **Site-to-Site VPN** connects the Main Campus and Branch Campus.

```text
┌────────────────┐                         ┌────────────────┐
│  Main Campus   │                         │ Branch Campus  │
│                │                         │                │
│    HQ-FW       │=========================│   Branch-FW    │
│                │      Site-to-Site VPN   │                │
└────────────────┘                         └────────────────┘
```

The VPN provides secure communication between private networks across the external/WAN infrastructure.

This design demonstrates the concept of secure enterprise branch connectivity.

---

# 🌍 WAN & Internet Connectivity

The infrastructure includes an ISP/WAN environment connecting:

* Main Campus
* Branch Campus
* Internet
* Cloud Infrastructure

The WAN design provides connectivity between geographically separated enterprise locations.

---

# ☁️ Cloud Integration

The topology includes a simulated Cloud environment containing:

* Oracle VM
* Oracle Server

The cloud segment demonstrates integration between enterprise infrastructure and external/cloud-hosted services.

```text
Enterprise Network
       │
       │ Internet
       ▼
   ISP Network
       │
       ▼
 Cloud Infrastructure
       │
 ┌─────┴─────┐
 │           │
Oracle VM  Oracle Server
```

This component provides a foundation for extending the project toward hybrid enterprise networking.

---

# 🖥️ Network Management & Security

A dedicated management/security segment is included in the architecture.

The management environment can be used for:

* Network administration
* Infrastructure monitoring
* Security management
* Device management
* Troubleshooting

Separating management traffic from normal user traffic improves security and operational control.

---

# 📡 End-User Connectivity

The network supports multiple types of enterprise endpoints:

* Desktop PCs
* Laptops
* Smartphones
* Tablets
* Printers
* Administrative devices

Each department is logically isolated using VLAN segmentation.

---

# 🧩 Technologies & Concepts Demonstrated

## Switching

* VLANs
* Access Ports
* Trunking
* Layer 2 Switching
* Layer 3 Switching
* LACP
* Redundant Uplinks

## Routing

* Inter-VLAN Routing
* Static Routing
* Dynamic Routing Concepts
* WAN Routing
* Default Routing
* Route Redundancy

## High Availability

* HSRP
* Redundant Core
* Redundant Distribution
* Redundant Firewalls
* Multiple Links
* LACP

## Security

* Network Segmentation
* DMZ
* Perimeter Firewalls
* Security Zones
* Management Network
* Site-to-Site VPN
* Defense in Depth

## WAN

* ISP Connectivity
* Site-to-Site VPN
* Branch Connectivity
* Internet Edge

## Cloud

* Cloud Connectivity
* Oracle VM
* Oracle Server
* Hybrid Infrastructure Concepts

---

# 📊 Network Design Principles

The project follows several enterprise architecture principles:

### Scalability

The modular design allows additional departments, VLANs, users, and services to be added without redesigning the entire infrastructure.

### Availability

Redundant devices and links reduce single points of failure.

### Security

Network segmentation, firewalls, DMZ architecture, and VPN connectivity provide multiple layers of protection.

### Performance

LACP and redundant high-speed links provide improved network capacity.

### Manageability

Dedicated management infrastructure provides centralized control and easier troubleshooting.

---

# 🧪 Testing & Verification

The following tests can be performed in the lab:

### Connectivity

```text
ping
traceroute
```

### VLAN Verification

```text
show vlan brief
show interfaces trunk
```

### HSRP Verification

```text
show standby
```

### EtherChannel / LACP Verification

```text
show etherchannel summary
```

### Routing Verification

```text
show ip route
show ip interface brief
```

### DHCP Verification

```text
show ip dhcp binding
show ip dhcp pool
```

These commands can be used to verify the operational state of the infrastructure.

---

# 📁 Recommended Repository Structure

```text
enterprise-campus-branch-network/
│
├── README.md
│
├── diagrams/
│   └── enterprise-campus-branch-topology.png
│
├── packet-tracer/
│   └── enterprise-campus-branch.pkt
│
├── configurations/
│   ├── main-campus/
│   │   ├── core/
│   │   ├── distribution/
│   │   ├── access/
│   │   └── firewall/
│   │
│   ├── branch-campus/
│   │   ├── core/
│   │   ├── distribution/
│   │   ├── access/
│   │   └── firewall/
│   │
│   └── wan/
│
├── documentation/
│   ├── network-architecture.md
│   ├── vlan-design.md
│   ├── ip-addressing.md
│   ├── security-design.md
│   ├── vpn-design.md
│   └── high-availability.md
│
└── screenshots/
    ├── hsrp-verification.png
    ├── vlan-verification.png
    ├── routing-verification.png
    └── vpn-verification.png
```

---

# 🎯 Project Objectives

The main objectives of this project are to demonstrate practical skills in:

* Designing an enterprise campus network
* Designing a branch office network
* Implementing VLAN segmentation
* Implementing Layer 2 and Layer 3 switching
* Designing redundant network infrastructure
* Implementing HSRP
* Implementing LACP
* Designing a secure DMZ
* Connecting branch and headquarters networks
* Designing Site-to-Site VPN connectivity
* Integrating Internet and ISP connectivity
* Integrating cloud infrastructure
* Designing secure network management
* Documenting enterprise network architecture

---

# 🚀 Future Improvements

The project can be extended with additional enterprise and security technologies:

* OSPF Multi-Area
* EIGRP
* BGP
* IPsec VPN
* Advanced Firewall Policies
* ACLs
* NAT/PAT
* DHCP Snooping
* Dynamic ARP Inspection
* Port Security
* STP / RSTP
* QoS
* AAA
* TACACS+
* RADIUS
* SNMP
* Syslog
* NetFlow
* IDS/IPS
* SIEM Integration
* Zero Trust Architecture
* Network Automation with Python
* Netmiko
* Ansible
* NetBox
* Zabbix

---

# 📚 Learning Outcomes

This project provides practical experience in designing and documenting a multi-site enterprise network.

It demonstrates how **Campus Networking, Branch Networking, WAN, Security, High Availability, VPN, DMZ, and Cloud Connectivity** can be integrated into a single enterprise architecture.

The project emphasizes the relationship between:

```text
Architecture
      ↓
Segmentation
      ↓
Routing
      ↓
Security
      ↓
High Availability
      ↓
WAN Connectivity
      ↓
Cloud Integration
      ↓
Monitoring & Management
```

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

**Next Generation Network Engineer**

### Areas of Focus

* Enterprise Networking
* Network Security
* Data Center Networking
* WAN & SD-WAN
* Network Automation
* Python for Network Engineers
* Cybersecurity
* Cloud Networking
* AI & Networking

---

# ⭐ Portfolio Project

This repository is part of my practical **Enterprise Networking & Network Security Portfolio**.

The project is continuously evolving as new technologies, security controls, automation capabilities, and enterprise architecture concepts are introduced.

**Design → Configure → Test → Secure → Document → Automate**
