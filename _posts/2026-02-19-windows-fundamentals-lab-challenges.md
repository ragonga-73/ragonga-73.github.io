---
title: "Windows Fundamentals Lab Challenges"
date: 2026-02-19 10:00:00 +0000
categories: [Cybersecurity, Windows, Hack The Box]
tags: [windows, hackthebox, enumeration, powershell, wmic, icacls, ntfs, permissions, sid, services, security]
---

# Windows Fundamentals Lab Challenges

## Overview
This document highlights key lab challenges completed during the **Windows Fundamentals** module on Hack The Box. These exercises provided hands-on experience with Windows architecture, user and group management, file systems, permissions, services, processes, and security concepts.

---

## Challenge 1: Identifying Windows Build Number

### Problem Statement
Identify the build number of the Windows workstation.

### Approach
1. Spawned the target machine and connected via RDP using `xfreerdp`.
2. Opened PowerShell on the remote machine.
3. Ran the following command to retrieve OS information:

```powershell
Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber
```

### Tools Used
- `xfreerdp` (Linux RDP client)
- PowerShell

### Screenshot


### Key Lessons Learned
- PowerShell cmdlets like `Get-WmiObject` provide detailed system information.
- Understanding how to query OS details is fundamental for enumeration.

---

## Challenge 2: Finding a Non-Standard Directory and Flag

### Problem Statement
Locate a non-standard directory in the C drive and retrieve the flag.

### Approach
- Navigated to the root directory (`C:\`) using `cd ..`
- Listed directories with the `dir` command.
- Identified a folder named `Academy`.
- Changed into the folder and found `flag.txt`.
- Used `type flag.txt` to display the contents.

### Tools Used
- Command Prompt (CMD)

### Screenshot
https://images/dir-academy.png  
https://images/flag-content.png  
*(Flag: c8fe8d977d3a0c655ed7cf81e4d13c75)*

### Key Lessons Learned
- The `dir` and `type` commands are essential for file system navigation and inspection.
- Non-standard directories often contain sensitive or challenge-related data.

---

## Challenge 3: Identifying Full Control User on C:\Users

### Problem Statement
Determine which system user has Full Control over the `C:\Users` directory.

### Approach
Opened Command Prompt and ran:

```cmd
icacls C:\Users
```

Analyzed the output to find the user with `(F)` (Full Control) permission.

### Tools Used
- Command Prompt (CMD)
- `icacls` utility

### Screenshot


### Key Lessons Learned
- `icacls` is a powerful tool for viewing and modifying NTFS permissions.
- Understanding permission inheritance and explicit entries is critical for security assessments.

---

## Challenge 4: Finding Non-Standard Update Service

### Problem Statement
Identify one non-standard update service running on the host.

### Approach
Opened PowerShell and ran:

```powershell
Get-Service | Where-Object {$_.Name -like "*reader*"} | Format-List
```

Identified `FoxitReaderUpdateService` as the non-standard service.

### Tools Used
- PowerShell

### Screenshot


### Key Lessons Learned
- Non-Microsoft services can be potential attack vectors.
- Filtering services helps in spotting unusual or third-party services.

---

## Challenge 5: Finding Alias for ipconfig.exe

### Problem Statement
Find the alias set for the `ipconfig.exe` command in PowerShell.

### Approach
Opened PowerShell and ran:

```powershell
Get-Alias
```

Located the alias for `ipconfig`, which was `ifconfig`.

### Tools Used
- PowerShell

### Screenshot


### Key Lessons Learned
- PowerShell aliases provide shortcuts for legacy command-line users.
- Understanding aliases helps in transitioning from CMD to PowerShell.

---

## Challenge 6: Finding Execution Policy for LocalMachine Scope

### Problem Statement
Determine the Execution Policy set for the `LocalMachine` scope.

### Approach
Opened PowerShell and ran:

```powershell
Get-ExecutionPolicy -List
```

Observed the policy for `LocalMachine` was `Unrestricted`.

### Tools Used
- PowerShell

### Screenshot


### Key Lessons Learned
- Execution policies control script execution and are a security feature.
- Misconfigured policies can lead to unintended script execution.

---

## Challenge 7: Finding System Serial Number via WMI

### Problem Statement
Use WMI to find the serial number of the system.

### Approach
Opened PowerShell and ran:

```powershell
Get-WmiObject -Class Win32_OperatingSystem | select SystemDirectory, BuildNumber, SerialNumber, Version
```

Retrieved serial number: `00329-10280-00000-AA938`.

### Tools Used
- PowerShell
- WMI

### Screenshot


### Key Lessons Learned
- WMI is a powerful management and enumeration interface.
- Serial numbers and other system details can be retrieved remotely.

---

## Challenge 8: Finding SID for bob.smith User

### Problem Statement
Identify the Security Identifier (SID) for the user `bob.smith`.

### Approach
Opened Command Prompt and ran:

```cmd
wmic useraccount get name,sid
```

Located `bob.smith` and copied the SID.

### Tools Used
- Command Prompt (CMD)
- `wmic` tool

### Screenshot


### Key Lessons Learned
- SIDs uniquely identify users, groups, and computers in Windows.
- `wmic` is a versatile command-line tool for system information.

---

## Challenge 9: Finding Disabled Third-Party Security Application at Startup

### Problem Statement
Identify which third-party security application is disabled at startup for the current user.

### Approach
Opened Command Prompt and ran:

```cmd
reg query HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
```

Identified `NordVPN` as the disabled security application.

### Tools Used
- Command Prompt (CMD)
- `reg` command

### Screenshot


### Key Lessons Learned
- Startup programs are stored in registry keys like `Run` and `RunOnce`.
- Disabled or missing entries can indicate misconfigurations or removals.

---

## Challenge 10: Creating a Secure Shared Folder with Permissions

### Problem Statement
Create a shared folder named **Company Data** with specific permissions for an HR security group, including disabling inheritance and setting both share and NTFS permissions.

### Approach
- Created the **Company Data** folder and HR subfolder.
- Created a user `Jim` and an `HR` security group, then added Jim to the group.
- Configured share permissions: removed `Everyone`, added `HR` with Change and Read.
- Disabled inheritance and set NTFS permissions: Modify, Read & Execute, List folder contents, Read, Write.
- Verified permissions using `icacls`.

### Tools Used
- File Explorer
- Computer Management (`lusrmgr.msc`)
- `icacls`

### Screenshots


### Key Lessons Learned
- Shared folders combine share permissions and NTFS permissions; the most restrictive applies.
- Disabling inheritance prevents unintended access from parent folders.
- Creating dedicated security groups simplifies permission management.

---

## Challenge 11: Identifying Default Group in Share Permissions ACL

### Problem Statement
Name the group that is present in the Company Data share permissions ACL by default.

### Approach
- Opened the Company Data folder properties.
- Navigated to the **Sharing** tab → **Advanced Sharing** → **Permissions**.
- Observed the default entry: `Everyone`.

### Tools Used
- File Explorer

### Screenshot


### Key Lessons Learned
- By default, new shares grant `Everyone` Read access.
- This should be removed or restricted to follow the principle of least privilege.

---

## Challenge 12: Identifying NTFS Permissions Configuration Tab

### Problem Statement
Name the tab that allows you to configure NTFS permissions.

### Approach
- Right-clicked any folder and selected **Properties**.
- Identified the **Security** tab.

### Tools Used
- File Explorer

### Screenshot


### Key Lessons Learned
- The **Security** tab is where NTFS permissions are configured.
- This tab is not visible by default if simple file sharing is enabled.

---

## Challenge 13: Identifying Windows Update Service

### Problem Statement
List the name of the service associated with Windows Update.

### Approach
Opened PowerShell and ran:

```powershell
Get-Service
```

Identified the service `wuauserv` (Windows Update).

### Tools Used
- PowerShell

### Screenshot


### Key Lessons Learned
- Windows Update service is critical for system patching and security.
- Service names often differ from display names.

---

## Challenge 14: Finding SID for User Jim

### Problem Statement
Retrieve the SID associated with the newly created user `Jim`.

### Approach
Opened Command Prompt and ran:

```cmd
wmic useraccount get name,sid
```

Located `Jim` and copied the SID.

### Tools Used
- Command Prompt (CMD)
- `wmic`

### Screenshot


### Key Lessons Learned
- Each new user gets a unique SID.
- SIDs are used internally for all access control decisions.

---

## Challenge 15: Finding SID for HR Security Group

### Problem Statement
List the SID associated with the HR security group.

### Approach
Opened Command Prompt and ran:

```cmd
wmic group get name,sid
```

Located the `HR` group and copied the SID.

### Tools Used
- Command Prompt (CMD)
- `wmic`

### Screenshot


### Key Lessons Learned
- Security groups also have unique SIDs.
- Groups simplify permission assignments across multiple users.

---

## Conclusion

These lab challenges provided a solid foundation in Windows fundamentals, including:

- Enumeration techniques using built-in tools like `wmic`, `icacls`, and PowerShell.
- Security concepts such as SIDs, permissions, and inheritance.
- Hands-on configuration of users, groups, shares, and services.
- Troubleshooting real-world issues like RDP connectivity and permission misconfigurations.

The practical experience gained is directly applicable to system administration, security assessments, and penetration testing in Windows environments.

*Completed as part of Hack The Box Windows Fundamentals module.*
