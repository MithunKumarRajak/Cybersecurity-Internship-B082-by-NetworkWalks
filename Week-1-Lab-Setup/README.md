# 🖥️ Week 1 — Cybersecurity & Pentesting Lab Setup

> **NetworkWalks Academy | Batch B082 | August 2026**
>
> **Submission Deadline:** 23:59H, Monday 17-August-2026

---

## 📋 Project Overview

Set up an isolated virtual lab environment for cybersecurity testing and penetration testing practice using VirtualBox and Kali Linux.

---

## 🏗️ Lab Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                   HOST MACHINE (Windows 10)                   │
│           Recommended: 8GB RAM | 256GB SSD | Core i3/i5+     │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │           VirtualBox — NATNetwork (Custom)              │  │
│  │               Network: 10.0.0.0/24                      │  │
│  │                                                         │  │
│  │   ┌────────────┐  ┌────────────┐  ┌────────────────┐   │  │
│  │   │ Kali Linux │  │ Windows 10 │  │ Metasploitable2│   │  │
│  │   │ (Attacker) │  │  (Victim)  │  │   (Victim)     │   │  │
│  │   │ 10.0.0.2   │  │ 10.0.0.10  │  │ 10.0.0.11      │   │  │
│  │   └────────────┘  └────────────┘  └────────────────┘   │  │
│  │                                                         │  │
│  │   ┌────────────┐  ┌────────────┐  ┌────────────────┐   │  │
│  │   │ Windows 7  │  │ Server 2016│  │   Android      │   │  │
│  │   │  (Victim)  │  │ (Optional) │  │  (Optional)    │   │  │
│  │   │ 10.0.0.16  │  │ 10.0.0.9   │  │ 10.0.0.7       │   │  │
│  │   └────────────┘  └────────────┘  └────────────────┘   │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

---

## ⚙️ Configuration Details

| 🧩 Component | ⚙️ Configuration |
|---|---|
| 🖥️ Host OS | Windows 10 |
| 🧠 Host RAM | 8 GB (recommended minimum) |
| 💾 Storage | 256 GB SSD (recommended minimum) |
| ⚡ Processor | Core i3/i5 or similar |
| 🧰 Hypervisor | VirtualBox |
| 🌐 Network Type | NATNetwork (Custom) |
| 📡 Network Range | 10.0.0.2–99 /24 |

### VM IP Assignments

| VM | IP Address | Role |
|---|---|---|
| 🐉 Kali Linux | 10.0.0.2/24 | Attacker |
| 🪟 Windows 10 | 10.0.0.10/24 | Victim |
| 💀 Metasploitable2 | 10.0.0.11/24 | Victim |
| 🪟 Windows 7 | 10.0.0.16/24 | Victim |
| 🤖 Android (Optional) | 10.0.0.7/24 | Victim |
| 🖥️ Server 2016 (Optional) | 10.0.0.9/24 | Victim |

---

## 🪜 Lab Setup Procedure

### Step 1. Install 7-Zip

7-Zip is needed to extract the Kali Linux virtual-machine package (distributed as `.7z` archive).

**Download:** [https://7-zip.org/download.html](https://7-zip.org/download.html)

<!-- Add your screenshot here -->
<!-- ![7-Zip Installation](screenshots/1-7zip-install.png) -->

---

### Step 2. Install VirtualBox

Download and install VirtualBox as the hypervisor.

**Download:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)

<!-- Add your screenshot here -->
<!-- ![VirtualBox Installation](screenshots/2-virtualbox-install.png) -->

---

### Step 3. Create the NAT Network

Create a dedicated NAT Network in VirtualBox:

```
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled
```

**Why NAT Network?** Multiple VMs connected to the same NAT Network can communicate with one another while having outbound network connectivity. This allows attacker and target VMs to interact within the lab.

<!-- Add your screenshot here -->
<!-- ![NAT Network Settings](screenshots/3-nat-network-settings.png) -->

---

### Step 4. Import Kali Linux

Download and import Kali Linux VM from the official website.

**Download:** [https://kali.org/get-kali](https://kali.org/get-kali)

VM Configuration:
```
Adapter 1
  Attached to: NAT Network
  Network:     NatNetwork
  Adapter Type: Intel PRO/1000 MT Desktop

RAM: 2048 MB
```

<!-- Add your screenshot here -->
<!-- ![Kali Linux VM](screenshots/4-kali-linux-import.png) -->

---

### Step 5. Configure Kali Linux Network

Configure a static IPv4 address on Kali Linux:

```
IP Address:   10.0.0.2
Subnet Mask:  255.255.255.0
Gateway:      10.0.0.1
DNS:          8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

<!-- Add your screenshot here -->
<!-- ![Kali Network Settings](screenshots/5-kali-network-config.png) -->

---

### Step 6. Create a Clean VM Snapshot

After completing the initial configuration, create a VirtualBox snapshot:

```
Snapshot Name: Clean Kali - Network Setup
```

This snapshot serves as the clean baseline. If a future exercise damages the VM configuration, it can be restored to this baseline.

<!-- Add your screenshot here -->
<!-- ![VM Snapshot](screenshots/6-vm-snapshot.png) -->

---

## 🔎 Lab Verification

| ✅ Test | 🧾 Command | 🎯 Expected Result |
|---|---|---|
| 🌐 Check IP address | `ip a` | Correct Kali IP displayed |
| 📡 Test gateway | `ping 10.0.0.1` | Successful replies |
| 🌍 Test Internet connectivity | `ping 8.8.8.8` | Successful replies |
| 🔎 Test DNS resolution | `nslookup networkwalks.com` | Domain resolves |
| 🧰 Verify Nmap | `nmap --version` | Nmap version displayed |
| 🔄 Verify snapshot | Restore snapshot and run `ip a` | Baseline configuration restored |

### Verification Results

```
# Add your verification results here

IP Address: 
Gateway ping:
Internet ping:
DNS resolution:
Nmap version:
```

<!-- Add your verification screenshots here -->

---

## 🐞 Problems Encountered & Solutions

### Problem 1: [Describe the problem you faced]

**Symptom:**
> Describe what happened

**Solution:**
```bash
# Add the commands or steps you used to fix it
```

**Explanation:**
> Explain why this fixed the issue

---

### Problem 2: [Describe another problem]

**Symptom:**
> Describe what happened

**Solution:**
```bash
# Add the commands or steps you used to fix it
```

---

## 💡 What I Learned

1. **NAT vs NAT Network:** The difference between standard NAT and NAT Network — NAT Network allows inter-VM communication while providing external connectivity.

2. **Virtual Machine Networking:** How VirtualBox virtual network adapters connect VMs to different network types.

3. **Static IP Configuration:** How to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

4. **VM Snapshots:** Creating a clean snapshot before performing risky activities provides a known-good recovery point.

5. **Documentation:** Documenting commands, configuration, screenshots, problems, and solutions is essential for professional cybersecurity work.

---

## 🔐 Security & Ethical Use

> This laboratory is intended strictly for **educational purposes only**.
> All testing is performed on **owned devices** within an isolated virtual lab environment.

---

## 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)
- **NetworkWalks:** [https://www.networkwalks.com](https://www.networkwalks.com)

---

## 📌 Project Information

| Field | Value |
|---|---|
| **Program** | Cybersecurity at NetworkWalks |
| **Batch** | B082 |
| **Week** | 01 |
| **Project** | Cybersecurity & Pentesting Lab Setup |

---

> 📂 [Back to Main README](../README.md)

