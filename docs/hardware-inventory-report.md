# Hardware Inventory and Assessment Report

## 1. Assessment Information

| Parameter | Details |
|---|---|
| Project | Hardware Support and Troubleshooting Lab |
| Assessment Date | 26 November 2026 |
| Device Type | Laptop |
| Assessment Method | Physical system and software-based diagnostics |
| Operating System | Windows 11 Pro |

## 2. Computer Identification

| Component | Specification |
|---|---|
| Manufacturer | Lenovo |
| Product Family | Legion Y7000 2021 |
| System Model | 82JK |
| System Architecture | x64 |
| Platform Role | Mobile |

### Evidence

![Computer Identification](../screenshots/02-computer-identification.png)

## 3. Processor

| Component | Specification |
|---|---|
| Manufacturer | Intel |
| Processor | Core i7-11800H |
| Generation | 11th Generation |
| Physical Processors | 1 |
| Physical Cores | 8 |
| Logical Processors | 16 |
| Base Clock Speed | 2.30 GHz |
| Architecture | 64-bit |

### Evidence

![Processor Identification](../screenshots/03-processor-identification.png)

## 4. Motherboard

| Component | Specification |
|---|---|
| Manufacturer | Lenovo |
| Product | LNVNB161216 |
| Version | SDK0T76479 WIN |

### Evidence

![Motherboard Identification](../screenshots/04-motherboard-identification.png)

## 5. BIOS and Firmware

| Component | Specification |
|---|---|
| BIOS Manufacturer | Lenovo |
| BIOS Version | H1CN49WW |
| BIOS Release Date | 16 August 2022 |
| BIOS Mode | UEFI |
| SMBIOS Version | 3.3 |
| Embedded Controller Version | 1.49 |
| Secure Boot | Enabled |

### Evidence

![BIOS Identification](../screenshots/05-bios-identification.png)

## 6. Graphics Hardware

| Component | Specification |
|---|---|
| Dedicated Graphics | NVIDIA GeForce RTX 3050 Laptop GPU |

### Evidence

![Graphics Hardware](../screenshots/06-graphics-hardware-identification.png)

## 7. Physical Memory

| Component | Specification |
|---|---|
| Installed RAM | 32 GB |
| Diagnostic Tool | Windows Memory Diagnostic |
| Memory Errors Detected | None |
| Diagnostic Result | Passed |

### Evidence

![RAM Identification](../screenshots/07-ram-identification.png)

![Memory Diagnostics](../screenshots/16-memory-diagnostics.png)

## 8. Storage Hardware

| Component | Specification |
|---|---|
| Drive Model | WD PC SN540 SDDPNPF-1T00 |
| Storage Type | SSD |
| Nominal Capacity | 1 TB |
| System Volume Capacity | 952.17 GiB |
| File System | NTFS |
| Available Space | 214.73 GiB |
| Available Percentage | 22.55% |
| Health Status | Healthy |
| Operational Status | OK |
| File System Errors | None detected |

### Evidence

![Storage Identification](../screenshots/08-storage-identification.png)

![Storage Health](../screenshots/13-storage-health-diagnostics.png)

![Disk Space Analysis](../screenshots/14-disk-space-analysis.png)

## 9. Battery

| Component | Specification |
|---|---|
| Manufacturer | Celxpert |
| Battery Model | L20C4PC1 |
| Chemistry | Lithium Polymer |
| Design Capacity | 80,000 mWh |
| Full Charge Capacity | 63,710 mWh |
| Charge Cycles | 755 |
| Battery Health | 79.64% |
| Capacity Degradation | 20.36% |

### Assessment

The battery exhibits measurable capacity degradation. Continued monitoring is recommended, with replacement considered if battery runtime becomes insufficient.

### Evidence

![Battery Health Diagnostics](../screenshots/15-battery-health-diagnostics.png)

## 10. Peripheral and Device Assessment

Connected hardware and peripheral devices were inspected using PowerShell and Windows Device Manager.

No currently present Plug and Play devices returned a non-OK status during the PowerShell health check.

### Evidence

![Peripheral Identification](../screenshots/09-peripheral-identification.png)

![Device Manager](../screenshots/11-device-manager-inspection.png)

![Hardware Health Check](../screenshots/12-hardware-health-check.png)

## 11. Overall Hardware Assessment

| Hardware Area | Assessment |
|---|---|
| Processor | Identified |
| Motherboard | Identified |
| BIOS and Firmware | Identified |
| Graphics Hardware | Identified |
| Physical Memory | Diagnostic passed |
| SSD | Healthy |
| Storage Capacity | Sufficient at assessment |
| Battery | Monitoring recommended |
| Plug and Play Devices | No non-OK status reported |
| System Stability | Unexpected shutdown investigated |

## 12. Recommendations

- Monitor battery capacity and runtime.
- Maintain sufficient available storage space.
- Review Windows and manufacturer driver updates periodically.
- Monitor for recurring Kernel-Power Event ID 41 incidents.
- Maintain regular backups.
- Repeat hardware diagnostics when performance or stability issues arise.

## Conclusion

The hardware inventory and diagnostic assessment established a baseline of the workstation's configuration and reported health.

No memory errors, file system corruption or physical disk health warnings were detected during the performed tests. Battery degradation and an unexpected shutdown event were identified as areas requiring continued monitoring.

This assessment demonstrates practical hardware identification, asset documentation, diagnostic interpretation and preventive maintenance skills.
