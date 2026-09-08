# Defense-in-Depth ICS Network Security Lab

## Overview

This project is based on the security lessons of the 2010 Stuxnet attack and explores how layered network controls can reduce lateral movement toward critical ICS/PLC systems.

## Environment

- GNS3 lab environment
- VLAN-based segmentation
- Debian firewall/router
- nftables default-deny firewalling
- Suricata inline IDS/IPS through NFQUEUE
- Wazuh SIEM for centralized monitoring

## Security zones

- VLAN 10 — SecAdmin
- VLAN 20 — User
- VLAN 30 — ICS / Controller
- VLAN 40 — PLC
- VLAN 50 — DMZ

## What was implemented

- VLAN segmentation and trunking
- Default-deny firewall policies
- Explicit inter-zone traffic rules
- Suricata custom IPS signatures
- Inline traffic blocking
- Wazuh correlation and alerting
- Validation of segmentation violations and scan activity

## Evidence included in the presentation

The presentation uses screenshots from the real lab environment, including the GNS3 topology, switch VLAN configuration, nftables rules, Suricata signatures, Wazuh alerts, and Wireshark payload inspection.

## Key lesson

Segmentation alone is not enough. The strongest result came from combining segmentation, enforcement, intrusion prevention, and centralized monitoring as a defense-in-depth architecture.

## Presentation

[View the full presentation (PDF)](./ics-network-security.pdf)

The presentation contains the complete lab architecture, implementation evidence, firewall and IPS configuration, Wazuh monitoring results, and validation of the defense-in-depth design.
