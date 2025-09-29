# Setup-and-Use-a-Firewall-on-Windows-Linux
Report: Setup and Use of Firewall on Windows

Introduction

This report outlines the process of setting up and using the Windows Defender Firewall, a built-in security feature in Windows operating systems. The firewall controls incoming and outgoing network traffic to protect the system from unauthorized access and cyber threats.

Firewall Setup on Windows

Access Windows Firewall by opening Settings, then navigate to Update & Security > Windows Security > Firewall & network protection.

Select the active network profile (Domain, Private, or Public).

Enable Microsoft Defender Firewall by toggling it on for the selected profile. This activation ensures protection based on the network environment.
# Firewall-Setup-Windows-Linux

This repository documents step-by-step setup and usage for **Windows Defender Firewall** (Windows) and **UFW / iptables** (Linux).  
Intended for students, sysadmins and security enthusiasts.

## Contents
- `Windows/` — GUI & PowerShell steps, advanced rules, logs, screenshots.
- `Linux/` — UFW quickstart, iptables examples, persistence, screenshots.
- `Comparison/` — Windows vs Linux comparison table.
- `Reports/` — Printable reports: Windows, Linux, Combined.

## Quick start
# Windows — Firewall Setup & Usage

## GUI: enable firewall
1. Open **Settings** → **Windows Security** → **Firewall & network protection**.
2. Select your active profile (Domain / Private / Public).
3. Toggle **Microsoft Defender Firewall** to **On**.

## Allow an app through the firewall (GUI)
- Open **Control Panel** → **System and Security** → **Windows Defender Firewall** → **Allow an app or feature through Windows Defender Firewall**.
- Tick the app and choose Private/Public.

## Advanced: Windows Defender Firewall with Advanced Security
- Run `wf.msc` (Start → run `wf.msc`) to open the advanced console.
- Create inbound/outbound rules based on Program, Port, Protocol, or IP addresses.

## PowerShell examples (run As Administrator)
```powershell
# enable firewall for all profiles
Set-NetFirewallProfile -Profile Domain,Private,Public -Enabled True

# allow inbound HTTP (port 80)
New-NetFirewallRule -DisplayName "Allow HTTP Inbound" -Direction Inbound -Protocol TCP -LocalPort 80 -Action Allow

# allow a program
New-NetFirewallRule -DisplayName "Allow MyApp" -Direction Inbound -Program "C:\Program Files\MyApp\myapp.exe" -Action Allow

# block a remote IP
New-NetFirewallRule -DisplayName "Block BadIP" -Direction Inbound -RemoteAddress 203.0.113.45 -Action Block

# list rules (basic)
Get-NetFirewallRule | Format-Table -AutoSize


Usage and Management

To allow trusted applications through the firewall, use the Allow an app through firewall option and select the appropriate applications and network access types.

For advanced configurations, open the Windows Defender Firewall with Advanced Security console by running wf.msc.

Create custom inbound or outbound rules based on programs, ports, protocols, or IP addresses to manage traffic more precisely.

These rules help specify which network communications are permitted or blocked, enhancing system security.

Best Practices

Regularly review firewall rules to avoid accidentally blocking essential services or applications.

Monitor firewall logs to detect unusual or unauthorized access attempts.

Avoid disabling the firewall unless necessary, as it increases system vulnerability.

Conclusion Windows Defender Firewall serves as a vital component of network security on Windows systems. Proper setup and diligent management of firewall rules protect the system from unauthorized network access and potential threats. This report emphasizes the importance of using the firewall effectively to maintain robust security tailored to different network environments.
