# Firewall Lab (IPTables, NFTables, IDS/IPS, FreeBSD & ICS Security)

## Overview
This project focuses on firewall configuration, network security, and traffic control across both Linux and FreeBSD environments.
The lab includes implementation of secure firewall policies, attack simulation, IDS/IPS integration, and Windows-based network management.

## Key Features
- Firewall configuration using IPTables and NFTables (Linux)
- PF firewall and IPFW traffic control (FreeBSD)
- Default deny security model with controlled access rules
- Rate limiting for ICMP (DoS mitigation) and SSH (brute force protection)
- Logging and monitoring of blocked traffic
- Network segmentation using LAN, WAN and DMZ zones
- NAT configuration (Masquerading & DNAT)
- Simulation and mitigation of attacks (Nmap, DoS, SSH brute force)

## IDS / IPS Integration
- Integrated Suricata as an IDS/IPS using NFQUEUE
- Deep Packet Inspection (DPI) for detecting malicious traffic
- Detection and blocking of file transfers (e.g. ZIP files)
- Comparison between basic firewall filtering and advanced IPS capabilities

## ICS Network Security
- Designed a segmented ICS network using VLANs and zones (Admin, User, Controller, PLC, DMZ)
- Implemented defense-in-depth architecture
- Restricted communication between critical systems to prevent lateral movement
- Integrated monitoring and detection using Suricata and Wazuh for real-time security visibility

## FreeBSD Firewall & Traffic Control
- Configured PF firewall with default deny policies
- Implemented DoS protection using connection limits and overload tables
- Simulated network conditions using IPFW and Dummynet (latency and bandwidth control)
- Analyzed network performance before and after traffic shaping

## Windows / Active Directory
- Installed and configured Windows Server with Active Directory Domain Services (AD DS)
- Configured NAT using Routing and Remote Access
- Implemented centralized firewall rules using Group Policy (GPO)
- Managed domain clients and enforced security policies across systems
- Tested access control and network restrictions in a domain environment

## Technologies Used
- Linux (Kali, Debian)
- FreeBSD (PF, IPFW, Dummynet)
- Windows Server (Active Directory, GPO)
- IPTables / NFTables
- Suricata (IDS/IPS)
- GNS3
- Wireshark, Nmap, Hydra
- VLAN, NAT, Firewall policies

## Key Learnings
- Implementing secure firewall architectures using default deny principles
- Understanding limitations of packet filtering vs deep inspection (DPI)
- Designing segmented and secure network architectures
- Working with both Linux and FreeBSD firewall technologies
- Managing users and policies in a Windows domain environment
- Detecting and mitigating real-world network attacks
