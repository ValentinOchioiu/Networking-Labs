# Site-to-Site IPSec VPN Security Lab

## Overview

This project implements and validates a Cisco IOSv site-to-site IPSec VPN between two private networks across an untrusted WAN.

## Lab addressing

- Site A LAN: `192.168.1.0/24`
- Router A LAN: `192.168.1.1`
- Router A WAN: `192.168.122.70`
- Site B LAN: `10.0.0.0/24`
- Router B LAN: `10.0.0.1`
- Router B WAN: `192.168.122.147`

## What was implemented

- IKEv1 peer negotiation
- AES-256 encryption
- SHA-256 IKE integrity
- Diffie-Hellman Group 14
- IPSec ESP tunnel mode
- Policy-based crypto maps
- Interesting-traffic ACLs
- NAT exemption
- WAN filtering
- Control Plane Policing for ICMP flood protection
- VTY ACLs for SSH management hardening

## Testing and validation

The project includes direct proof rather than relying on connectivity alone:

- Active IKE and IPSec Security Associations
- Increasing encryption/decryption packet counters
- End-to-end connectivity testing
- Wireshark capture of ESP traffic across the WAN
- Comparison with visible internal TCP traffic
- Nmap scanning from the WAN and through the VPN
- ICMP flood testing with `hping3`
- CoPP before/after counters
- SSH exposure testing before and after VTY restrictions

## Troubleshooting

The project documents several real configuration issues encountered during the lab:

- VPN traffic being NATed before matching the crypto ACL
- Incorrect VPN peer addressing
- Unexpected ACL behaviour caused by packet-processing order before and after IPSec decryption

## Modern production context

The lab intentionally uses a classic Cisco policy-based IPSec design. The presentation also discusses modern alternatives without claiming they were implemented, including:

- IKEv2
- Certificate-based authentication
- Route-based VPNs using VTIs
- Stronger integrity / AEAD algorithms
- Next-generation firewalls for post-decryption inspection, IDS/IPS, DPI, application-aware policy, and centralized logging

## Presentation

The final presentation PDF will be added to this project after export from the LaTeX source.
