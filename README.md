# Network Security Portfolio

Practical network and cybersecurity projects completed during my Network Security studies at Folkuniversitetet in Gothenburg.
Each project documents the security objective, architecture, implementation, testing, troubleshooting, and lessons learned.

## Current projects

### 1. Defense-in-Depth ICS Network Security Lab
A segmented ICS/OT security environment built in GNS3 with VLANs, nftables, Suricata inline IPS, NFQUEUE, and Wazuh SIEM. The project focuses on reducing lateral movement toward critical industrial assets and validating segmentation, blocking, and centralized monitoring.

[View project](./projects/1-ics-network-security/README.md) · [Presentation PDF](./projects/1-ics-network-security/ics-network-security.pdf)

### 2. Site-to-Site IPSec VPN Security Lab
A Cisco IOSv site-to-site IPSec VPN lab covering IKE negotiation, ESP encryption, NAT exemption, WAN filtering, packet-level verification in Wireshark, Nmap testing, ICMP control-plane protection, SSH hardening, and troubleshooting.

[View project](./projects/2-cisco-ipsec/README.md) · [Presentation PDF](./projects/2-cisco-ipsec/cisco-ipsec.pdf)

### 3. Windows Active Directory & GPO Security Lab
A Windows Server 2022 Active Directory lab focused on centralized endpoint security management through Group Policy. The project covers AD DS and DNS, RRAS/NAT, domain-joined clients, centrally deployed Windows Firewall policy, client-side GPO verification, functional testing, and security limitations.

[View project](./projects/3-windows-ad-gpo/README.md) · [Presentation PDF](./projects/3-windows-ad-gpo/windows-ad-gpo-security-lab.pdf)

### 4. Windows AppLocker & Group Policy Security Lab
A Windows Server 2022 application-control lab using Local Group Policy, TestUser execution tests, and AppLocker event logs. Covers Path, Publisher and File Hash rules, default-deny behaviour, additional rule collections, recovery, and production limitations.

[View project](./projects/4-applocker-gpo/README.md) · [Presentation PDF](./projects/4-applocker-gpo/applocker-gpo-security-lab.pdf)

### 5. Linux AppArmor & SSH MFA Security Lab

Linux security-hardening lab focused on AppArmor application confinement, SSH multi-factor authentication, audit-driven policy refinement, and targeted restriction of privileged Nmap raw-socket scanning.

[View project](./projects/5-AppArmor/README.md) · [Presentation PDF](./projects/5-AppArmor/apparmor-security-lab.pdf)

## Portfolio direction

The repository will grow with selected security projects rather than every classroom exercise. The focus is on projects that demonstrate practical configuration, validation, troubleshooting, and security reasoning.
