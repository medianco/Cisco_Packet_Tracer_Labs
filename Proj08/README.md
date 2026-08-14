# Cisco Enterprise Department Network with Voice VLAN, DHCP & Inter-VLAN Routing

## 📌 Project Overview

This project is a **Cisco Enterprise Network Lab** designed and implemented in **Cisco Packet Tracer**.

The topology simulates a multi-department enterprise network with separate **Data VLANs and Voice VLANs**, centralized server services, DHCP configuration, Inter-VLAN Routing using **Router-on-a-Stick**, and IP Phone connectivity.

The project demonstrates practical implementation of enterprise networking concepts including:

* VLAN segmentation
* Inter-VLAN Routing
* Router-on-a-Stick
* DHCP
* Voice VLAN
* Cisco IP Phones
* DHCP Option 150
* TFTP-based IP Phone provisioning
* Departmental network segmentation
* Point-to-point router links
* Centralized server infrastructure

---

# 🏢 Network Architecture

The network is divided into multiple business departments:

* Finance Department
* ICT Department
* Sales Department
* HR Department
* Server Room

Each department has its own **Data VLAN** and dedicated **Voice VLAN**.

```text
                         ┌──────────────────┐
                         │   Server Room     │
                         │   DATA VLAN 50    │
                         │                  │
                         │ DHCP / DNS / WEB │
                         │ EMAIL / SERVICES │
                         └────────┬─────────┘
                                  │
                           ┌──────┴──────┐
                           │ ICT Router  │
                           └──────┬──────┘
                                  │
                     ┌────────────┼────────────┐
                     │            │            │
                FIN Router    HR Router    SALES Router
                     │            │            │
              ┌──────┘            │            └──────┐
              │                   │                   │
        Finance Dept.          HR Dept.          Sales Dept.
        Data + Voice           Data + Voice       Data + Voice
```

---

# 🏷️ VLAN Design

The project uses dedicated VLANs for data and voice traffic.

| VLAN     | Purpose        | Network            |
| -------- | -------------- | ------------------ |
| VLAN 10  | Finance Data   | 192.168.100.0/27   |
| VLAN 20  | HR Data        | 192.168.100.32/27  |
| VLAN 30  | Sales Data     | 192.168.100.64/27  |
| VLAN 40  | ICT Data       | 192.168.100.96/27  |
| VLAN 50  | Server Network | 192.168.100.128/29 |
| VLAN 100 | Finance Voice  | 172.16.100.0/27    |
| VLAN 100 | HR Voice       | 172.16.100.32/27   |
| VLAN 100 | Sales Voice    | 172.16.100.64/27   |
| VLAN 100 | ICT Voice      | 172.16.100.96/27   |

> The voice networks use dedicated IP subnets per department while maintaining a common Voice VLAN ID in the departmental access segments.

---

# 🔀 Inter-VLAN Routing

Inter-VLAN communication is implemented using the **Router-on-a-Stick** architecture.

Each router uses logical subinterfaces to provide Layer 3 gateways for the connected VLANs.

Conceptually:

```text
                  Router
                    │
              Trunk Interface
                    │
              ┌─────┴─────┐
              │  Switch   │
              └─────┬─────┘
                    │
          ┌─────────┼─────────┐
          │         │         │
       VLAN 10   VLAN 100   VLAN 50
        DATA       VOICE     SERVER
```

Router subinterfaces provide:

* Default Gateway
* Inter-VLAN Routing
* DHCP relay where required
* Layer 3 connectivity between network segments

---

# ☎️ Voice VLAN & Cisco IP Phones

One of the main objectives of this lab is to demonstrate **Cisco IP Phone deployment** using dedicated Voice VLANs.

Each department contains multiple IP Phones connected through the access switch.

The topology separates:

```text
Data Traffic
      +
Voice Traffic
```

using dedicated VLAN configuration.

A typical access port can support both:

* Data VLAN → PC
* Voice VLAN → IP Phone

This allows a PC to connect through the IP Phone while voice traffic remains logically separated from normal data traffic.

---

# 📡 DHCP for Voice Networks

DHCP is used to dynamically assign IP addresses to Cisco IP Phones.

The DHCP configuration includes:

* IP address allocation
* Default gateway
* Voice network
* DHCP excluded addresses
* DHCP Option 150

Example concept:

```text
DHCP Pool
    │
    ├── Network
    ├── Default Gateway
    └── Option 150
             │
             ▼
          TFTP Server
             │
             ▼
        Cisco IP Phone
```

---

# ⚙️ DHCP Option 150

**DHCP Option 150** is used to provide Cisco IP Phones with the address of the **TFTP server** used for phone configuration and provisioning.

This allows IP Phones to discover the TFTP service and retrieve their configuration files.

Example:

```text
option 150 ip 172.16.100.1
```

The actual TFTP address depends on the configured Voice Gateway in each department.

---

# 🖥️ Server Room

The topology contains a dedicated **Server Room** connected to the ICT network.

The server infrastructure includes services such as:

* DHCP Server
* DNS Server
* Web Server
* Email Server

The server segment is separated using **VLAN 50**.

Example addressing:

```text
Server Network:
192.168.100.128/29
```

The server network provides centralized services to the enterprise environment.

---

# 🌐 Router-to-Router Connectivity

The departmental routers are interconnected using point-to-point networks.

The topology uses private transit networks such as:

```text
10.10.10.0/30
10.10.10.4/30
10.10.10.8/30
```

These links provide Layer 3 connectivity between the routers.

This design allows departments to communicate with:

* Other departments
* Centralized servers
* Voice services
* Network infrastructure

---

# 🏦 Department Networks

## Finance Department

**Data VLAN:** VLAN 10

**Network:**

```text
192.168.100.0/27
```

**Voice Network:**

```text
172.16.100.0/27
```

The Finance department contains multiple PCs and Cisco IP Phones.

---

## 👥 HR Department

**Data VLAN:** VLAN 20

**Network:**

```text
192.168.100.32/27
```

**Voice Network:**

```text
172.16.100.32/27
```

The HR department provides separate data and voice connectivity for employees.

---

## 💼 Sales Department

**Data VLAN:** VLAN 30

**Network:**

```text
192.168.100.64/27
```

**Voice Network:**

```text
172.16.100.64/27
```

The Sales network contains multiple workstations and Cisco IP Phones.

---

## 💻 ICT Department

**Data VLAN:** VLAN 40

**Network:**

```text
192.168.100.96/27
```

**Voice Network:**

```text
172.16.100.96/27
```

The ICT department provides access to the centralized server infrastructure.

---

# 🔐 Network Segmentation

The project applies logical segmentation to separate:

```text
Finance
   │
   ├── Data
   └── Voice

HR
   │
   ├── Data
   └── Voice

Sales
   │
   ├── Data
   └── Voice

ICT
   │
   ├── Data
   └── Voice

Servers
   │
   └── Server VLAN
```

This architecture improves:

* Security
* Broadcast-domain control
* Network organization
* Troubleshooting
* Scalability
* Traffic management

---

# 🧪 Technologies & Concepts Demonstrated

### Switching

* VLANs
* Access Ports
* Trunk Ports
* Voice VLAN
* MAC Address Learning
* Layer 2 Switching

### Routing

* Inter-VLAN Routing
* Router-on-a-Stick
* Router Subinterfaces
* Default Gateways
* Point-to-Point Routing

### DHCP

* DHCP Pools
* DHCP Excluded Addresses
* Default Gateway Assignment
* DHCP Option 150
* Voice DHCP

### VoIP

* Cisco IP Phones
* Voice VLAN
* TFTP
* DHCP Option 150
* Voice Gateway

### Network Design

* Departmental Segmentation
* Centralized Services
* Dedicated Server Network
* Point-to-Point Router Links
* Enterprise Network Architecture

---

# 📊 IP Addressing Summary

## Data Networks

```text
VLAN 10
192.168.100.0/27

VLAN 20
192.168.100.32/27

VLAN 30
192.168.100.64/27

VLAN 40
192.168.100.96/27

VLAN 50
192.168.100.128/29
```

## Voice Networks

```text
Finance Voice
172.16.100.0/27

HR Voice
172.16.100.32/27

Sales Voice
172.16.100.64/27

ICT Voice
172.16.100.96/27
```

## Router Transit Networks

```text
10.10.10.0/30
10.10.10.4/30
10.10.10.8/30
```

---

# 🗺️ Network Topology

The complete topology is available here:

```text
diagrams/
└── enterprise-department-network.png
```

The diagram illustrates:

* Finance Department
* HR Department
* Sales Department
* ICT Department
* Server Room
* Routers
* Switches
* PCs
* Cisco IP Phones
* Data VLANs
* Voice VLANs
* DHCP
* TFTP
* Server Infrastructure
* Router-to-Router Links

---

# 📁 Recommended Repository Structure

```text
cisco-enterprise-voice-vlan-lab/
│
├── README.md
│
├── diagrams/
│   └── enterprise-department-network.png
│
├── packet-tracer/
│   └── enterprise-voice-vlan.pkt
│
├── configurations/
│   ├── finance-router.txt
│   ├── hr-router.txt
│   ├── sales-router.txt
│   ├── ict-router.txt
│   └── switches/
│
├── documentation/
│   ├── vlan-design.md
│   ├── ip-addressing.md
│   ├── dhcp-design.md
│   └── voice-vlan.md
│
└── screenshots/
    ├── vlan-verification.png
    ├── dhcp-verification.png
    └── ip-phone-registration.png
```

---

# 🎯 Project Objectives

The main objectives of this project are to demonstrate practical skills in:

* Designing a departmental enterprise network
* Implementing VLAN segmentation
* Configuring Inter-VLAN Routing
* Implementing Router-on-a-Stick
* Configuring DHCP
* Deploying Cisco IP Phones
* Implementing Voice VLANs
* Understanding DHCP Option 150
* Integrating TFTP services
* Connecting multiple routers
* Designing centralized server infrastructure
* Troubleshooting enterprise network connectivity

---

# 🚀 Possible Future Improvements

The project can be extended with additional enterprise technologies, including:

* OSPF
* EIGRP
* HSRP / VRRP
* EtherChannel
* STP / RSTP
* DHCP Snooping
* Dynamic ARP Inspection
* Port Security
* ACLs
* QoS for Voice
* Voice Gateway / CME
* AAA
* SNMP
* Syslog
* Network Monitoring
* Network Automation with Python
* Ansible
* Netmiko

---

# 📚 Learning Outcomes

After completing this project, the learner gains practical experience with the relationship between **Layer 2 switching, Layer 3 routing, DHCP, VLAN segmentation, and Voice over IP**.

The project demonstrates how an enterprise network can be structured into separate logical domains while still providing controlled communication between departments and centralized services.

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

**Next Generation Network Engineer**

### Areas of Interest

* Enterprise Networking
* Network Security
* Cisco Networking
* Data Center Networking
* Network Automation
* Python for Network Engineers
* Cybersecurity
* AI & Networking

---

## ⭐ Portfolio Project

This project is part of my practical **Cisco Networking & Enterprise Infrastructure Portfolio**.

The goal is to continuously expand the lab with advanced routing, switching, security, voice, automation, and network management technologies.

**Build. Configure. Test. Document. Automate.**
