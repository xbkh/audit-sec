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

## 🖼️ Screenshots

Captured during the build and the tests. Highlights first, then every step grouped below.

<p align="center">
  <img src="docs/screenshots/001-schma-rseau.png" alt="Network diagram" width="48%">
  <img src="docs/screenshots/030-4-accs-au-dashboard.png" alt="Wazuh dashboard login" width="48%">
  <img src="docs/screenshots/083-idsips-opnsense.png" alt="OPNsense IDS/IPS" width="48%">
  <img src="docs/screenshots/085-tches--raliser.png" alt="Red team attack simulation" width="48%">
</p>

<details><summary><b>Network diagram</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/001-schma-rseau.png" alt="Network diagram (1/1)" width="80%">
</p>

</details>

<details><summary><b>Kali: LAN interface configuration</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/002-configuration-de-linterface-lan-dans-kal.png" alt="Kali: LAN interface configuration (1/1)" width="80%">
</p>

</details>

<details><summary><b>Nessus: download</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/003-tlchargement-de-nessus.png" alt="Nessus: download (1/1)" width="80%">
</p>

</details>

<details><summary><b>Nessus: installation</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/004-installation-de-nessus.png" alt="Nessus: installation (1/1)" width="80%">
</p>

</details>

<details><summary><b>Exegol: installation</b> (6)</summary>

<p align="center">
  <img src="docs/screenshots/005-installation-officielle-dexegol.png" alt="Exegol: installation (1/6)" width="80%">
  <img src="docs/screenshots/006-installation-officielle-dexegol.png" alt="Exegol: installation (2/6)" width="80%">
  <img src="docs/screenshots/007-installation-officielle-dexegol.png" alt="Exegol: installation (3/6)" width="80%">
  <img src="docs/screenshots/008-installation-officielle-dexegol.png" alt="Exegol: installation (4/6)" width="80%">
  <img src="docs/screenshots/009-installation-officielle-dexegol.png" alt="Exegol: installation (5/6)" width="80%">
  <img src="docs/screenshots/011-installation-officielle-dexegol.png" alt="Exegol: installation (6/6)" width="80%">
</p>

</details>

<details><summary><b>Ubuntu: Netplan network configuration</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/012-configuration-rseau-avec-netplan.png" alt="Ubuntu: Netplan network configuration (1/1)" width="80%">
</p>

</details>

<details><summary><b>Ubuntu: system hardening</b> (2)</summary>

<p align="center">
  <img src="docs/screenshots/013-hardening-du-systme.png" alt="Ubuntu: system hardening (1/2)" width="80%">
  <img src="docs/screenshots/014-hardening-du-systme.png" alt="Ubuntu: system hardening (2/2)" width="80%">
</p>

</details>

<details><summary><b>Ubuntu: kernel hardening (sysctl)</b> (3)</summary>

<p align="center">
  <img src="docs/screenshots/015-durcissement-noyau-sysctl.png" alt="Ubuntu: kernel hardening (sysctl) (1/3)" width="80%">
  <img src="docs/screenshots/016-durcissement-noyau-sysctl.png" alt="Ubuntu: kernel hardening (sysctl) (2/3)" width="80%">
  <img src="docs/screenshots/017-durcissement-noyau-sysctl.png" alt="Ubuntu: kernel hardening (sysctl) (3/3)" width="80%">
</p>

</details>

<details><summary><b>Ubuntu: secure SSH configuration</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/018-configuration-ssh-scurise.png" alt="Ubuntu: secure SSH configuration (1/1)" width="80%">
</p>

</details>

<details><summary><b>SSH: generating an RSA key pair</b> (2)</summary>

<p align="center">
  <img src="docs/screenshots/019-gnrer-une-paire-de-cls-rsa-si-non-exista.png" alt="SSH: generating an RSA key pair (1/2)" width="80%">
  <img src="docs/screenshots/020-gnrer-une-paire-de-cls-rsa-si-non-exista.png" alt="SSH: generating an RSA key pair (2/2)" width="80%">
</p>

</details>

<details><summary><b>SSH: copying the public key</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/021-copier-la-cl-publique.png" alt="SSH: copying the public key (1/1)" width="80%">
</p>

</details>

<details><summary><b>SSH: testing the connection</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/022-tester-la-connexion-ssh.png" alt="SSH: testing the connection (1/1)" width="80%">
</p>

</details>

<details><summary><b>UFW firewall</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/023-ufw-pare-feu.png" alt="UFW firewall (1/1)" width="80%">
</p>

</details>

<details><summary><b>Fail2Ban</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/024-fail2ban.png" alt="Fail2Ban (1/1)" width="80%">
</p>

</details>

<details><summary><b>Wazuh VM: update and network configuration</b> (2)</summary>

<p align="center">
  <img src="docs/screenshots/025-1-mise--jour-et-configuration-rseau-de-l.png" alt="Wazuh VM: update and network configuration (1/2)" width="80%">
  <img src="docs/screenshots/026-1-mise--jour-et-configuration-rseau-de-l.png" alt="Wazuh VM: update and network configuration (2/2)" width="80%">
</p>

</details>

<details><summary><b>Wazuh Manager: automatic installation</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/027-2-installation-automatique-de-wazuh-mana.png" alt="Wazuh Manager: automatic installation (1/1)" width="80%">
</p>

</details>

<details><summary><b>Wazuh Manager: checking the installation</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/029-3-vrification-de-linstallation.png" alt="Wazuh Manager: checking the installation (1/1)" width="80%">
</p>

</details>

<details><summary><b>Wazuh: dashboard access</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/030-4-accs-au-dashboard.png" alt="Wazuh: dashboard access (1/1)" width="80%">
</p>

</details>

<details><summary><b>Wazuh VM: optional UFW hardening</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/032-5-scurisation-optionnelle-avec-ufw.png" alt="Wazuh VM: optional UFW hardening (1/1)" width="80%">
</p>

</details>

<details><summary><b>Wazuh Agent: installation on Ubuntu Hardened</b> (6)</summary>

<p align="center">
  <img src="docs/screenshots/033-installation-wazuh-agent-sur-ubuntu-hard.png" alt="Wazuh Agent: installation on Ubuntu Hardened (1/6)" width="80%">
  <img src="docs/screenshots/035-installation-wazuh-agent-sur-ubuntu-hard.png" alt="Wazuh Agent: installation on Ubuntu Hardened (2/6)" width="80%">
  <img src="docs/screenshots/036-installation-wazuh-agent-sur-ubuntu-hard.png" alt="Wazuh Agent: installation on Ubuntu Hardened (3/6)" width="80%">
  <img src="docs/screenshots/037-installation-wazuh-agent-sur-ubuntu-hard.png" alt="Wazuh Agent: installation on Ubuntu Hardened (4/6)" width="80%">
  <img src="docs/screenshots/038-installation-wazuh-agent-sur-ubuntu-hard.png" alt="Wazuh Agent: installation on Ubuntu Hardened (5/6)" width="80%">
  <img src="docs/screenshots/039-installation-wazuh-agent-sur-ubuntu-hard.png" alt="Wazuh Agent: installation on Ubuntu Hardened (6/6)" width="80%">
</p>

</details>

<details><summary><b>Wazuh Agent: successful command output</b> (6)</summary>

<p align="center">
  <img src="docs/screenshots/040-captures-de-succs-excution-des-commandes.png" alt="Wazuh Agent: successful command output (1/6)" width="80%">
  <img src="docs/screenshots/041-captures-de-succs-excution-des-commandes.png" alt="Wazuh Agent: successful command output (2/6)" width="80%">
  <img src="docs/screenshots/042-captures-de-succs-excution-des-commandes.png" alt="Wazuh Agent: successful command output (3/6)" width="80%">
  <img src="docs/screenshots/043-captures-de-succs-excution-des-commandes.png" alt="Wazuh Agent: successful command output (4/6)" width="80%">
  <img src="docs/screenshots/044-captures-de-succs-excution-des-commandes.png" alt="Wazuh Agent: successful command output (5/6)" width="80%">
  <img src="docs/screenshots/045-captures-de-succs-excution-des-commandes.png" alt="Wazuh Agent: successful command output (6/6)" width="80%">
</p>

</details>

<details><summary><b>Wazuh: agent, manager and dashboard version compatibility</b> (5)</summary>

<p align="center">
  <img src="docs/screenshots/046-6-compatibilit-version-agentmanagerdashb.png" alt="Wazuh: agent, manager and dashboard version compatibility (1/5)" width="80%">
  <img src="docs/screenshots/047-6-compatibilit-version-agentmanagerdashb.png" alt="Wazuh: agent, manager and dashboard version compatibility (2/5)" width="80%">
  <img src="docs/screenshots/048-6-compatibilit-version-agentmanagerdashb.png" alt="Wazuh: agent, manager and dashboard version compatibility (3/5)" width="80%">
  <img src="docs/screenshots/049-6-compatibilit-version-agentmanagerdashb.png" alt="Wazuh: agent, manager and dashboard version compatibility (4/5)" width="80%">
  <img src="docs/screenshots/050-6-compatibilit-version-agentmanagerdashb.png" alt="Wazuh: agent, manager and dashboard version compatibility (5/5)" width="80%">
</p>

</details>

<details><summary><b>Wazuh Agent: automatic reconnection script</b> (7)</summary>

<p align="center">
  <img src="docs/screenshots/051-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (1/7)" width="80%">
  <img src="docs/screenshots/052-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (2/7)" width="80%">
  <img src="docs/screenshots/053-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (3/7)" width="80%">
  <img src="docs/screenshots/054-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (4/7)" width="80%">
  <img src="docs/screenshots/055-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (5/7)" width="80%">
  <img src="docs/screenshots/056-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (6/7)" width="80%">
  <img src="docs/screenshots/057-7-cration-dun-script-pour-automatiser-le.png" alt="Wazuh Agent: automatic reconnection script (7/7)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: installation</b> (6)</summary>

<p align="center">
  <img src="docs/screenshots/058-installation-dopnsense.png" alt="OPNsense: installation (1/6)" width="80%">
  <img src="docs/screenshots/059-installation-dopnsense.png" alt="OPNsense: installation (2/6)" width="80%">
  <img src="docs/screenshots/060-installation-dopnsense.png" alt="OPNsense: installation (3/6)" width="80%">
  <img src="docs/screenshots/061-installation-dopnsense.png" alt="OPNsense: installation (4/6)" width="80%">
  <img src="docs/screenshots/062-installation-dopnsense.png" alt="OPNsense: installation (5/6)" width="80%">
  <img src="docs/screenshots/063-installation-dopnsense.png" alt="OPNsense: installation (6/6)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: authentication</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/064-authentification.png" alt="OPNsense: authentication (1/1)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: LAN interface configuration</b> (4)</summary>

<p align="center">
  <img src="docs/screenshots/065-configuration-de-linterface-lan.png" alt="OPNsense: LAN interface configuration (1/4)" width="80%">
  <img src="docs/screenshots/066-configuration-de-linterface-lan.png" alt="OPNsense: LAN interface configuration (2/4)" width="80%">
  <img src="docs/screenshots/067-configuration-de-linterface-lan.png" alt="OPNsense: LAN interface configuration (3/4)" width="80%">
  <img src="docs/screenshots/068-configuration-de-linterface-lan.png" alt="OPNsense: LAN interface configuration (4/4)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: WAN interface configuration</b> (2)</summary>

<p align="center">
  <img src="docs/screenshots/069-configuration-de-linterface-wan.png" alt="OPNsense: WAN interface configuration (1/2)" width="80%">
  <img src="docs/screenshots/070-configuration-de-linterface-wan.png" alt="OPNsense: WAN interface configuration (2/2)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: first login</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/071-connection-opnsense.png" alt="OPNsense: first login (1/1)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: administration and SSH settings</b> (3)</summary>

<p align="center">
  <img src="docs/screenshots/072-config-settings-administration-ssh.png" alt="OPNsense: administration and SSH settings (1/3)" width="80%">
  <img src="docs/screenshots/073-config-settings-administration-ssh.png" alt="OPNsense: administration and SSH settings (2/3)" width="80%">
  <img src="docs/screenshots/074-config-settings-administration-ssh.png" alt="OPNsense: administration and SSH settings (3/3)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: system wizard</b> (6)</summary>

<p align="center">
  <img src="docs/screenshots/075-config-settings-system-wizard.png" alt="OPNsense: system wizard (1/6)" width="80%">
  <img src="docs/screenshots/076-config-settings-system-wizard.png" alt="OPNsense: system wizard (2/6)" width="80%">
  <img src="docs/screenshots/077-config-settings-system-wizard.png" alt="OPNsense: system wizard (3/6)" width="80%">
  <img src="docs/screenshots/078-config-settings-system-wizard.png" alt="OPNsense: system wizard (4/6)" width="80%">
  <img src="docs/screenshots/079-config-settings-system-wizard.png" alt="OPNsense: system wizard (5/6)" width="80%">
  <img src="docs/screenshots/080-config-settings-system-wizard.png" alt="OPNsense: system wizard (6/6)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: firewall NAT</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/081-firewall-nat.png" alt="OPNsense: firewall NAT (1/1)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: firewall rules</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/082-rules-firewall.png" alt="OPNsense: firewall rules (1/1)" width="80%">
</p>

</details>

<details><summary><b>OPNsense: IDS/IPS (Suricata)</b> (2)</summary>

<p align="center">
  <img src="docs/screenshots/083-idsips-opnsense.png" alt="OPNsense: IDS/IPS (Suricata) (1/2)" width="80%">
  <img src="docs/screenshots/084-idsips-opnsense.png" alt="OPNsense: IDS/IPS (Suricata) (2/2)" width="80%">
</p>

</details>

<details><summary><b>Red team: attack simulation from Kali</b> (2)</summary>

<p align="center">
  <img src="docs/screenshots/085-tches--raliser.png" alt="Red team: attack simulation from Kali (1/2)" width="80%">
  <img src="docs/screenshots/086-tches--raliser.png" alt="Red team: attack simulation from Kali (2/2)" width="80%">
</p>

</details>

<details><summary><b>Wazuh: detection of the attacks</b> (1)</summary>

<p align="center">
  <img src="docs/screenshots/087-supervision-avec-wazuh.png" alt="Wazuh: detection of the attacks (1/1)" width="80%">
</p>

</details>

<details><summary><b>OpenVPN: remote access (CA, certificates, users, server, firewall, client)</b> (19)</summary>

<p align="center">
  <img src="docs/screenshots/088-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (1/19)" width="80%">
  <img src="docs/screenshots/090-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (2/19)" width="80%">
  <img src="docs/screenshots/091-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (3/19)" width="80%">
  <img src="docs/screenshots/092-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (4/19)" width="80%">
  <img src="docs/screenshots/093-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (5/19)" width="80%">
  <img src="docs/screenshots/095-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (6/19)" width="80%">
  <img src="docs/screenshots/096-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (7/19)" width="80%">
  <img src="docs/screenshots/097-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (8/19)" width="80%">
  <img src="docs/screenshots/098-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (9/19)" width="80%">
  <img src="docs/screenshots/099-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (10/19)" width="80%">
  <img src="docs/screenshots/100-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (11/19)" width="80%">
  <img src="docs/screenshots/101-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (12/19)" width="80%">
  <img src="docs/screenshots/102-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (13/19)" width="80%">
  <img src="docs/screenshots/103-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (14/19)" width="80%">
  <img src="docs/screenshots/104-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (15/19)" width="80%">
  <img src="docs/screenshots/105-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (16/19)" width="80%">
  <img src="docs/screenshots/106-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (17/19)" width="80%">
  <img src="docs/screenshots/107-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (18/19)" width="80%">
  <img src="docs/screenshots/108-rle-test-vpn-accs-distant-scuris.png" alt="OpenVPN: remote access (CA, certificates, users, server, firewall, client) (19/19)" width="80%">
</p>

</details>

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
