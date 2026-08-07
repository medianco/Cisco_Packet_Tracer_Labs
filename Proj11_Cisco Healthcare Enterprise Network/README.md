# Cisco Healthcare Enterprise Network Lab

## 📖 Overview

This project is a comprehensive **Cisco Healthcare Enterprise Network Lab** that simulates the network infrastructure of a modern hospital or healthcare organization.

The topology combines enterprise networking, network security, wireless infrastructure, cloud integration, and healthcare department segmentation using Cisco technologies. It provides a realistic environment for learning, testing, and validating enterprise networking concepts deployed in production healthcare environments.

The network is designed with scalability, redundancy, high availability, and security in mind while integrating on-premises services with cloud resources.

---

# 🏥 Network Architecture

The enterprise network consists of the following components:

- AWS Cloud Integration
- Internet Service Provider (ISP)
- Perimeter Firewall
- DMZ Network
- WAN Router
- Core Layer (Collapsed Core)
- Access Layer
- Wireless Infrastructure
- Voice Network
- Enterprise Server Infrastructure
- Hospital Departments

The architecture follows Cisco best practices for secure enterprise campus deployments.

---

# ☁️ Cloud Integration

The topology includes an AWS cloud environment connected securely to the enterprise network.

Cloud resources include:

- Virtual Servers
- Administrative Workstation
- Cloud Router
- Private Cloud Network

This integration demonstrates hybrid cloud connectivity between on-premises infrastructure and cloud services.

---

# 🌐 Core Technologies

## Layer 2

- VLAN Segmentation
- IEEE 802.1Q Trunking
- EtherChannel (LACP)
- Rapid PVST+
- VTP
- Layer 2 Redundancy

---

## Layer 3

- Inter-VLAN Routing
- OSPF Dynamic Routing
- HSRP Gateway Redundancy
- Static Routing
- Default Route
- Layer 3 Switching

---

# 🔥 Security Infrastructure

The security architecture includes:

- Cisco Perimeter Firewall
- DMZ Network
- Secure Internet Edge
- Public Server Isolation
- Network Segmentation
- Secure Internal Services

The DMZ protects public-facing services while isolating them from the internal healthcare network.

---

# 🖥️ DMZ Services

The DMZ hosts enterprise services including:

- Web Server
- DNS Server
- DHCP Server
- FTP Server

These services provide controlled external access while maintaining internal network security.

---

# 🏢 Internal Services

Internal enterprise services include:

- DHCP
- DNS
- Wireless LAN Controller (WLC)
- Voice Gateway
- Network Administration Workstation

These services support centralized network management and enterprise operations.

---

# 📶 Wireless Infrastructure

The wireless deployment includes:

- Cisco Wireless LAN Controller (WLC)
- Lightweight Access Points
- Wireless Clients
- Centralized WLAN Management

The solution provides seamless wireless connectivity across the healthcare campus.

---

# ☎️ Voice Network

The enterprise voice infrastructure includes:

- Cisco IP Phones
- Dedicated Voice VLAN
- Voice Gateway
- Voice over IP (VoIP)

This enables reliable communication between hospital departments.

---

# 🏥 Hospital Departments

The network is segmented into dedicated VLANs for different departments:

- Pharmacy
- Medical Laboratory
- Reception
- Finance
- Human Resources
- Information Technology (IT)
- Network Administration

Each department includes:

- Desktop PCs
- Laptops
- Network Printers
- Cisco IP Phones
- Wireless Devices
- Lightweight Access Points

---

# 🌐 VLAN Design

The infrastructure uses multiple VLANs, including:

- Management VLAN
- Pharmacy VLAN
- Medical Laboratory VLAN
- Reception VLAN
- Finance VLAN
- Human Resources VLAN
- IT Department VLAN
- Voice VLAN
- Wireless Management VLAN
- DMZ VLAN

This segmentation improves security, traffic isolation, and network performance.

---

# ♻️ High Availability

To ensure continuous network operation, the lab implements:

- Dual Core Multilayer Switches
- HSRP Gateway Redundancy
- OSPF Dynamic Routing
- EtherChannel (LACP)
- Redundant Core Links
- Multiple Uplinks

These mechanisms eliminate single points of failure and increase network resilience.

---

# 🎯 Learning Objectives

This project provides practical experience with:

- Enterprise Campus Network Design
- Cisco Routing & Switching
- Healthcare Network Architecture
- Hybrid Cloud Connectivity
- Firewall Deployment
- Wireless Networking
- Cisco Voice Technologies
- VLAN Design
- High Availability
- Enterprise Security
- Network Troubleshooting

---

# 🛠️ Technologies Demonstrated

- Cisco IOS
- Multilayer Switching
- VLANs
- Inter-VLAN Routing
- OSPF
- HSRP
- EtherChannel (LACP)
- Rapid PVST+
- VTP
- Cisco Firewall
- Wireless LAN Controller
- Lightweight Access Points
- VoIP
- DHCP
- DNS
- AWS Connectivity

---

# 🚀 Purpose

This repository showcases the design and implementation of a secure, scalable, and highly available healthcare enterprise network.

It serves as a hands-on learning project and professional portfolio demonstrating practical experience with Cisco Enterprise networking, cloud integration, network security, wireless technologies, and enterprise infrastructure.

---

# 👨‍💻 Author

**Mohammed AL-Dubai**

### 🎯 Focus Areas

- Enterprise Networking
- Network Engineering
- Cybersecurity
- Cloud Networking
- Network Automation
- AI in Networking

---

> **A complete Cisco Healthcare Enterprise Network Lab integrating cloud services, enterprise security, wireless networking, and high availability into a modern healthcare infrastructure.**