# Routing (Static, Dynamic Routing & Network Services)

## Overview
This project focuses on routing, switching, and network services in a simulated enterprise environment using Cisco IOS devices.
The lab covers both static and dynamic routing, NAT, DHCP, and network security concepts through practical implementation and testing.

## Key Features
- Static routing between multiple networks
- Dynamic routing protocols: RIP, OSPF and EIGRP
- Network segmentation using subnets and VLAN concepts
- NAT (Network Address Translation) for internet access
- DHCP configuration and IP address management
- ACL (Access Control Lists) for traffic filtering and security
- PXE boot and TFTP configuration
- Simulation of real-world network attacks (DHCP starvation, rogue DHCP)

## Routing Implementation

### Static Routing
- Manual route configuration
- Address planning using /24 and /30 networks
- Point-to-point network design for router communication
- Full connectivity verified with ping and traceroute

### Dynamic Routing
- Implementation and comparison of:
  - RIP (distance-vector)
  - OSPF (link-state)
  - EIGRP (hybrid)

- Tested:
  - Route convergence
  - Failover behavior
  - Load balancing

Key observations:
- RIP: slow convergence (~30s)
- OSPF: fast convergence (1–2s)
- EIGRP: fastest (<1s, using DUAL algorithm)

(Observed during link failure simulations where traffic was automatically rerouted through alternative paths)

## Network Services

### NAT Configuration
- PAT (overload) for internet access
- Internal networks translated to public IP
- ACL used to define allowed internal hosts

### DHCP & PXE
- DHCP server configured on switch
- PXE boot using TFTP server (Kali Linux)
- Automatic OS deployment over network

### Security Implementation
- DHCP Snooping to prevent starvation and rogue attacks
- ACLs for traffic filtering (HTTP/HTTPS only, DNS allowed)
- Basic DDoS mitigation concepts (SYN flood observation)

## Technologies Used
- Cisco IOS (Routers & Switches)
- GNS3
- Linux (Kali)
- Wireshark
- Routing Protocols: RIP, OSPF, EIGRP
- NAT, DHCP, ACL

## Key Learnings
- Understanding differences between static and dynamic routing
- Designing scalable and segmented networks
- Implementing and comparing routing protocols in real scenarios
- Configuring secure network services (DHCP, NAT, ACL)
- Identifying and mitigating common network attacks
- Troubleshooting using tools like ping, traceroute and Wireshark
