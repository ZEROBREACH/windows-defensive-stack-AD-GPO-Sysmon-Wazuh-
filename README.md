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

<img width="1843" height="856" alt="image" src="https://github.com/user-attachments/assets/54693d83-58d2-430c-9ef1-10cb766705fe" />


---

## Setup Steps

### Domain Controller Setup
1. Installed **Windows Server 2022**.
2. Added **Active Directory Domain Services (AD DS)** role.
3. Promoted to new forest: `lab.local`.
4. Rebooted and verified domain status.

<img width="1023" height="723" alt="Screenshot 2025-12-01 132746" src="https://github.com/user-attachments/assets/821aeb5d-0c94-451b-9885-3c11e115e6bd" />


**Verification Commands:**
```powershell
Get-ADDomain
nslookup lab.local
whoami
```
<img width="987" height="592" alt="image" src="https://github.com/user-attachments/assets/94b2cdfb-cebc-451a-b3a0-686d00ac3b0c" />
<img width="306" height="57" alt="image" src="https://github.com/user-attachments/assets/fc5f8d9f-46f0-433f-b87c-9c940e4370c6" />

## OU and User Management

 Created lab.ou under lab.local.

Created child OUs: Servers, Computers, Users, Admins, Service-Accounts.

Added test users and groups:

Admin.Basit → Domain Admins

Helpdesk.User → Helpdesk

Workstation.User → Workstation Users

<img width="770" height="540" alt="image" src="https://github.com/user-attachments/assets/68390670-aef0-45fa-a80a-54f1e275d9c5" />


## GPO Hardening
Password & Account Policies

Minimum length: 12+

Complexity: Enabled

Password history: 24

Max age: 60 days

<img width="1017" height="760" alt="image" src="https://github.com/user-attachments/assets/04b5d750-d3c8-47e6-a71f-0f956f15637b" />


## Account Lockout

Threshold: 4

Duration: 15 mins

Reset counter: 15 mins

<img width="1017" height="723" alt="image" src="https://github.com/user-attachments/assets/386136bc-05a6-4efa-b915-3a19126f9a85" />


## Advanced Audit Policy

Enable auditing for:

Logon/Logoff → Success/Failure

Account Logon → Success/Failure

Object Access → Success/Failure

Directory Service Changes → Success/Failure

Privilege Use → Success/Failure

<img width="1010" height="672" alt="image" src="https://github.com/user-attachments/assets/7414a552-9ecb-4dac-8509-4da1649747a6" />


## Firewall Rules

Inbound allowed: DNS, LDAP, LDAPS, Kerberos, SMB (domain-only)
<img width="1028" height="621" alt="image" src="https://github.com/user-attachments/assets/84caf743-e8ec-4609-b81c-1f2b5222e4c5" />

Outbound allowed: HTTP/HTTPS
<img width="851" height="510" alt="image" src="https://github.com/user-attachments/assets/4cd91a36-a618-4694-b61c-d1dc62c70e04" />

## Wazuh Integration

Installed Wazuh Manager (Ubuntu VM).

Installed Wazuh Agent on DC 
<img width="387" height="350" alt="image" src="https://github.com/user-attachments/assets/502862d3-9bc2-427e-855c-cecee08b3a8f" />
<img width="390" height="103" alt="image" src="https://github.com/user-attachments/assets/ba473002-cb07-474f-973c-572052df5938" />

Configured Sysmon log ingestion.
<img width="406" height="96" alt="image" src="https://github.com/user-attachments/assets/72dfef2b-2d3c-46c6-ac9f-58413a99a58c" />

Verified events appear in Wazuh dashboard.

<img width="787" height="167" alt="image" src="https://github.com/user-attachments/assets/1b45e752-d972-4911-a59e-1843278c2c09" />
<img width="1892" height="706" alt="image" src="https://github.com/user-attachments/assets/97e64a60-6999-44e0-aa6a-225b0dc2b10a" />

## LAPS Deployment

Extended AD schema for LAPS.

Created and linked LAPS GPO to lab.ou.

Configured:

Password length: 14+

Expiration: 30 days
<img width="298" height="642" alt="image" src="https://github.com/user-attachments/assets/ccc0beb9-e693-4f7b-a771-8b2e9a913125" />

<img width="1017" height="732" alt="image" src="https://github.com/user-attachments/assets/82372366-6a8d-4aa5-8ef0-5b58a29cfea1" />

## VLAN Segmentation

Created virtual VLANs for DC, clients, and Wazuh Manager.

Segmented traffic and tested connectivity.
<img width="882" height="472" alt="image" src="https://github.com/user-attachments/assets/f075001f-959a-4e93-8a9b-f414c98d81b2" />

## Conclusion

This lab demonstrates a professional enterprise defensive setup:

Active Directory hardening

Endpoint logging and monitoring (Sysmon + Wazuh)

Secure admin password management (LAPS)

Firewall enforcement and network segmentation

SOC-ready, reproducible lab 


