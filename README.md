# windows-defensive-stack-AD-GPO-Sysmon-Wazuh-
Windows Defensive Security Lab with AD Hardening, Sysmon, Wazuh SIEM, LAPS, VLAN segmentation, and Firewall Security. A complete SOC-focused home lab for monitoring, detection engineering, and enterprise defense.
# SOC Defensive Lab: Active Directory Hardening & Monitoring

A professional lab demonstrating **Windows AD hardening, GPO management, Sysmon logging, Wazuh monitoring, LAPS, firewall rules, and VLAN segmentation**.  
This lab simulates a realistic enterprise defensive environment for SOC analysts.

---

## Badges
![Windows Server](https://img.shields.io/badge/OS-Windows-blue)
![Wazuh](https://img.shields.io/badge/SIEM-Wazuh-orange)
![Sysmon](https://img.shields.io/badge/Logging-Sysmon-green)
![AD Hardening](https://img.shields.io/badge/AD-Hardening-red)

---

## Table of Contents
1. [Overview](#overview)
2. [Lab Architecture](#lab-architecture)
3. [Setup Steps](#setup-steps)
   - [Domain Controller Setup](#domain-controller-setup)
   - [OU & User Management](#ou-and-user-management)
   - [GPO Hardening](#gpo-hardening)
   - [Sysmon Deployment](#sysmon-deployment)
   - [Wazuh Integration](#wazuh-integration)
   - [LAPS Deployment](#laps-deployment)
   - [VLAN Segmentation](#vlan-segmentation)
4. [Verification](#verification)
5. [Screenshots](#screenshots)
6. [Conclusion](#conclusion)

---

## Overview
This lab demonstrates a professional **defensive security stack**:

- Active Directory hardening via Group Policy Objects (GPO)  
- Sysmon deployment for endpoint process/event logging  
- Wazuh SIEM integration for centralized monitoring and alerting  
- LAPS for secure local admin password management  
- Firewall rules enforcement  
- VLAN segmentation for network isolation  

---

## Lab Architecture

| Component        | Role                                       |
|-----------------|--------------------------------------------|
| **DC01**         | Windows Server 2022 - Domain Controller   |
| **WinClient01**  | Test workstation for GPO, LAPS, Sysmon    |
| **Wazuh Manager**| Centralized SIEM and alerting             |
| **Network**      | VLAN-segmented virtual network             |

**Screenshot placeholder:** `/docs/screenshots/network_topology.png`

---

## Setup Steps

### Domain Controller Setup
1. Installed **Windows Server 2022**.
2. Added **Active Directory Domain Services (AD DS)** role.
3. Promoted to new forest: `lab.local`.
4. Rebooted and verified domain status.

**Screenshot placeholder:** `/docs/screenshots/dc-promotion.png`

**Verification Commands:**
```powershell
Get-ADDomain
nslookup lab.local
whoami
