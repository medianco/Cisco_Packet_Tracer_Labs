# Device Configurations

This directory contains the configuration files for all network devices used in this Cisco Packet Tracer lab.

Each configuration file represents the running configuration of a specific router, Layer 3 switch, or Layer 2 switch within the network topology.

## Purpose

The configuration files are provided to:

- Document the complete device configurations.
- Make it easier to review and understand the network setup.
- Assist in troubleshooting and verification.
- Serve as a reference for learning Cisco IOS configuration.
- Support future network automation projects using Python, Netmiko, NAPALM, or pyATS.

## Directory Structure

```text
configurations/
│
├── HQ-Router.txt
├── Branch-Router.txt
├── HQ-MLS.txt
├── Branch-MLS.txt
├── IT-SW.txt
├── MLOCS-SW.txt
├── MER-SW.txt
├── MRM-SW.txt
├── HR-SW.txt
├── Finance-SW.txt
└── ...
```

## Configuration Contents

Each file may include:

- Hostname
- Interface Configuration
- IP Addressing
- VLAN Configuration
- Trunk Ports
- Inter-VLAN Routing (SVI)
- Static or Dynamic Routing
- DHCP Configuration
- NAT Configuration
- VPN Configuration
- Access Control Lists (ACLs)
- Security Settings
- Management Configuration

## How to Use

1. Open the required configuration file.
2. Review the Cisco IOS commands.
3. Compare the configuration with the network topology.
4. Apply the configuration to a Cisco device or Packet Tracer lab if needed.
5. Verify the configuration using Cisco IOS verification commands.

## Notes

- All configuration files are intended for educational purposes.
- Device names correspond to the network topology shown in the project documentation.
- Configuration files may be updated as the project evolves.
