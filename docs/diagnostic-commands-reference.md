# PowerShell and Windows Diagnostic Commands Reference

## Overview

This document provides a technical reference for Windows hardware identification, system diagnostics, troubleshooting and corrective maintenance using PowerShell and native Windows utilities.

## 1. Hardware Identification

### Computer Information

```powershell
Get-CimInstance Win32_ComputerSystem
```

Purpose: Identifies the computer manufacturer, model and system configuration.

### Processor Identification

```powershell
Get-CimInstance Win32_Processor
```

Purpose: Identifies processor specifications, cores and logical processors.

### Motherboard Identification

```powershell
Get-CimInstance Win32_BaseBoard
```

Purpose: Retrieves motherboard manufacturer and product information.

### BIOS Identification

```powershell
Get-CimInstance Win32_BIOS
```

Purpose: Retrieves BIOS manufacturer, version and release information.

### Graphics Hardware

```powershell
Get-CimInstance Win32_VideoController
```

Purpose: Identifies installed graphics adapters.

### Physical Memory

```powershell
Get-CimInstance Win32_PhysicalMemory
```

Purpose: Retrieves installed RAM specifications, capacity and speed.

### Storage Identification

```powershell
Get-PhysicalDisk
```

Purpose: Identifies physical storage devices.

### Peripheral Identification

```powershell
Get-PnpDevice -PresentOnly
```

Purpose: Lists currently present Plug and Play devices.

## 2. Windows Management Utilities

### System Information

```powershell
msinfo32
```

Purpose: Displays comprehensive hardware and operating system information.

### Device Manager

```powershell
devmgmt.msc
```

Purpose: Inspects installed hardware, drivers and device configuration.

## 3. Hardware Health Diagnostics

### Device Error Detection

```powershell
Get-PnpDevice -PresentOnly |
Where-Object {$_.Status -ne "OK"} |
Format-Table Status, Class, FriendlyName -AutoSize
```

Purpose: Identifies currently present devices reporting a non-OK status.

### Physical Disk Health

```powershell
Get-PhysicalDisk |
Format-Table FriendlyName, MediaType, HealthStatus, OperationalStatus, Size -AutoSize
```

Purpose: Checks physical storage health and operational status.

### Disk Space Analysis

```powershell
Get-Volume | Where-Object DriveLetter |
Select-Object DriveLetter, FileSystem, HealthStatus,
@{Name="TotalGiB";Expression={[math]::Round($_.Size/1GB,2)}},
@{Name="FreeGiB";Expression={[math]::Round($_.SizeRemaining/1GB,2)}},
@{Name="FreePercent";Expression={[math]::Round(($_.SizeRemaining/$_.Size)*100,2)}} |
Format-Table -AutoSize
```

Purpose: Identifies storage capacity, available space and utilisation.

### Battery Health Report

```powershell
powercfg /batteryreport /output "$env:USERPROFILE\battery-report.html"
```

Open the generated report:

```powershell
Invoke-Item "$env:USERPROFILE\battery-report.html"
```

Purpose: Assesses battery capacity, degradation and charge cycles.

Battery health calculation:

Full charge capacity / Design capacity x 100

## 4. Memory Diagnostics

### Launch Windows Memory Diagnostic

```powershell
mdsched.exe
```

Purpose: Tests physical memory for potential errors.

Requirement: Computer restart.

### Retrieve Memory Diagnostic Results

```powershell
Get-WinEvent -FilterHashtable @{
    LogName='System'
    ProviderName='Microsoft-Windows-MemoryDiagnostics-Results'
} -MaxEvents 1 |
Format-List TimeCreated, Id, Message
```

Purpose: Retrieves the most recent memory diagnostic result.

## 5. Administrative Privileges

### Launch Elevated PowerShell

```powershell
Start-Process powershell -Verb RunAs
```

Purpose: Opens PowerShell with administrative privileges after UAC approval.

Useful when troubleshooting permission-related command failures.

## 6. File System Diagnostics

### Online File System Scan

```powershell
chkdsk C: /scan
```

Purpose: Checks the NTFS file system for logical errors and corruption.

Requirement: Administrative privileges.

## 7. Windows Event Log Analysis

### Hardware-Related Event Filtering

```powershell
Get-WinEvent -FilterHashtable @{
    LogName='System'
    StartTime=(Get-Date).AddDays(-30)
    Level=1,2,3
} -ErrorAction SilentlyContinue |
Where-Object {
    $_.ProviderName -match 'WHEA|Disk|Ntfs|storahci|stornvme|Kernel-Power'
} |
Select-Object -First 20 TimeCreated, Id, LevelDisplayName, ProviderName |
Format-Table -AutoSize
```

Purpose: Identifies up to 20 recent critical events, errors and warnings from selected hardware-related providers.

### Kernel-Power Investigation

```powershell
Get-WinEvent -FilterHashtable @{
    LogName='System'
    Id=41
    ProviderName='Microsoft-Windows-Kernel-Power'
} -MaxEvents 1 |
Format-List TimeCreated, Id, Message
```

Purpose: Investigates unexpected shutdown events.

### Detailed Event Data Analysis

```powershell
$event = Get-WinEvent -FilterHashtable @{
    LogName='System'
    Id=41
    ProviderName='Microsoft-Windows-Kernel-Power'
} -MaxEvents 1

([xml]$event.ToXml()).Event.EventData.Data |
Format-Table Name, '#text' -AutoSize
```

Purpose: Examines detailed event properties, including crash and power-related indicators.

### Shutdown Event Correlation

```powershell
Get-WinEvent -FilterHashtable @{
    LogName='System'
    StartTime=[datetime]'2026-11-26T18:30:00'
    EndTime=[datetime]'2026-11-26T19:00:00'
    Id=1,12,13,41,42,109,1001,1074,1201,6005,6006,6008
} |
Sort-Object TimeCreated |
Format-Table TimeCreated, Id, ProviderName -AutoSize
```

Purpose: Correlates startup, shutdown and diagnostic events chronologically.

Note: Event IDs must be interpreted alongside their provider names.

## 8. Windows System Integrity and Repair

### System File Checker

```powershell
sfc /scannow
```

Purpose: Scans protected Windows system files and repairs detected integrity violations where possible.

### DISM Component Store Health Scan

```powershell
DISM /Online /Cleanup-Image /ScanHealth
```

Purpose: Detects Windows component store corruption.

### DISM Component Store Repair

```powershell
DISM /Online /Cleanup-Image /RestoreHealth
```

Purpose: Repairs Windows component store corruption.

### Post-Repair Verification

```powershell
DISM /Online /Cleanup-Image /ScanHealth
sfc /scannow
```

Purpose: Verifies component store health and protected system file integrity following repair.

## 9. Troubleshooting Best Practices

- Identify the problem before implementing corrective action.
- Collect diagnostic evidence.
- Verify administrative privileges when required.
- Distinguish symptoms from confirmed root causes.
- Document error messages accurately.
- Verify successful repairs through follow-up diagnostics.
- Protect sensitive system information before publishing screenshots.
- Document unresolved issues and recommend further investigation.

## Conclusion

These commands demonstrate practical Windows administration, hardware diagnostics, system troubleshooting, corrective maintenance and technical investigation skills relevant to IT Support and Service Desk environments.
