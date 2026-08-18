# Cisco Enterprise Network Lab – OSPF Multi-Area, NAT/PAT & High Availability

## 📌 Project Overview

This project is a comprehensive **Cisco Enterprise Network Lab** designed and implemented in **Cisco Packet Tracer**.

The lab demonstrates the integration of multiple enterprise networking technologies within a single topology, including:

* OSPF Multi-Area
* VLANs
* Inter-VLAN Routing
* Router-on-a-Stick (ROAS)
* NAT/PAT
* DHCP
* DHCP Relay / IP Helper
* VTP
* EtherChannel / Port-Channel
* First Hop Redundancy Protocols (FHRP)
* HSRP / VRRP concepts
* NTP
* Management VLAN
* Static and dynamic IP addressing
* Enterprise LAN and WAN connectivity

The primary objective is to build a realistic enterprise environment where routing, switching, redundancy, address translation, and network services work together.

---

# 🏗️ Network Architecture

The topology consists of three major routing domains:

```text
                         ┌──────────────────┐
                         │     Internet     │
                         └────────┬─────────┘
                                  │
                              ISP Router
                                  │
                              NAT/PAT
                                  │
                           ┌──────┴──────┐
                           │   Edge R1   │
                           └──────┬──────┘
                                  │
                             OSPF Area 0
                         ┌────────┴────────┐
                         │                 │
                      Router R2         Router R3
                         │                 │
                    Area 2 / LAN       Area 1 / LAN
                         │                 │
                    ┌────┴────┐       ┌────┴────┐
                    │ Access  │       │   ROAS  │
                    │ Switches│       │ Network │
                    └────┬────┘       └─────────┘
                         │
                VLANs / End Devices
```

The network is designed around an **OSPF Multi-Area architecture** with Area 0 acting as the backbone.

---

# 🌐 OSPF Multi-Area Architecture

OSPF is the primary dynamic routing protocol used in the lab.

The topology contains:

* **OSPF Area 0**
* **OSPF Area 1**
* **OSPF Area 2**

```text
                 OSPF Area 0
                      │
             ┌────────┴────────┐
             │                 │
         Area 1             Area 2
             │                 │
        VLAN / ROAS       Enterprise LAN
```

### OSPF Router IDs

| Router      | Router ID |
| ----------- | --------- |
| Edge Router | 1.1.1.1   |
| R2          | 2.2.2.2   |
| R3          | 3.3.3.3   |

The design demonstrates:

* OSPF neighbor relationships
* Area 0 backbone
* Inter-area routing
* Route advertisement
* OSPF network statements
* Router ID configuration
* Multi-area enterprise routing

---

# 🔀 VLAN Segmentation

The LAN is segmented using multiple VLANs.

| VLAN    | Purpose                 | Network           |
| ------- | ----------------------- | ----------------- |
| VLAN 10 | User Network            | 192.168.54.0/26   |
| VLAN 20 | User Network            | 192.168.54.64/26  |
| VLAN 30 | Server / Infrastructure | 192.168.54.128/28 |
| VLAN 40 | Web / Application       | 192.168.54.144/28 |
| VLAN 99 | Management              | 192.168.54.160/28 |
| VLAN 2  | Native VLAN             | Native VLAN       |

This segmentation creates separate broadcast domains and provides a foundation for implementing security and access-control policies.

---

# 🧭 Inter-VLAN Routing

Inter-VLAN routing is implemented using multiple approaches.

The topology demonstrates both:

### Layer 3 Switching / SVI

SVIs provide Layer 3 gateways for VLANs in the multilayer switching environment.

```text
VLAN
 │
 ▼
SVI
 │
 ▼
Default Gateway
 │
 ▼
OSPF
```

### Router-on-a-Stick

A router provides inter-VLAN routing through subinterfaces.

```text
                 Router
                    │
                  Trunk
                    │
                 Switch
          ┌─────────┼─────────┐
          │         │         │
       VLAN 10   VLAN 20   VLAN 30
```

This demonstrates how both multilayer switching and ROAS can be used in different parts of an enterprise network.

---

# 🔥 NAT & PAT

The edge router provides connectivity toward the external network using **Network Address Translation**.

The topology separates:

```text
NAT Inside
     │
     ▼
Enterprise LAN
     │
   Router
     │
NAT Outside
     │
     ▼
    ISP
     │
     ▼
 Internet
```

### NAT/PAT Concepts Demonstrated

* NAT Inside
* NAT Outside
* Inside Local
* Inside Global
* PAT / NAT Overload
* NAT boundary
* Private-to-public address translation

This allows internal private addresses to access external networks through the edge router.

---

# 📡 DHCP Services

DHCP is used to dynamically assign IP addresses to client devices.

The topology includes DHCP-enabled VLANs for end-user networks.

DHCP provides:

* IP Address
* Subnet Mask
* Default Gateway
* Network Configuration

Some devices use static IP addressing for infrastructure services.

---

# 🔄 DHCP Relay / IP Helper

The topology demonstrates the use of **DHCP Relay** through the `ip helper-address` mechanism.

This allows clients located in different VLANs or subnets to obtain their DHCP configuration from a centralized DHCP server.

```text
DHCP Client
     │
     ▼
VLAN
     │
     ▼
Router / SVI
     │
 ip helper-address
     │
     ▼
DHCP Server
```

This is an important enterprise networking concept because DHCP broadcast traffic normally does not cross Layer 3 boundaries.

---

# 🔗 EtherChannel / Port-Channel

Multiple physical links are bundled into logical Port-Channels.

The topology contains:

* Port-Channel 1
* Port-Channel 2
* Port-Channel 3
* Additional redundant links

This design improves:

* Link redundancy
* Available bandwidth
* Network resilience
* Infrastructure availability

The lab also demonstrates trunk connectivity across aggregated links.

---

# 🔄 First Hop Redundancy

The topology includes **First Hop Redundancy Protocol (FHRP)** concepts.

The architecture references:

* HSRP
* VRRP

FHRP provides redundant default gateway services.

```text
                  Virtual Gateway
                       │
              ┌────────┴────────┐
              │                 │
          Active Router     Standby Router
              │                 │
              └────── LAN ──────┘
```

The objective is to eliminate a single default-gateway failure point.

---

# 🕐 NTP Infrastructure

The lab includes an **NTP Master** configuration.

The NTP service provides synchronized time information to network devices.

Accurate time synchronization is important for:

* Network troubleshooting
* Log correlation
* Security monitoring
* Event analysis
* Infrastructure management

---

# 🗂️ VTP

The switching environment demonstrates **VLAN Trunking Protocol (VTP)**.

The topology includes:

```text
SW-A → VTP Server

SW-B → VTP Client
SW-C → VTP Client
```

VTP can be used to distribute VLAN information across participating switches.

This lab demonstrates the relationship between:

* VTP
* VLAN databases
* Trunk links
* Access switches

---

# 🖥️ Server Infrastructure

The enterprise network includes several infrastructure servers.

Examples include:

* DNS Server
* DHCP Server
* Web Server
* NTP services

Server networks are separated from normal user networks using dedicated VLANs.

This provides better organization and makes it easier to apply security and access-control policies.

---

# 🛡️ Management Network

A dedicated **Management VLAN** is included in the architecture.

```text
VLAN 99
192.168.54.160/28
```

The management network can be used for:

* Switch management
* Router management
* Network administration
* Monitoring
* Troubleshooting

Separating management traffic from user traffic is an important enterprise security practice.

---

# 🌐 WAN & Edge Connectivity

The edge router connects the internal enterprise network to an external ISP environment.

The topology includes multiple point-to-point networks between routing devices and the ISP.

Example WAN addressing includes:

```text
172.16.4.0/30
172.16.4.4/30
172.16.4.8/30
```

External connectivity includes additional public-facing networks used for ISP and Internet simulation.

---

# 📊 IP Addressing Summary

### OSPF Area 0

```text
172.16.4.0/30
172.16.4.4/30
172.16.4.8/30
```

### OSPF Area 1

```text
192.168.10.0/25
```

### OSPF Area 2

```text
192.168.54.0/26
192.168.54.64/26
```

### Additional Area 2 Networks

```text
192.168.54.128/28
192.168.54.144/28
192.168.54.160/28
```

### Management

```text
192.168.54.160/28
```

The complete IP addressing plan is represented in the topology diagram and configuration files.

---

# 🧩 Technologies & Concepts Demonstrated

## Routing

* OSPF
* OSPF Multi-Area
* OSPF Area 0
* OSPF Area 1
* OSPF Area 2
* Dynamic Routing
* Inter-Area Routing
* Router IDs

## Switching

* VLANs
* Access Ports
* Trunk Ports
* Native VLAN
* SVI
* Layer 2 Switching
* Layer 3 Switching
* EtherChannel
* Port-Channel
* VTP

## High Availability

* FHRP
* HSRP Concepts
* VRRP Concepts
* Redundant Gateway Architecture
* Link Redundancy

## Network Services

* DHCP
* DHCP Relay
* IP Helper Address
* DNS
* NTP
* Web Services

## WAN / Internet

* ISP Connectivity
* NAT
* PAT
* NAT Inside
* NAT Outside
* NAT Boundary

## Network Management

* Management VLAN
* NTP
* Device Management
* Infrastructure Segmentation

---

# 🧪 Verification & Troubleshooting

The following commands can be used to verify the implementation.

### VLANs

```bash
show vlan brief
```

### Trunking

```bash
show interfaces trunk
```

### EtherChannel

```bash
show etherchannel summary
```

### VTP

```bash
show vtp status
```

### SVI

```bash
show ip interface brief
```

### OSPF Neighbors

```bash
show ip ospf neighbor
```

### OSPF Routes

```bash
show ip route ospf
```

### OSPF Information

```bash
show ip ospf
```

### HSRP

```bash
show standby
```

### NAT Translations

```bash
show ip nat translations
```

### NAT Statistics

```bash
show ip nat statistics
```

### DHCP

```bash
show ip dhcp binding
show ip dhcp pool
```

### Connectivity

```bash
ping
traceroute
```

These verification commands help validate routing, switching, redundancy, NAT, DHCP, and overall network connectivity.

---

# 🗺️ Network Topology

The complete topology diagram is available in:

```text
diagrams/
└── cisco-enterprise-ospf-multiarea-nat-ha.png
```

The topology demonstrates:

* OSPF Multi-Area
* VLAN Segmentation
* Layer 3 Switching
* Router-on-a-Stick
* NAT/PAT
* DHCP
* DHCP Relay
* VTP
* EtherChannel
* FHRP
* NTP
* Management VLAN
* ISP Connectivity
* Internet Access

---

# 📁 Recommended Repository Structure

```text
cisco-enterprise-ospf-multiarea-nat-ha-lab/
│
├── README.md
│
├── diagrams/
│   └── cisco-enterprise-ospf-multiarea-nat-ha.png
│
├── packet-tracer/
│   └── enterprise-ospf-multiarea-nat-ha.pkt
│
├── configurations/
│   ├── edge-router/
│   ├── r2/
│   ├── r3/
│   ├── core-switches/
│   ├── access-switches/
│   └── isp/
│
├── documentation/
│   ├── network-architecture.md
│   ├── vlan-design.md
│   ├── ip-addressing.md
│   ├── ospf-multi-area.md
│   ├── nat-pat.md
│   ├── dhcp.md
│   ├── etherchannel.md
│   ├── vtp.md
│   └── fhrp.md
│
└── screenshots/
    ├── ospf-neighbors.png
    ├── routing-table.png
    ├── nat-translations.png
    ├── etherchannel.png
    └── hsrp-status.png
```

---

# 🎯 Project Objectives

The main objectives of this lab are to demonstrate practical skills in:

* Designing an enterprise network
* Implementing OSPF Multi-Area
* Building an OSPF backbone
* Segmenting networks with VLANs
* Implementing Inter-VLAN Routing
* Configuring Router-on-a-Stick
* Implementing NAT/PAT
* Configuring DHCP
* Implementing DHCP Relay
* Configuring VTP
* Implementing EtherChannel
* Designing gateway redundancy
* Implementing FHRP concepts
* Configuring NTP
* Creating a dedicated management network
* Connecting enterprise networks to an ISP
* Troubleshooting enterprise connectivity

---

# 🚀 Future Improvements

The lab can be extended with additional enterprise technologies:

* OSPF Authentication
* OSPF Route Summarization
* OSPF Stub Areas
* EIGRP
* BGP
* HSRP Load Balancing
* VRRP
* STP / RSTP / MST
* LACP Advanced Configuration
* DHCP Snooping
* Dynamic ARP Inspection
* IP Source Guard
* Port Security
* ACLs
* QoS
* AAA
* TACACS+
* RADIUS
* SNMP
* Syslog
* NetFlow
* Zabbix
* Network Automation with Python
* Netmiko
* Ansible

---

# 📚 Learning Outcomes

This lab provides practical experience in integrating multiple Cisco technologies into a single enterprise network.

The project demonstrates the relationship between:

```text
VLAN Segmentation
       ↓
Inter-VLAN Routing
       ↓
OSPF Multi-Area
       ↓
Gateway Redundancy
       ↓
WAN Connectivity
       ↓
NAT/PAT
       ↓
Network Services
       ↓
Enterprise Management
```

It provides a practical foundation for understanding how enterprise networks are designed, configured, verified, and troubleshot.

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

**Next Generation Network Engineer**

### Areas of Focus

* Enterprise Networking
* Cisco Networking
* Network Security
* Routing & Switching
* WAN Technologies
* Data Center Networking
* Network Automation
* Python for Network Engineers
* Cybersecurity
* AI & Networking

---

# ⭐ Portfolio Project

This repository is part of my practical **Cisco Networking & Enterprise Infrastructure Portfolio**.

The lab is continuously evolving as advanced routing, switching, security, automation, and network management technologies are added.

**Design → Configure → Verify → Troubleshoot → Secure → Automate**
