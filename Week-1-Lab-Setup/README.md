# 🖥️ Week 1 — Cybersecurity & Pentesting Lab Setup

> **Batch B082** · NetworkWalks Academy · August 2026

---

## 🎯 Objective

Build an isolated virtual lab environment for cybersecurity testing and penetration testing practice using **VirtualBox** and **Kali Linux**.

---

## 🏗️ Lab Architecture

```
┌──────────────────────────────────────────────────────┐
│              HOST — Windows 10                        │
│       8 GB RAM  ·  256 GB SSD  ·  Core i5            │
│                                                      │
│   ┌──────────────────────────────────────────────┐   │
│   │       VirtualBox · NATNetwork 10.0.0.0/24    │   │
│   │                                              │   │
│   │   ┌──────────┐  ┌───────────┐  ┌─────────┐  │   │
│   │   │  Kali    │  │  Win 10   │  │ Metaspl │  │   │
│   │   │ 10.0.0.2 │  │ 10.0.0.10 │  │10.0.0.11│  │   │
│   │   │ Attacker │  │  Victim   │  │ Victim  │  │   │
│   │   └──────────┘  └───────────┘  └─────────┘  │   │
│   │                                              │   │
│   │   ┌──────────┐  ┌───────────┐  ┌─────────┐  │   │
│   │   │  Win 7   │  │ Srv 2016  │  │ Android │  │   │
│   │   │10.0.0.16 │  │ 10.0.0.9  │  │ 10.0.0.7│  │   │
│   │   │ Victim   │  │ Optional  │  │Optional │  │   │
│   │   └──────────┘  └───────────┘  └─────────┘  │   │
│   └──────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────┘
```

---

## ⚙️ Configuration Summary

| Component | Configuration |
|---|---|
| Host OS | Windows 10 |
| Hypervisor | VirtualBox |
| Network | NATNetwork — `10.0.0.0/24` |
| Kali Linux (Attacker) | `10.0.0.2/24` · 2048 MB RAM |
| Windows 10 (Victim) | `10.0.0.10/24` |
| Metasploitable 2 (Victim) | `10.0.0.11/24` |
| Windows 7 (Victim) | `10.0.0.16/24` |
| Gateway | `10.0.0.1` |
| DNS | `8.8.8.8` |

---

## 🪜 Setup Steps

### 1. Install 7-Zip

Installed [7-Zip](https://7-zip.org/download.html) to extract the Kali Linux `.7z` package.

<!-- ![7-Zip Installation](screenshots/1-7zip-install.png) -->

### 2. Install VirtualBox

Downloaded and installed [VirtualBox](https://virtualbox.org/wiki/Downloads) as the hypervisor.

<!-- ![VirtualBox Installation](screenshots/2-virtualbox-install.png) -->

### 3. Create NAT Network

Created a dedicated NAT Network in VirtualBox:

```
Network Name:  NatNetwork
IPv4 Prefix:   10.0.0.0/24
DHCP:          Enabled
IPv6:          Disabled
```

> **Why NAT Network?** Allows all VMs to communicate with each other *and* access the internet — essential for a multi-machine pentesting lab.

<!-- ![NAT Network](screenshots/3-nat-network-settings.png) -->

### 4. Import Kali Linux

Imported the [Kali Linux](https://kali.org/get-kali) pre-built VM into VirtualBox.

```
Adapter:    NAT Network → NatNetwork
RAM:        2048 MB
Adapter:    Intel PRO/1000 MT Desktop
```

<!-- ![Kali Linux VM](screenshots/4-kali-linux-import.png) -->

### 5. Configure Static IP on Kali

Assigned a consistent static IP for reliable lab documentation:

```
IP Address:    10.0.0.2
Subnet Mask:   255.255.255.0
Gateway:       10.0.0.1
DNS:           8.8.8.8
```

<!-- ![Kali Network](screenshots/5-kali-network-config.png) -->

### 6. Create Baseline Snapshot

Took a clean VirtualBox snapshot after initial configuration:

```
Snapshot: "Clean Kali — Network Setup"
```

> Provides a known-good restore point before any risky exercises.

<!-- ![Snapshot](screenshots/6-vm-snapshot.png) -->

---

## 🔎 Verification

| Test | Command | Expected Result | Status |
|---|---|---|:---:|
| IP Address | `ip a` | Shows `10.0.0.2/24` | ⬜ |
| Gateway Ping | `ping 10.0.0.1` | Replies received | ⬜ |
| Internet Ping | `ping 8.8.8.8` | Replies received | ⬜ |
| DNS Resolution | `nslookup networkwalks.com` | Domain resolves | ⬜ |
| Nmap Installed | `nmap --version` | Version displayed | ⬜ |
| Snapshot Restore | Restore → `ip a` | Baseline intact | ⬜ |

---

## 🐞 Troubleshooting

### Problem 1: [Title]

- **Symptom:** *Describe what went wrong*
- **Root Cause:** *What caused it*
- **Fix:**
  ```bash
  # command(s) used to resolve
  ```

### Problem 2: [Title]

- **Symptom:** *Describe what went wrong*
- **Root Cause:** *What caused it*
- **Fix:**
  ```bash
  # command(s) used to resolve
  ```

---

## 💡 Key Takeaways

- **NAT Network vs NAT** — NAT Network enables inter-VM communication; standard NAT isolates each VM.
- **Static IPs** — Assigning consistent IPs simplifies documentation and tool configurations.
- **Snapshots** — Always snapshot before risky operations for quick rollback.
- **Documentation** — Recording every step, command, and problem is a core cybersecurity practice.

---

## 🔐 Ethical Statement

> All testing in this lab is performed exclusively on **personally owned virtual machines** within an **isolated network**.
> No unauthorized systems were accessed.

---

## 🔗 References

- [VirtualBox Downloads](https://virtualbox.org/wiki/Downloads)
- [Kali Linux Downloads](https://kali.org/get-kali)
- [7-Zip Downloads](https://7-zip.org/download.html)
- [NetworkWalks Academy](https://www.networkwalks.com)
- [Sample Lab Repo](https://github.com/waqaskarimccie/Cybersecurity-Lab-Setup1)

---

<p align="center">
  <strong>Week 1</strong> · B082 · NetworkWalks Academy
</p>
