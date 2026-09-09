# Linux AppArmor & SSH MFA Security Lab

## Overview

Linux security-hardening lab focused on application confinement, SSH multi-factor authentication, and restriction of privileged network-scanning behaviour.

The project was performed in an isolated Ubuntu environment using AppArmor to create and refine application security profiles. The lab also strengthened SSH authentication with password and authenticator-code verification and implemented a targeted restriction on Nmap raw-socket scanning.

The objective was to preserve required application functionality while limiting unnecessary access and privileged operations.

## Implementation and testing

### AppArmor application confinement

* Verified AppArmor status, loaded profiles, and enforcement modes
* Compared `complain` and `enforce` modes
* Installed and used `apparmor-utils` for profile management
* Created a custom profile for `/usr/games/cowsay`
* Used `aa-logprof` to review application access and refine policy rules
* Generated a missing profile for `/usr/bin/lnav`
* Tested `lnav` against `/var/log/syslog`
* Reloaded and validated modified AppArmor profiles

The lab used an audit-driven workflow where application behaviour and log events were reviewed before refining security policies.

### SSH multi-factor authentication

SSH authentication was strengthened using PAM and time-based one-time passwords.

The configuration included:

* PAM integration through `/etc/pam.d/sshd`
* `pam_google_authenticator.so`
* SSH PAM integration
* Keyboard-interactive authentication
* Google Authenticator enrollment
* Password and authenticator verification-code authentication
* Rate limiting and prevention of one-time-code reuse

Sensitive MFA information such as QR codes, shared secrets, and recovery codes was intentionally excluded from the documentation.

### Nmap confinement with AppArmor

A custom AppArmor profile was created for:

```text
/usr/bin/nmap
```

The profile was configured with required application resources such as:

```text
/usr/share/nmap/** r,
/usr/bin/nmap mr,
/proc/*/net/dev r,
```

A targeted restriction was then introduced:

```text
deny capability net_raw,
```

The purpose was not to completely block Nmap, but to restrict scanning techniques that require raw-socket access.

## Troubleshooting and policy refinement

Initial enforcement caused Nmap to report:

```text
Nmap: cannot find interface ens5
```

Audit-log analysis showed denied access to:

```text
/proc/<PID>/net/dev
```

The AppArmor profile was corrected with:

```text
/proc/*/net/dev r,
```

This restored access to the required network-interface information while retaining the intended raw-socket restriction.

This demonstrated a practical AppArmor troubleshooting workflow:

```text
Create profile
    ↓
Test application
    ↓
Observe failure
    ↓
Inspect audit logs
    ↓
Refine policy
    ↓
Reload and retest
```

## Nmap scan validation

Two different scan behaviours were tested.

An unprivileged scan:

```bash
nmap -Pn <target>
```

completed successfully using normal TCP connections.

A privileged SYN scan:

```bash
sudo nmap -sS <target>
```

failed because the scan required raw-socket access that was denied by the AppArmor policy.

This demonstrated that basic Nmap functionality could remain available while a specific privileged operation was restricted.

## Audit-log verification

The blocked SYN scan generated AppArmor denial events containing fields such as:

```text
apparmor="DENIED"
profile="/usr/bin/nmap"
operation="create"
sock_type="raw"
```

The logs confirmed that AppArmor denied raw-socket creation.

The audit event did not explicitly isolate `net_raw` as the sole blocking rule, so the evidence is interpreted conservatively as confirmation of raw-socket denial rather than a capability-specific denial event.

## Security concepts demonstrated

* AppArmor Mandatory Access Control
* Application confinement
* Least-privilege policy design
* `complain` and `enforce` modes
* Audit-driven policy refinement
* Linux capabilities
* Raw-socket restrictions
* PAM authentication
* TOTP multi-factor authentication
* SSH hardening
* Security-control validation
* Linux audit-log analysis
* Troubleshooting restrictive security policies

## Evidence and limitations

The presentation includes terminal evidence demonstrating:

* AppArmor status and loaded profiles
* `cowsay` profile creation and refinement
* `lnav` profile generation and testing
* `aa-logprof` policy refinement
* PAM and SSH MFA configuration
* Authenticator enrollment
* SSH password and verification-code prompts
* Nmap profile creation and enforcement
* Nmap interface-access troubleshooting
* Successful unprivileged scanning
* Blocked privileged SYN scanning
* AppArmor raw-socket denial events

The SSH capture shows the password and verification-code prompts but does not show the final authenticated shell.

The Nmap test demonstrates restriction of a privileged TCP SYN scan using `-sS`. It does not demonstrate a complete Nmap execution ban or a separate UDP-scanning test.

## Security result

The lab combines stronger authentication with Linux process confinement.

A key lesson from the project is that security controls must be tested in both directions: legitimate operations should continue to work while the specific operation targeted by the policy should be denied.

## Presentation

View the full presentation (PDF):

[apparmor-security-lab.pdf](./apparmor-security-lab.pdf)
