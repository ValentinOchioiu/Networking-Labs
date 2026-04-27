# Server Administration (Security, Monitoring & Storage)

## Overview
This project focuses on server administration in Linux and Windows environments, covering system configuration, security hardening, monitoring, and storage management. 
The lab includes implementation of IDS/IPS, brute-force protection, application control, and RAID-based storage solutions.

## Key Features
- Intrusion Detection and Prevention using Suricata (IDS/IPS)
- Brute-force protection using Fail2Ban
- Application control in Linux using AppArmor
- Application whitelisting in Windows using AppLocker & Group Policies
- Secure remote access with SSH and 2FA
- RAID-5 configuration with mdadm
- Logical Volume Management (LVM)
- Disk encryption using LUKS
- Network monitoring and attack analysis using Wireshark

## Security Implementation

### Suricata (IDS/IPS)
- Configured Suricata for real-time network monitoring
- Deep Packet Inspection to analyze traffic content
- Created custom Snort-based rules for attack detection
- Detection of SMB brute-force attacks using packet signatures

Example:
- Detection based on SMB Session Setup (0x73)
- Identification of failed logins using NT Status (0xC000006D)

Traffic patterns were analyzed in Wireshark before rule creation to ensure accurate detection and reduce false positives.


### Fail2Ban (Brute-force Protection)
- Configured Fail2Ban to monitor system logs
- Implemented SSH protection with automatic IP banning
- Threshold-based blocking (5 failed attempts)

Key result:
- Attacking host (Kali) was automatically banned after repeated failed login attempts
- Verified through logs and active jail status

- Integrated with Suricata logs for advanced automated response
- Blocking extended to firewall level for full access restriction


### AppArmor (Linux Application Control)
- Created custom AppArmor profiles for applications (cowsay, lnav, nmap)
- Used complain mode for testing and enforce mode for restriction
- Controlled file access and system capabilities

Example:
- Restricted `nmap` by denying `net_raw` capability
- Prevented advanced scans (SYN/UDP scans)
- Allowed only necessary file and system access


### AppLocker & Group Policies (Windows Security)
- Implemented application control using Group Policy
- Created default allow rules for system stability
- Applied **default deny model** for application execution

Rule types used:
- Path-based rules
- Hash-based rules
- Publisher-based rules

Example:
- Blocked specific applications for selected users
- Allowed only trusted applications in controlled directories


## Storage & System Configuration

### RAID-5 (mdadm)
- Configured RAID-5 array for redundancy and performance
- Combined multiple disks into a single logical storage unit
- Tested disk expansion and rebuild process

### LVM (Logical Volume Management)
- Created volume groups and logical volumes on top of RAID
- Enabled flexible storage management and resizing
- Extended storage dynamically without downtime

### Disk Encryption (LUKS)
- Implemented LUKS encryption on logical volumes
- Added multiple encryption keys for flexibility
- Ensured secure data storage at rest

### Secure Access (SSH + 2FA)
- Configured SSH login with two-factor authentication
- Integrated Google Authenticator
- Enabled rate-limiting to mitigate brute-force attacks

## Technologies Used
- Linux (Ubuntu Server, Debian)
- FreeBSD (basic system management)
- Windows Server (Group Policy, AppLocker)
- Suricata (IDS/IPS)
- Fail2Ban
- AppArmor
- mdadm (RAID)
- LVM
- LUKS Encryption
- Wireshark
- GNS3 / Virtual environments


## Key Learnings
- Implementing layered security (IDS/IPS + automated response)
- Understanding real-world attack patterns through traffic analysis
- Creating custom detection rules based on packet inspection
- Applying least privilege principles in Linux and Windows
- Managing secure storage using RAID, LVM and encryption
- Hardening systems against brute-force and unauthorized access
- Troubleshooting system, network, and security configurations
