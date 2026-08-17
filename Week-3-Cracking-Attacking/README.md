# ⚔️ Week 3 — Cracking & Attacking

> **NetworkWalks Academy | Batch B082 | August 2026**
>
> **Track:** Offensive (Red Team) — Phase 3/4 of Hacking
>
> **Submission Deadline:** Friday, 11:59 PM Dubai Time

---

## 📋 Project Overview

Execute Phase 3 (Gaining Access) and Phase 4 (Maintaining Access) of the hacking methodology on multiple targets using various tools and techniques.

---

## 🛠️ Tools Used

| Tool | Purpose | Version |
|---|---|---|
| 💀 Metasploit Framework | Exploitation & Post-Exploitation | |
| 🔓 John The Ripper (JTR) | Password Cracking | |
| 🔑 Hydra | Brute Force Attacks | |
| 🐍 Custom Scripts | Automation | |
| 🗡️ Other tools | [Specify] | |

---

## 🎯 Targets

> ⚠️ **All testing was performed on owned/authorized lab machines ONLY.**

| Target | IP Address | OS | Services |
|---|---|---|---|
| | 10.0.0.x | | |
| | 10.0.0.x | | |

---

## 📝 Attack Documentation

### Attack 1: [Attack Name]

**Target:** [Target details]
**Tool:** [Tool used]
**Vulnerability:** [CVE or description]

**Steps:**

```bash
# Step 1: [Description]
# command here

# Step 2: [Description]
# command here

# Step 3: [Description]
# command here
```

**Result:**
> [Describe the outcome]

**Evidence:**
<!-- Add screenshots here -->

---

### Attack 2: [Attack Name]

**Target:** [Target details]
**Tool:** [Tool used]
**Vulnerability:** [CVE or description]

**Steps:**

```bash
# Add your commands here
```

**Result:**
> [Describe the outcome]

**Evidence:**
<!-- Add screenshots here -->

---

### Attack 3: [Attack Name]

**Target:** [Target details]
**Tool:** [Tool used]

**Steps:**

```bash
# Add your commands here
```

**Result:**
> [Describe the outcome]

---

## 🔓 Password Cracking

### John The Ripper

```bash
# Example commands (on lab/authorized targets only)

# Crack password hashes
john --wordlist=/usr/share/wordlists/rockyou.txt [hash_file]

# Show cracked passwords
john --show [hash_file]
```

### Results

| Hash Type | Target | Status |
|---|---|---|
| | | ⬜ Not Cracked / ✅ Cracked |

---

## 💀 Metasploit Framework

### Exploitation Steps

```bash
# Example Metasploit workflow

msfconsole
search [vulnerability]
use [exploit_module]
set RHOSTS [target_ip]
set LHOST [attacker_ip]
exploit
```

### Sessions Gained

| Target | Exploit Used | Session Type | Privileges |
|---|---|---|---|
| | | Meterpreter / Shell | |

---

## 🐞 Problems Encountered & Solutions

### Problem 1: [Describe the problem]

**Symptom:**
> Describe what happened

**Solution:**
```bash
# Steps to fix
```

---

## 💡 What I Learned

1. [Key learning about gaining access]
2. [Key learning about exploitation]
3. [Key learning about password cracking]
4. [Key learning about post-exploitation]

---

## 🔐 Security & Ethical Use

> ⚠️ **All attacks were performed ONLY on owned/authorized lab machines.**
> No unauthorized systems were accessed or tested.
> This documentation is for **educational purposes only**.

---

## 📌 Project Information

| Field | Value |
|---|---|
| **Program** | Cybersecurity at NetworkWalks |
| **Batch** | B082 |
| **Week** | 03 |
| **Project** | Cracking & Attacking (Phase 3/4) |

---

> 📂 [Back to Main README](../README.md)

