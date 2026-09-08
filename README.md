# Network Security Portfolio

Practical network and cybersecurity projects completed during my Network Security studies at Folkuniversitetet in Gothenburg.
Each project documents the security objective, architecture, implementation, testing, troubleshooting, and lessons learned.

## Current projects

### Defense-in-Depth ICS Network Security Lab
A segmented ICS/OT security environment built in GNS3 with VLANs, nftables, Suricata inline IPS, NFQUEUE, and Wazuh SIEM. The project focuses on reducing lateral movement toward critical industrial assets and validating segmentation, blocking, and centralized monitoring.

[View project](./projects/ics-network-security/README.md) · [Presentation PDF](./projects/ics-network-security/ics-network-security.pdf)

### Site-to-Site IPSec VPN Security Lab
A Cisco IOSv site-to-site IPSec VPN lab covering IKE negotiation, ESP encryption, NAT exemption, WAN filtering, packet-level verification in Wireshark, Nmap testing, ICMP control-plane protection, SSH hardening, and troubleshooting.

[View project](./projects/cisco-ipsec/README.md) · [Presentation PDF](./projects/cisco-ipsec/cisco-ipsec.pdf)

### Windows Active Directory & GPO Security Lab
A Windows Server 2022 Active Directory lab focused on centralized endpoint security management through Group Policy. The project covers AD DS and DNS, RRAS/NAT, domain-joined clients, centrally deployed Windows Firewall policy, client-side GPO verification, functional testing, and security limitations.

[View project](./projects/windows-ad-gpo/README.md) · [Presentation PDF](./projects/windows-ad-gpo/windows-ad-gpo-security-lab.pdf)

### Windows AppLocker & Group Policy Security Lab
A Windows Server 2022 application-control lab using Local Group Policy, TestUser execution tests, and AppLocker event logs. Covers Path, Publisher and File Hash rules, default-deny behaviour, additional rule collections, recovery, and production limitations.

[View project](./projects/applocker-gpo/README.md) · [Presentation PDF](./projects/applocker-gpo/applocker-gpo-security-lab.pdf) · [Full LaTeX project ZIP](./projects/applocker-gpo/AppLocker-GPO-Portfolio.zip)

## Portfolio direction

The repository will grow with selected security projects rather than every classroom exercise. The focus is on projects that demonstrate practical configuration, validation, troubleshooting, and security reasoning.
