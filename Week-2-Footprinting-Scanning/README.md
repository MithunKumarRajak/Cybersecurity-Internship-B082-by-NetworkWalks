# 🔍 Week 2 — Footprinting, Scanning & Report Writing

> **NetworkWalks Academy | Batch B082 | August 2026**
>
> **Track:** Offensive (Red Team) — Phase 1 & 2 of Hacking Lifecycle
>
> **Submission Deadline:** 23:00H, Friday 28-August-2026

---

## 📋 Project Overview

Perform systematic reconnaissance, Open Source Intelligence (OSINT), network footprinting, and vulnerability scanning on target machines within the isolated `10.0.2.0/24` lab environment using Kali Linux tools, followed by compiling a formal Penetration Testing Report.

---

## 📦 Project Modules

Complete **at least 1 elective** + both **essential** modules (minimum 3 modules total).

### Elective Modules (Choose ≥ 1)

| Module ID | Module Name | Scope | Status |
|---|---|---|:---:|
| **W2-PM1** | Multi-Tool Footprinting | 6+ CLI tools (WHOIS, DNSenum, Nslookup, etc.) | ⬜ Not Started |
| **W2-PM2** | Google Hacking Database (GHDB) | Google Dorks & search operator reconnaissance | ⬜ Not Started |
| **W2-PM3** | Maltego Reconnaissance | Graph-based entity link analysis & transforms | ⬜ Not Started |
| **W2-PM4** | theHarvester OSINT | Email, domain, subdomain & IP enumeration | ⬜ Not Started |

### Essential Modules (Both Mandatory)

| Module ID | Module Name | Scope | Status |
|---|---|---|:---:|
| **W2-PM5** | Zenmap / Nmap Network Scanning | Port scanning, service detection, OS fingerprinting | ⬜ Not Started |
| **W2-PM-FINAL** | Formal Pentest Report | Professional client-ready vulnerability report | ⬜ Not Started |

---

## W2-PM1: Footprinting with Multiple Kali Tools

> *Document your findings if this elective is selected.*

### Tools Configured & Executed

1. **Tool 1: [Tool Name]**
   - Command: `command here`
   - Target: `10.0.2.x` / Domain
   - Findings: [Details]

2. **Tool 2: [Tool Name]**
   - Command: `command here`
   - Target: `10.0.2.x` / Domain
   - Findings: [Details]

---

## W2-PM2: GHDB-based Footprinting Attacks

> *Document your findings if this elective is selected.*

### Google Dorks Applied

```
# Authorized educational search strings
site:example.com filetype:pdf "confidential"
intitle:"index of" "password"
```

---

## W2-PM3: Maltego-based Footprinting Attacks

> *Document your findings if this elective is selected.*

### Maltego Configuration & Transforms
- **Transform Hub:** Standard Transforms / Community Edition
- **Target Entity:** [Domain / IP / Person]
- **Key Relationships Discovered:** [Summary of graph links]

---

## W2-PM4: theHarvester-based Footprinting Attacks

> *Document your findings if this elective is selected.*

```bash
# Example syntax
theHarvester -d [target-domain] -b all -l 100
```

| Discovered Data Type | Count | Key Examples |
|---|---|---|
| **Email Addresses** | | |
| **Subdomains / Hosts** | | |
| **Public IP Addresses** | | |

---

## W2-PM5: Zenmap-based Network Scanning (Essential)

### Target Environment: Lab Subnet (`10.0.2.0/24`)

| Scan Profile | Command Syntax | Objective |
|---|---|---|
| **Ping Discovery** | `nmap -sn 10.0.2.0/24` | Identify live lab hosts |
| **Quick Scan** | `nmap -T4 -F 10.0.2.x` | Rapid top 100 port scan |
| **Intense Scan** | `nmap -T4 -A -v 10.0.2.x` | OS, services, scripts & traceroute |
| **Vulnerability Scan** | `nmap --script vuln 10.0.2.x` | Detect known CVEs on open services |

### Scan Findings Matrix

| Target IP | Host Name | Open Ports | Services & Versions | Detected OS |
|---|---|---|---|---|
| `10.0.2.x` | | | | |

---

## W2-PM-FINAL: Penetration Testing Report (Essential)

- **Deliverable File:** `Reports/Week-2-Pentest-Report.md` (or `.pdf`)
- **Key Sections:** Executive Summary, Scope (`10.0.2.0/24`), Findings with Severity, POC Evidence, Risk Matrix, Remediation Advice.

---

## 💡 What I Learned

1. [Reconnaissance methodology]
2. [Effective Nmap timing templates and NSE scripts]
3. [Structure of professional penetration testing documentation]

---

## 🔐 Ethical Statement

> All scanning and reconnaissance were restricted strictly to the **authorized lab network** (`10.0.2.0/24`) and permitted domains. No unauthorized systems were targeted.

---

> 📂 [Back to Main README](../README.md)
