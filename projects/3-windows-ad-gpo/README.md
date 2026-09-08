# Windows Active Directory & GPO Security Lab

## Overview

This project builds and validates a small Windows Active Directory environment in which Windows Server 2022 acts as the domain controller and centrally distributes Windows Firewall policy to managed domain clients through Group Policy.

## Lab architecture

- Windows Server external interface: `192.168.122.36/24`
- Windows Server internal interface: `192.168.137.1/24`
- Windows-1 / CLIENT-1: `192.168.137.10/24`
- Windows-2 / CLIENT-2: `192.168.137.20/24`
- Client gateway and DNS: `192.168.137.1`
- Domain: `lab3.local`

## What was implemented

- Windows Server 2022 with Active Directory Domain Services
- DNS through the domain controller
- RRAS/NAT for client Internet access
- Two domain-joined Windows clients
- Domain-linked `firewall-rules` Group Policy Object
- Centrally managed Windows Firewall outbound policy
- Client-side policy refresh and verification

## Testing and validation

The project validates both policy delivery and actual endpoint behaviour:

- `gpupdate /force` used to refresh computer policy
- `gpresult` confirms that `firewall-rules` is applied to both clients
- Browser testing confirms consistent blocking behaviour on CLIENT-1 and CLIENT-2
- A control test verifies that unrelated websites remain reachable
- CLI connectivity testing confirms that general network access continues to function while the target service is blocked

## Security findings

The lab demonstrates the value of centralized Windows security management:

- A single policy can be distributed consistently to multiple managed endpoints
- Endpoint-side verification confirms whether the intended GPO actually arrived
- Centralized policy reduces the need to configure security settings independently on every client
- Testing from the endpoint perspective is necessary to distinguish configured policy from effective policy

## Limitations and production context

The Google access test used static remote-IP ranges as a practical demonstration of centrally enforced firewall policy. The lab also identified limitations with this method because large Internet services use many addresses and multiple protocols.

For a production environment, additional considerations could include:

- OU-based and security-group policy scoping
- Dedicated network-edge/NAT infrastructure
- Centralized firewall and event logging
- Application- or domain-aware controls where appropriate

These are production design considerations and are not claimed as features implemented in the original lab.

## Presentation

[View the full presentation (PDF)](./windows-ad-gpo-security-lab.pdf)

The presentation contains the architecture, AD DS and domain configuration, RRAS/NAT evidence, GPO deployment, client-side verification, functional testing, limitations, and production-security discussion.
