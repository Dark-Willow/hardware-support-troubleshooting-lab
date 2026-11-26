# Hardware Support and Troubleshooting Lab

## Project Overview

This hands-on IT Support lab demonstrates hardware identification, system diagnostics, troubleshooting, corrective maintenance and post-repair verification on a physical Windows 11 workstation.

The project involved 21 practical steps, including real-world troubleshooting incidents and documented diagnostic evidence.

## Lab Environment

| Component | Specification |
|---|---|
| Manufacturer | Lenovo |
| System Model | Legion Y7000 2021 (82JK) |
| Processor | Intel Core i7-11800H |
| CPU Cores | 8 |
| Logical Processors | 16 |
| Operating System | Windows 11 Pro |
| Storage | 1 TB SSD |
| BIOS Mode | UEFI |
| Secure Boot | Enabled |

## Tools and Technologies

- Windows PowerShell 5.1
- Windows Device Manager
- Windows System Information
- CIM and WMI
- Windows Event Logs
- Windows Memory Diagnostic
- CHKDSK
- System File Checker (SFC)
- Deployment Image Servicing and Management (DISM)
- Windows Battery Report

## Practical Skills Demonstrated

- Hardware inventory and identification
- Device and driver diagnostics
- Storage health and capacity monitoring
- Battery health assessment
- Memory fault detection
- Administrative privilege troubleshooting
- Windows Event Log analysis
- File system integrity verification
- Windows component store repair
- Root cause investigation
- Post-repair verification
- Technical documentation

## Diagnostic Results

| Diagnostic Area | Result |
|---|---|
| Device Health | No reported PnP errors |
| SSD Health | Healthy |
| Available Storage | 22.55% |
| Battery Health | 79.64% |
| Memory Diagnostic | No errors detected |
| File System Integrity | Passed |
| Component Store | Repaired and verified |
| Final System Integrity | Passed |

## Troubleshooting Cases

### Case 1: Battery Degradation

Battery diagnostics identified a 20.36% reduction in original battery capacity after 755 charge cycles.

Recommendation: Monitor battery performance and consider replacement when runtime becomes insufficient.

### Case 2: CHKDSK Access Denied

CHKDSK initially failed because the PowerShell session lacked administrative privileges.

Resolution: Launched an elevated PowerShell session and successfully completed the file system scan.

Status: Resolved.

### Case 3: Kernel-Power Event ID 41

Event Log analysis identified an unexpected shutdown. Further investigation included examining crash indicators, power-button information and correlating event timestamps.

Status: Investigated. Root cause remains unconfirmed.

### Case 4: Windows Component Store Corruption

DISM detected repairable Windows component store corruption.

Resolution:
- Executed DISM RestoreHealth.
- Performed a follow-up DISM health scan.
- Executed a final SFC scan.

Verification confirmed that no component store corruption or protected system file integrity violations were detected.

Status: Resolved and verified.

## Project Documentation

| Document | Description |
|---|---|
| [Hardware Inventory Report](docs/hardware-inventory-report.md) | Detailed hardware specifications and health assessment |
| [Troubleshooting Case Reports](docs/troubleshooting-case-reports.md) | Four real technical incidents, investigations and resolutions |
| [Diagnostic Commands Reference](docs/diagnostic-commands-reference.md) | PowerShell commands and Windows diagnostic utilities |
| [Final Assessment and Recommendations](docs/final-assessment-and-recommendations.md) | Diagnostic findings, risk assessment and preventive maintenance plan |
| [Practical Evidence](screenshots/) | Screenshots documenting the practical lab |

## Key Project Achievements

- Completed 21 practical diagnostic steps.
- Documented four real technical incidents.
- Resolved administrative permission issues.
- Successfully repaired Windows component store corruption.
- Verified repairs through follow-up diagnostic scans.
- Produced comprehensive technical documentation.

## Project Status

- Practical assessment: Completed
- Technical documentation: Completed
- Identified repairable issues: Resolved and verified
- Outstanding concerns: Monitoring recommended


## Conclusion

This project demonstrates practical IT Support and Service Desk competencies through hardware assessment, structured troubleshooting, system maintenance and evidence-based verification on a physical Windows workstation.
