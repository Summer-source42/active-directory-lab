# 🏢 Active Directory Blue Team Lab with Splunk, Sysmon & Attack Simulation

This project is a hands-on lab environment built to simulate a small enterprise network. It includes an Active Directory domain, logging infrastructure using Splunk and Sysmon, and an attacker machine for red-team-style simulations. The goal is to build detection skills, understand log flows, and practice offensive/defensive security techniques in a contained environment.

---

## 🌐 Network Overview

- **Network Range:** `192.168.10.0/24`
- **Domain:** `x.local`

### 🧱 Lab Components

| Role              | OS              | IP Address        | Description |
|-------------------|------------------|--------------------|-------------|
| **Domain Controller** | Windows Server 2019 | `192.168.10.7`     | AD DS, DNS, Sysmon + Splunk UF |
| **Splunk Server**     | Ubuntu Server 20.04  | `192.168.10.10`    | Splunk Core for SIEM |
| **Windows 10 Client** | Windows 10 Pro       | DHCP (e.g. `.20`)  | Domain-joined, Sysmon + Splunk UF |
| **Kali Linux**        | Kali Rolling         | `192.168.10.250`   | Attacker machine (BloodHound, CME, Impacket) |
| **Router**            | pfSense/Generic      | `192.168.10.1`     | Internet gateway, DHCP |
| **Switch**            | Layer 2 switch       | N/A                | Connects all devices |

---

## 🗺️ Lab Diagram

![Lab Topology](architecture/ActivieDirectory.png)

---

## 🎯 Project Objectives

- Set up a working AD domain with DNS
- Configure endpoint logging with Sysmon
- Forward logs to Splunk using Universal Forwarder
- Simulate common attacks and analyze detection patterns
- Document the setup, configurations, and attack paths

---

## ⚙️ Tools Used

- **Sysmon** – Endpoint telemetry
- **Splunk + UF** – Log collection and SIEM
- **BloodHound** – AD recon
- **CrackMapExec** – Lateral movement & enumeration
- **Impacket** – Credential attacks (e.g., Pass-the-Hash, DCSync)

---

## 🛠️ Setup Summary

### Domain Controller (Windows Server)
- Installed Active Directory Domain Services
- Promoted to Domain Controller: `x.local`
- Installed and configured Sysmon (with SwiftOnSecurity config)
- Installed Splunk Universal Forwarder and connected to Splunk server

### Windows 10 Client
- Joined domain `x.local`
- Installed Sysmon and Splunk UF
- Received IP via DHCP

### Splunk Server (Ubuntu)
- Installed Splunk Enterprise
- Created index and added WinEventLog inputs
- Verified log flow from endpoints

### Kali Linux (Attacker)
- Used tools: BloodHound, CrackMapExec, Impacket, mimikatz
- Connected to domain and performed:
  - Kerberoasting
  - DCsync
  - Lateral movement
- Collected logs and analyzed them in Splunk

---
