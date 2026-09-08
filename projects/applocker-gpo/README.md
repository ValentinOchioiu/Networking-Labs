# Windows AppLocker & Group Policy Security Lab

## Overview

Application control on Windows Server 2022 through Local Group Policy. The lab progressively restricts application execution and validates policy behaviour using a standard TestUser account and AppLocker events.

## Implementation and testing

- Application Identity service and default Windows/administrator rules
- A user-specific Notepad++ Path Deny rule
- Removal of the broad Program Files allowance and selected hash-based allowances
- Publisher rules for mIRC, a SpecialApps path allowance, and a CPU-Z File Hash rule
- Windows Installer, Script and Packaged App rule collections
- Allowed and blocked execution events, plus recovery lessons

Internet Explorer is one example of expected default-deny behaviour after removing the broad Program Files rule. The captured packaged-app default allows all signed packaged apps.

## Evidence and limitations

The 18-slide presentation uses screenshots from LAB 4. CPU-Z screenshots show the File Hash rule and allowed/blocked events, but no raw hash value or hash-condition dialog. No hash value is invented. DLL coverage, trusted-binary proxy execution and broader deployment controls are production context, not lab implementations.

## Presentation and source

- [View presentation (PDF)](./applocker-gpo-security-lab.pdf)
- [Download complete LaTeX project (ZIP)](./AppLocker-GPO-Portfolio.zip)
- [LaTeX source](./applocker-gpo-security-lab.tex)
- [Screenshot provenance](./IMAGE-SOURCES.txt)

Compile twice with `pdflatex applocker-gpo-security-lab.tex` from this directory. TeX Live with Beamer and Source Sans Pro is required. Keep the images directory beside the source.
