# Enterprise Multi-Site WAN & Routing Architecture

## 📌 Project Overview

This project is a comprehensive **Enterprise Multi-Site Network Architecture** designed and implemented in **Cisco Packet Tracer**.

The topology simulates a geographically distributed enterprise environment connecting:

* **Headquarters – Abu Dhabi**
* **Branch Office – Yemen**
* **Branch Office – Egypt**
* **Multiple ISP Networks**
* **Internet**
* **Enterprise WAN**
* **GRE Tunnel Connectivity**

The project focuses on enterprise routing, WAN connectivity, high availability, network segmentation, and dynamic routing.

It demonstrates how multiple enterprise sites can be interconnected through different service providers while maintaining redundancy and reliable communication.

---

# 🏗️ Network Architecture

The infrastructure consists of three major enterprise locations:

```text
                         ┌────────────────────┐
                         │      INTERNET      │
                         └─────────┬──────────┘
                                   │
                    ┌──────────────┴──────────────┐
                    │       ISP Infrastructure     │
                    │                              │
                    │   ISP Etisalat / ISP Orange  │
                    └───────┬──────────────┬───────┘
                            │              │
                  ┌─────────┘              └─────────┐
                  │                                  │
          ┌───────▼────────┐                 ┌───────▼────────┐
          │  HQ Abu Dhabi  │                 │ Branch Yemen   │
          │                │                 │                │
          │ Core / Dist.   │                 │ HSRP / VLANs   │
          │ VLANs          │                 │ OSPF           │
          └───────┬────────┘                 └────────────────┘
                  │
                  │ GRE / WAN
                  │
          ┌───────▼────────┐
          │  Branch Egypt  │
          │                │
          │ OSPF           │
          │ ROAS           │
          │ VLANs          │
          └────────────────┘
```

---

# 🌍 Enterprise Sites

## 🇦🇪 Headquarters – Abu Dhabi

The Headquarters represents the primary enterprise site.

It includes:

* Core switches
* Distribution switches
* Access switching
* Multiple VLANs
* Redundant Layer 3 gateways
* HSRP
* OSPF
* Zabbix monitoring
* Server infrastructure
* WAN connectivity
* Multiple ISP connections

The HQ architecture follows a hierarchical enterprise network model.

---

## 🇾🇪 Branch Office – Yemen

The Yemen branch provides a dedicated enterprise branch network.

The branch includes:

* Redundant multilayer switching
* HSRP
* OSPF
* VLAN segmentation
* Access switches
* End-user networks
* Server connectivity
* WAN connectivity

The design provides gateway redundancy and dynamic routing between the branch and the enterprise WAN.

---

## 🇪🇬 Branch Office – Egypt

The Egypt branch is connected to the enterprise WAN and demonstrates a smaller branch-office architecture.

The branch includes:

* Router
* Access switches
* Multiple VLANs
* End-user networks
* OSPF
* Router-on-a-Stick (ROAS)

This provides a practical example of extending enterprise connectivity to a remote office.

---

# 🔀 VLAN Segmentation

VLAN segmentation is used throughout the enterprise to separate different types of traffic.

The topology includes VLANs for:

* User Networks
* Server Networks
* IT / Management
* Departmental Networks

Example VLAN structure:

| VLAN    | Purpose                   |
| ------- | ------------------------- |
| VLAN 10 | User Network              |
| VLAN 20 | User / Department Network |
| VLAN 30 | Server Network            |
| VLAN 40 | IT / Management           |

VLAN segmentation provides:

* Smaller broadcast domains
* Improved security
* Logical separation
* Easier network management
* Better scalability

---

# 🧭 Layer 3 Switching

The Headquarters uses multilayer switches to provide Layer 3 gateway services for VLANs.

SVIs are configured to provide default gateways for internal networks.

Example:

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
Enterprise Routing
```

This allows the campus network to perform inter-VLAN routing without depending entirely on external routers.

---

# 🔄 HSRP High Availability

**Hot Standby Router Protocol (HSRP)** is implemented to provide redundant default gateways.

The topology uses active and standby devices to maintain gateway availability.

```text
                    Virtual IP
                       │
                ┌──────┴──────┐
                │             │
          HSRP Active    HSRP Standby
                │             │
             Core/MLS      Core/MLS
```

If the active gateway becomes unavailable, the standby device can take over the virtual gateway.

### Benefits

* Gateway redundancy
* Improved availability
* Fault tolerance
* Reduced single points of failure

---

# 🌐 OSPF Multi-Area

**OSPF (Open Shortest Path First)** is used as the dynamic routing protocol.

The WAN design demonstrates the use of multiple OSPF areas.

```text
                    OSPF Area 0
                         │
              ┌──────────┼──────────┐
              │          │          │
           Area 1     Area 0      Area 0
              │
          Branch / WAN
```

The topology includes:

* OSPF Area 0
* OSPF Area 1
* Inter-area routing
* Dynamic route exchange
* WAN route propagation

Using OSPF provides:

* Dynamic routing
* Automatic route learning
* Faster convergence
* Scalability
* Reduced manual routing configuration

---

# 🔗 GRE Tunnel

A **Generic Routing Encapsulation (GRE)** tunnel is implemented to provide logical connectivity across the WAN/ISP infrastructure.

```text
┌───────────────┐                       ┌───────────────┐
│ Enterprise    │=======================│ Remote Site   │
│ Router        │       GRE Tunnel      │ Router        │
└───────────────┘                       └───────────────┘
```

The GRE tunnel creates a logical point-to-point path between remote network locations.

### GRE provides

* Logical tunnel connectivity
* Encapsulation of routed traffic
* Support for routing protocols across the tunnel
* Flexible WAN topology

The topology demonstrates GRE as an overlay network over the underlying ISP infrastructure.

---

# 🌐 Multiple ISP Architecture

The enterprise WAN includes multiple ISP environments.

The topology demonstrates connectivity through:

* ISP Etisalat
* ISP Orange
* Internet connectivity

This provides an environment for studying:

* Multi-provider WAN connectivity
* ISP routing
* Redundancy
* Route selection
* WAN failover concepts

---

# ☁️ Internet Connectivity

The enterprise network connects to the Internet through the ISP infrastructure.

The architecture can be represented as:

```text
Enterprise
    │
    ▼
Edge Router
    │
    ▼
ISP
    │
    ▼
Internet
```

This provides external connectivity for enterprise sites while allowing routing and WAN technologies to be tested in a controlled lab environment.

---

# 🔀 Router-on-a-Stick

The Egypt branch demonstrates **Router-on-a-Stick (ROAS)** for inter-VLAN routing.

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

The router uses subinterfaces to provide Layer 3 gateways for multiple VLANs.

This is particularly useful in smaller branch-office environments where a multilayer switch may not be available.

---

# 📡 Network Monitoring

The Headquarters includes a dedicated **Zabbix monitoring environment**.

Zabbix can be used to monitor:

* Network devices
* Interfaces
* Availability
* Performance
* Network traffic
* Infrastructure health

The monitoring architecture demonstrates the importance of operational visibility in enterprise networks.

---

# 🛡️ Network Resilience

The architecture incorporates several redundancy mechanisms:

### Gateway Redundancy

* HSRP

### Routing Redundancy

* OSPF
* Multiple routing paths

### WAN Redundancy

* Multiple ISP connections
* Multiple WAN paths

### Infrastructure Redundancy

* Dual multilayer switches
* Redundant uplinks
* Multiple paths between network layers

These mechanisms reduce the impact of individual device or link failures.

---

# 📊 IP Addressing

The project uses structured IPv4 addressing.

### Headquarters

```text
192.168.0.0/16
```

### Branch Networks

```text
172.16.0.0/16
```

### WAN / Transit Networks

```text
10.x.x.x
```

### GRE / Tunnel Networks

Dedicated point-to-point addressing is used for tunnel connectivity.

The complete addressing information is available in the topology diagram and configuration files.

---

# 🧩 Technologies & Concepts Demonstrated

## Routing

* OSPF
* OSPF Multi-Area
* Inter-Area Routing
* Dynamic Routing
* Route Propagation
* WAN Routing

## Switching

* VLANs
* Trunking
* Access Ports
* Layer 2 Switching
* Layer 3 Switching
* SVI
* Inter-VLAN Routing

## High Availability

* HSRP
* Redundant Core
* Redundant Uplinks
* Multiple WAN Paths
* Multiple ISP Connectivity

## WAN

* ISP Connectivity
* Multi-Site WAN
* GRE
* Point-to-Point Connectivity
* Internet Edge

## Monitoring

* Zabbix
* Network Monitoring
* Infrastructure Visibility

## Branch Networking

* Router-on-a-Stick
* Branch VLANs
* Remote Site Routing
* WAN Connectivity

---

# 🧪 Verification & Troubleshooting

The following Cisco commands can be used to validate the network.

### VLAN Verification

```bash
show vlan brief
show interfaces trunk
```

### SVI Verification

```bash
show ip interface brief
show interfaces vlan
```

### HSRP Verification

```bash
show standby
```

### OSPF Verification

```bash
show ip ospf neighbor
show ip ospf
show ip route ospf
```

### Routing Table

```bash
show ip route
```

### GRE Verification

```bash
show interfaces tunnel
show ip interface brief
```

### Connectivity Testing

```bash
ping
traceroute
```

These commands help verify:

* VLAN operation
* Gateway availability
* OSPF neighbor relationships
* Route propagation
* GRE tunnel status
* End-to-end connectivity

---

# 🗺️ Network Topology

The complete network topology is available in:

```text
diagrams/
└── enterprise-multisite-wan-topology.png
```

The diagram illustrates:

* Abu Dhabi Headquarters
* Yemen Branch
* Egypt Branch
* ISP Etisalat
* ISP Orange
* Internet
* OSPF Areas
* GRE Tunnel
* HSRP
* VLANs
* Layer 3 Switching
* Router-on-a-Stick
* Zabbix Monitoring
* End Devices

---

# 📁 Recommended Repository Structure

```text
enterprise-multisite-wan-routing-lab/
│
├── README.md
│
├── diagrams/
│   └── enterprise-multisite-wan-topology.png
│
├── packet-tracer/
│   └── enterprise-multisite-wan.pkt
│
├── configurations/
│   ├── headquarters/
│   │   ├── core/
│   │   ├── distribution/
│   │   └── access/
│   │
│   ├── branch-yemen/
│   │   ├── routers/
│   │   └── switches/
│   │
│   ├── branch-egypt/
│   │   ├── router/
│   │   └── switches/
│   │
│   └── isp/
│
├── documentation/
│   ├── network-architecture.md
│   ├── vlan-design.md
│   ├── ip-addressing.md
│   ├── ospf-design.md
│   ├── hsrp-design.md
│   ├── gre-tunnel.md
│   └── wan-design.md
│
└── screenshots/
    ├── ospf-neighbors.png
    ├── hsrp-status.png
    ├── routing-table.png
    └── gre-tunnel.png
```

---

# 🎯 Project Objectives

The main objectives of this project are to demonstrate practical enterprise networking skills in:

* Multi-site network architecture
* Enterprise WAN design
* OSPF Multi-Area
* VLAN segmentation
* Layer 3 switching
* HSRP high availability
* GRE tunneling
* Multi-ISP connectivity
* Router-on-a-Stick
* Branch office networking
* Network monitoring
* Infrastructure redundancy
* Network troubleshooting

---

# 🚀 Future Improvements

Future versions of the project can be extended with:

* BGP
* eBGP ISP Peering
* OSPF Authentication
* IPsec over GRE
* DMVPN
* SD-WAN
* NAT/PAT
* ACLs
* QoS
* DHCP Snooping
* Dynamic ARP Inspection
* Port Security
* STP / RSTP
* EtherChannel
* AAA
* TACACS+
* RADIUS
* SNMP
* Syslog
* NetFlow
* IDS/IPS
* SIEM Integration
* Network Automation with Python
* Netmiko
* Ansible
* NetBox
* Zabbix Advanced Monitoring

---

# 📚 Learning Outcomes

This project provides practical experience in designing and troubleshooting a **multi-site enterprise network**.

It demonstrates how:

```text
Campus Networking
       ↓
VLAN Segmentation
       ↓
Layer 3 Switching
       ↓
OSPF Multi-Area
       ↓
WAN / ISP Connectivity
       ↓
GRE Overlay
       ↓
HSRP High Availability
       ↓
Branch Networking
       ↓
Network Monitoring
```

can be integrated into a single enterprise architecture.

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

**Next Generation Network Engineer**

### Areas of Focus

* Enterprise Networking
* Network Security
* WAN & Routing
* Data Center Networking
* Network Automation
* Python for Network Engineers
* Cybersecurity
* Cloud Networking
* AI & Networking

---

# ⭐ Portfolio Project

This repository is part of my practical **Enterprise Networking & Network Engineering Portfolio**.

The project is continuously evolving as advanced routing, WAN, security, automation, monitoring, and cloud networking technologies are introduced.

**Design → Configure → Route → Secure → Monitor → Troubleshoot → Automate**

