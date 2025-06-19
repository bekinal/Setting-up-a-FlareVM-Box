# Installing FLARE VM on a Windows Machine

## Overview

This lab documents the process of installing FLARE VM on a Windows Enterprise machine, setting up a secure analysis environment suitable for dynamic and static malware examination.

## Prerequisites

- A Windows 10 or Windows 11 Enterprise/Professional machine with administrative privileges. I used VirtualBox for this lab. 
- Internet connectivity for downloading required packages  
- PowerShell version 5.1 or higher (comes preinstalled on Windows 10+)  
- Approximately 70+ GB of free disk space  
- Patience — the installation can take upwards of 4 hours depending on system and network speed. I got stuck on the Windows startup screen for 2+ hours. Just be patient. 

**Note:** My VM was built with 4GB of RAM, 2 CPUs and 100GB storage. This is not necessary, but runs pretty smooth. 

---

## Installation Steps

**Important Notice: Take a snapshot of your machine before running the below commands. It's a pain to lose a perfectly good VM due to a bad installation.**

Launch PowerShell **as Administrator** and run the following command to allow script execution:

```powershell
Set-ExecutionPolicy Unrestricted -Scope Process
```
Confirm the change if prompted.

Next, download the FLARE VM installation script from the official FireEye GitHub repository:

```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/fireeye/flare-vm/master/installer/Install-FLAREVM.ps1 -OutFile Install-FLAREVM.ps1
```
Run the installer script:

```powershell
.\Install-FLAREVM.ps1
```
The script will begin installing dozens of tools including debuggers, disassemblers, memory analysis utilities, and network monitoring tools.

The installation will prompt for reboots; allow them as needed and rerun the script after reboot until installation completes.

## Verify Installation
Once complete, you should see a new FLARE VM start menu folder containing hundreds of analysis tools, as well as a free cool background change. 

![image](https://github.com/user-attachments/assets/c75024cc-4a0f-430c-93b5-7ecf385a187e)


**Important Notice: Take a snapshot of your machine as soon you confirmed that the installation was successful.**

Open a command prompt or PowerShell window and run a tool like x64dbg or Wireshark to verify proper installation.

Tools Included (Highlights)
- x64dbg and OllyDbg — Debuggers for malware analysis
- IDA Pro Freeware — Disassembler and reverse engineering tool
- PEiD and DIE — Executable packer detectors
- Process Hacker — Advanced process viewer and memory editor
- Volatility Framework — Memory forensics toolkit
- Sysinternals Suite — Collection of Windows system utilities
- Wireshark — Network protocol analyzer
- Many, many more

---

### The Importance of FlareVM for SOC Analysts
- Provides a safe sandbox environment to analyze malware without risking the host system or network
- Speeds up incident response with pre-installed, curated tools
- Enables dynamic and static analysis workflows crucial for understanding malware behavior
- Helps SOC analysts develop deeper threat intelligence and forensic investigation capabilities


**Important Notice: Before executing any malware sample on your system, ENSURE THAT THE NETWORK IS DISCONNECTED. Malware is growing in complexity each day, and has the ability to traverse hypervisors and infect your host machine if the network is not properly configured**

That's it! Enjoy your new malware analysis VM! 
