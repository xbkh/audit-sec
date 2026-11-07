<div align="center">

# 🛡️ Security Audit Report

**Cybersecurity Hackathon — June 2025**

*Defense in depth for a fictional IT network*

![OPNsense](https://img.shields.io/badge/OPNsense-D94F00?style=for-the-badge&logoColor=white)
![Wazuh](https://img.shields.io/badge/Wazuh-005571?style=for-the-badge&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![OpenVPN](https://img.shields.io/badge/OpenVPN-EA7E20?style=for-the-badge&logo=openvpn&logoColor=white)

![Typst](https://img.shields.io/badge/Typst-239DAD?style=for-the-badge&logo=typst&logoColor=white)
![PDF](https://img.shields.io/badge/PDF-available-CC0000?style=for-the-badge&logo=adobeacrobatreader&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed_✓-27ae60?style=for-the-badge)
![Vulns](https://img.shields.io/badge/Vulnerabilities_fixed->90%25-27ae60?style=for-the-badge)

</div>

---

## 📋 Overview

This repository contains the complete documentation of the cybersecurity project carried out during a hackathon from **10 to 26 June 2025**, with the final presentation on **27 June**.

The goal: design, deploy and audit a fictional network infrastructure by applying **defense in depth** principles with open-source tools.

| | Result |
|---|---|
| 🏗️ Infrastructure | Deployed and working |
| 🔍 Vulnerabilities | >90 % fixed after the audit |
| 📡 Monitoring | Real-time monitoring operational (Wazuh) |
| 🔴 Simulated attacks | 100 % detected |
| 🔐 VPN | Secure access validated |

---

## 🏗️ Network architecture

```
              ┌──────────────────────────────────────────┐
   WAN        │   🔥 OPNsense Firewall (192.168.10.254)   │
 10.40.10.x ──┤   IDS/IPS Suricata · NAT · VPN OpenVPN   │
              └──────────────────┬───────────────────────┘
                                 │ LAN 192.168.10.0/24
           ┌─────────────────────┼──────────────────────┐
           │                     │                      │
  ┌────────▼──────┐   ┌──────────▼──────┐   ┌──────────▼──────┐
  │🐧 Ubuntu Hard. │   │ 📊 Wazuh Manager│   │ 🐉 Kali Linux   │
  │ 192.168.10.10 │   │  192.168.10.20  │   │  192.168.10.50  │
  │ Target server │   │  IDS / SIEM     │   │  Red Team       │
  │ UFW · Fail2Ban│   │  Dashboard :443 │   │  Nessus · Exegol│
  └───────────────┘   └─────────────────┘   └─────────────────┘
                                                      │
                                         ┌────────────▼──────┐
                                         │ 🔐 Client VPN      │
                                         │ 192.168.10.60 (VPN)│
                                         └───────────────────┘
```

### Addressing plan

| Host | Role | IP | VMware interface |
|------|------|----|-----------------|
| 🔥 OPNsense | Firewall & VPN | `192.168.10.254` | VMnet1 + Bridged |
| 🐧 Ubuntu Hardened | Hardened target server | `192.168.10.10` | VMnet1 + NAT |
| 📊 Wazuh Manager | IDS / SIEM | `192.168.10.20` | VMnet1 + NAT |
| 🐉 Kali Linux | Red Team + Nessus | `192.168.10.50` | VMnet1 + Bridged |
| 🔐 Ubuntu VPN client | Remote VPN access | `192.168.10.60` | NAT + tunnel |

---

## 🔧 Tech stack

<div align="center">

### Defense

![OPNsense](https://img.shields.io/badge/OPNsense-Firewall_&_VPN-D94F00?style=flat-square&logoColor=white)
![Wazuh](https://img.shields.io/badge/Wazuh-SIEM_/_IDS-005571?style=flat-square&logoColor=white)
![Fail2Ban](https://img.shields.io/badge/Fail2Ban-Brute--Force_Protection-CC0000?style=flat-square&logoColor=white)
![UFW](https://img.shields.io/badge/UFW-Linux_firewall-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![OpenVPN](https://img.shields.io/badge/OpenVPN-Remote_access-EA7E20?style=flat-square&logo=openvpn&logoColor=white)
![Suricata](https://img.shields.io/badge/Suricata-IDS_/_IPS-FF6600?style=flat-square&logoColor=white)

### Offense / Audit

![Nessus](https://img.shields.io/badge/Nessus-Scanner_CVE-00C176?style=flat-square&logoColor=white)
![Exegol](https://img.shields.io/badge/Exegol-Red_Team-1a1a2e?style=flat-square&logoColor=white)
![Hydra](https://img.shields.io/badge/Hydra-Brute--Force_SSH-8B0000?style=flat-square&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-Network_scan-4479A1?style=flat-square&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=flat-square&logo=kali-linux&logoColor=white)

### Infrastructure

![VMware](https://img.shields.io/badge/VMware_Workstation-607078?style=flat-square&logo=vmware&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

</div>

| Tool | Role |
|-------|------|
| **OPNsense** | Firewall, NAT, network rules, OpenVPN tunnel, Suricata IDS |
| **Wazuh** | SIEM / IDS — log collection, real-time alerts, dashboard |
| **Fail2Ban** | Automatic ban after SSH brute-force |
| **Nessus** | Vulnerability scanner (Tenable) |
| **Exegol** | Docker-based Red Team framework |
| **OpenVPN** | Secure remote access by certificate |
| **UFW** | Linux host firewall |
| **Hydra** | Brute-force testing (attack simulation) |
| **Nmap** | Network discovery and service detection |

---

## 📁 Repository contents

```
audit-sec/
├── 📄 rapport-audit-securite.typ   # Typst source (main document)
├── 📕 rapport-audit-securite.pdf   # Compiled report (~430 KB)
└── 📖 README.md                    # This file
```

### Building the report

The report is written in [Typst](https://typst.app/), a modern alternative to LaTeX. The report itself is written in French.

```bash
# Install Typst (Linux)
curl -fsSL https://typst.app/docs/install | sh

# Compile to PDF
typst compile rapport-audit-securite.typ

# Watch mode (automatic reload)
typst watch rapport-audit-securite.typ
```

---

## 🔍 Vulnerabilities found

### 🐧 Ubuntu Hardened (`192.168.10.10`)

| Severity | Vulnerability | CVE |
|----------|--------------|-----|
| ![CRITICAL](https://img.shields.io/badge/CRITICAL-8e0000?style=flat-square) | OpenSSH Privilege Escalation | `CVE-2023-2650` |
| ![HIGH](https://img.shields.io/badge/HIGH-c0392b?style=flat-square) | OpenSSL Multiple Vulnerabilities | `CVE-2023-0464` |
| ![HIGH](https://img.shields.io/badge/HIGH-c0392b?style=flat-square) | OpenSSL Timing Side Channel | `CVE-2023-0465` |
| ![MEDIUM](https://img.shields.io/badge/MEDIUM-e67e22?style=flat-square) | SSL Medium Strength Cipher Suites | `CVE-2000-1200` |
| ![MEDIUM](https://img.shields.io/badge/MEDIUM-e67e22?style=flat-square) | SSL Certificate Signature Weak | `CVE-2018-0734` |
| ![LOW](https://img.shields.io/badge/LOW-2980b9?style=flat-square) | ICMP Timestamp / TCP Timestamps | — |

### 📊 Wazuh Manager (`192.168.10.20`)

| Severity | Vulnerability | CVE |
|----------|--------------|-----|
| ![CRITICAL](https://img.shields.io/badge/CRITICAL-8e0000?style=flat-square) | Apache HTTP/2 DoS — Rapid Reset Attack | `CVE-2023-44487` |
| ![CRITICAL](https://img.shields.io/badge/CRITICAL-8e0000?style=flat-square) | Apache HTTP Server 2.4 < 2.4.57 | `CVE-2023-25690` |
| ![HIGH](https://img.shields.io/badge/HIGH-c0392b?style=flat-square) | Apache 2.4.7 < 2.4.57 Multi-Vuln | `CVE-2023-25690` |
| ![MEDIUM](https://img.shields.io/badge/MEDIUM-e67e22?style=flat-square) | TLS 1.0 / 1.1 detected | — |
| ![MEDIUM](https://img.shields.io/badge/MEDIUM-e67e22?style=flat-square) | Weak SSL cipher suites | — |
| ![LOW](https://img.shields.io/badge/LOW-2980b9?style=flat-square) | SSH Weak MAC / CBC Mode | — |

> **11 vulnerabilities detected — >90 % fixed after hardening.**

---

## 🛡️ Hardening applied

<details>
<summary><b>🐧 Ubuntu Hardened system</b></summary>

```bash
# Automatic updates
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades

# Kernel hardening
cat << 'EOF' | sudo tee /etc/sysctl.d/99-hardening.conf
net.ipv4.ip_forward = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.rp_filter = 1
EOF
sudo sysctl --system

# AppArmor
sudo systemctl enable --now apparmor
```
</details>

<details>
<summary><b>🔑 SSH — Secure configuration</b></summary>

```text
PermitRootLogin no
PasswordAuthentication no
MACs hmac-sha2-256,hmac-sha2-512
Ciphers aes256-ctr,aes192-ctr,aes128-ctr
```
</details>

<details>
<summary><b>🔥 UFW — Host firewall</b></summary>

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw enable && sudo ufw status verbose
```
</details>

<details>
<summary><b>🚫 Fail2Ban — Anti brute-force</b></summary>

```ini
[sshd]
enabled  = true
port     = 22
maxretry = 3
bantime  = 600
```
</details>

---

## 🚨 Simulated attacks & detection

| Attack | Tool | Detected by | Result |
|---------|-------|-------------|---------|
| SSH brute-force | ![Hydra](https://img.shields.io/badge/Hydra-8B0000?style=flat-square) | Wazuh + Fail2Ban | ✅ Banned after 3 attempts |
| Network scan | ![Nmap](https://img.shields.io/badge/Nmap-4479A1?style=flat-square) | Suricata (OPNsense) | ✅ Alert raised |
| Ping flood | ![hping3](https://img.shields.io/badge/hping3-555?style=flat-square) | Suricata | ✅ Detected |
| Vulnerability scan | ![Nessus](https://img.shields.io/badge/Nessus-00C176?style=flat-square) | — | ✅ 11 CVEs reported |
| Red Team | ![Exegol](https://img.shields.io/badge/Exegol-1a1a2e?style=flat-square) | Wazuh | ✅ Traces logged |

---

## 📅 Schedule

```
June 2025
──────────────────────────────────────────────────────────
10──────15  🏗️  Deployment & network (VMs, IPs, connectivity)
       16───18  🔥  Firewall & IDS (OPNsense, Wazuh, agents)
           19──────24  🔴  Attacks & hardening (Nessus, Hydra, fixes)
              20─────────26  📝  Analysis & documentation
                       25────27  🎤  Finalization & presentation
──────────────────────────────────────────────────────────
```

---

## 📚 Official documentation

[![Wazuh](https://img.shields.io/badge/Wazuh_Docs-005571?style=flat-square&logoColor=white)](https://documentation.wazuh.com/current/installation-guide/)
[![OPNsense](https://img.shields.io/badge/OPNsense_Docs-D94F00?style=flat-square&logoColor=white)](https://docs.opnsense.org/)
[![Docker](https://img.shields.io/badge/Docker_Docs-2496ED?style=flat-square&logo=docker&logoColor=white)](https://docs.docker.com/engine/install/)
[![Exegol](https://img.shields.io/badge/Exegol_Docs-1a1a2e?style=flat-square&logoColor=white)](https://docs.exegol.com/first-install)
[![Nessus](https://img.shields.io/badge/Nessus_Downloads-00C176?style=flat-square&logoColor=white)](https://www.tenable.com/downloads/nessus)
[![OpenVPN](https://img.shields.io/badge/OpenVPN_Community-EA7E20?style=flat-square&logo=openvpn&logoColor=white)](https://community.openvpn.net/)

---

<div align="center">
  <sub>Cybersecurity Hackathon · 10–27 June 2025 · Confidential</sub>
</div>
