# 🔗 Resources & Lab Reference Guide

> **NetworkWalks Academy | Batch B082 | August 2026**

---

## 📋 Overview

A practical reference guide containing verified software download sources, official documentation, and command cheat sheets directly practiced and utilized in the **Cybersecurity & Ethical Hacking Lab**.

---

## 🛠️ Lab Software & Downloads

### Hypervisor & Utilities

| Software | Version / Purpose | Official Source |
|---|---|---|
| 🧰 **Oracle VirtualBox** | Type-2 Hypervisor for isolated lab environment | [VirtualBox Downloads](https://virtualbox.org/wiki/Downloads) |
| 📦 **7-Zip** | Archive utility for `.7z` VM image extraction | [7-Zip Official](https://7-zip.org/download.html) |

### Operating System Images

| System | Role | Official Source |
|---|---|---|
| 🐉 **Kali Linux 2026.2** | Attacker VM (Pre-built VirtualBox Image) | [Kali Linux Get-Kali](https://kali.org/get-kali) |

---

## 📖 Practiced Commands Reference

### 1. System Administration & Hardening (Week 1 Practiced)

```bash
# Verify system architecture & kernel release
uname -a

# Check active user identity and privileges
whoami
id

# Hardening default credentials (mandatory on first boot)
passwd              # Update 'kali' user password
sudo passwd root    # Set and secure 'root' account password
```

### 2. Network Inspection & Lab Subnet Verification (Week 1 Practiced)

```bash
# Inspect network interfaces and verify 10.0.2.15/24 IP assignment
ifconfig
ip a

# Check active network routes and default gateway
ip route

# Test internal gateway connectivity
ping -c 4 10.0.2.1

# Test outbound internet and DNS resolution
ping -c 4 8.8.8.8
nslookup networkwalks.com
```

### 3. Footprinting, OSINT & Reconnaissance (Week 2 Reference)

```bash
# Query domain WHOIS registration details
whois [target-domain]

# DNS record enumeration
nslookup [target-domain]
dig [target-domain] ANY

# Open-source email, domain and IP harvesting
theHarvester -d [target-domain] -b all -l 100
```

### 4. Nmap & Zenmap Network Scanning (`10.0.2.0/24` Lab Subnet)

```bash
# Host discovery sweep across the NatNetwork subnet
nmap -sn 10.0.2.0/24

# Fast scan of the top 100 most common ports
nmap -T4 -F [target-ip]

# Service version detection on open ports
nmap -sV [target-ip]

# Remote Operating System fingerprinting
nmap -O [target-ip]

# Comprehensive scan (Service versions + OS detection + Traceroute)
nmap -T4 -A -v [target-ip]
```

---

## 📚 Official Documentation & Manuals

| Resource | Scope | Link |
|---|---|---|
| **Kali Linux Official Documentation** | OS configuration, package management & tool usage | [kali.org/docs](https://www.kali.org/docs/) |
| **Nmap Reference Guide** | Official command-line flags, scan types & NSE scripts | [nmap.org/book/man.html](https://nmap.org/book/man.html) |
| **Oracle VirtualBox User Manual** | Networking modes (NAT vs NAT Network), snapshot management | [virtualbox.org/manual](https://www.virtualbox.org/manual/) |

---

## 🏛️ Program References

- 🌐 **NetworkWalks Academy:** [networkwalks.com](https://www.networkwalks.com)
- 🏢 **NetworkWalks LinkedIn:** [Company Page](https://linkedin.com/company/networkwalks/)
- 👨‍🏫 **Lead Instructor:** [Waqas Karim (CCIE)](https://linkedin.com/in/waqaskarim/)

---

> 📂 [Back to Main README](../README.md)
