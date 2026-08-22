# 🖥️ Week 1 — Lab Environment Setup Report

> **Batch B082** · NetworkWalks Academy · **Submission Date:** 22 August 2026

---

## 🎯 Objective

Build a safe, isolated penetration-testing environment on a personal host machine using **Oracle VirtualBox**. This involved deploying a pre-built **Kali Linux 2026.2** virtual machine, securing default credentials, and configuring an internal virtual network (**NAT Network**) so that multiple lab VMs can communicate with each other and access the internet, without exposing the lab environment to the host's real home/office network.

---

## 🏗️ Lab Architecture

```
+-----------------------------------------------------------------------+
|                         HOST: Windows 10/11                           |
|                    Oracle VirtualBox Hypervisor                       |
|                                                                       |
|   +---------------------------------------------------------------+   |
|   |         Isolated Virtual Subnet: NatNetwork (10.0.2.0/24)     |   |
|   |                     DHCP: Enabled | IPv6: Off                 |   |
|   |                                                               |   |
|   |   +--------------------------+     +----------------------+   |   |
|   |   |   Kali Linux 2026.2      |     |  Target VM (Planned) |   |   |
|   |   |   Role: Attacker         |     |  Role: Victim        |   |   |
|   |   |   IP:   10.0.2.15 (eth0) | <-> |  IP:   10.0.2.x      |   |   |
|   |   |   RAM:  4096 MB | 3 vCPU |     |  OS:   Metasploitable|   |   |
|   |   |   Disk: 80.09 GB VDI     |     |        / Windows     |   |   |
|   |   |   Mode: Promisc AllowAll |     |                      |   |   |
|   |   +--------------------------+     +----------------------+   |   |
|   +---------------------------------------------------------------+   |
|                                  |                                    |
|                                  v (NAT Outbound Access)              |
|                    +---------------------------+                      |
|                    |      Internet / WAN       |                      |
|                    +---------------------------+                      |
+-----------------------------------------------------------------------+
```

---

## ⚙️ Lab Environment Summary

| Component | Configuration Details |
|---|---|
| **Host Operating System** | Windows 10/11 |
| **Hypervisor** | Oracle VirtualBox |
| **Guest OS** | Kali Linux 2026.2 (Rolling, x64) — Pre-built VirtualBox Image |
| **Base Memory (RAM)** | 4096 MB (4 GB) |
| **Virtual Processors (vCPU)** | 3 vCPUs |
| **Storage (Virtual Disk)** | 80.09 GB SATA VDI (Dynamically Allocated) |
| **Virtual Network Name** | `NatNetwork` |
| **Network Mode** | NAT Network (`10.0.2.0/24`) |
| **DHCP Configuration** | Enabled (Auto-assigns lab IP addresses) |
| **Kali Assigned IP** | `10.0.2.15/24` (Interface: `eth0`) |
| **Adapter Promiscuous Mode** | Allow All (Required for Wireshark & packet sniffing) |

---

## 🪜 Steps Performed

### 3.1 Download and Extraction

Downloaded the official pre-built **Kali Linux VirtualBox image** (`kali-linux-2026.2-virtualbox-amd64`) as a compressed `.7z` archive and extracted it to obtain two essential files:

- **`kali-linux-2026.2-virtualbox-amd64.vbox`** — The VM configuration file (stores settings including RAM, CPU, network adapters, and boot order).
- **`kali-linux-2026.2-virtualbox-amd64.vdi`** — The Virtual Disk Image (~15.8 GB) containing the complete pre-installed Kali Linux OS.

> 📝 **Linked Pair Architecture:** The `.vbox` and `.vdi` files function as a linked pair, not a merged file. The `.vbox` configuration holds a path reference to the `.vdi` disk — VirtualBox reads both together at boot time, so moving one without the other breaks VM registration.

**Troubleshooting — Duplicate File Extraction:**
During extraction, the archive unpacked into a nested folder of the same name, producing a duplicate copy of both the `.vbox` and `.vdi` files inside it. The redundant nested copy (~15+ GB) was identified and removed, and the archive was re-extracted cleanly before import.

---

### 3.2 Importing the VM into VirtualBox

The cleaned `.vbox` file was registered in VirtualBox via **Machine → Add**, which automatically linked the associated `.vdi` virtual hard disk.

**Import Specifications:**
- **VM Name:** `kali-linux-2026.2-virtualbox-amd64`
- **Memory:** 4096 MB RAM
- **Processors:** 3 vCPUs
- **Storage:** 80.09 GB VDI (Dynamically allocated)
- **Network Adapter:** Attached to `NatNetwork`

---

### 3.3 First Boot and Login

1. Powered on the Kali Linux virtual machine.
2. Verified the graphical boot sequence and login screen loaded without system errors.
3. Authenticated using default pre-built credentials:
   - **Username:** `kali`
   - **Password:** `kali`
4. Confirmed the Kali XFCE desktop environment loaded properly.

---

### 3.4 Hardening Default Credentials

Pre-built virtual machines ship with well-known default credentials (`kali:kali`). As a mandatory security baseline, account credentials were changed immediately after first login:

```bash
# 1. Update user account password
passwd

# 2. Reset and secure root account password
sudo passwd root
```

- Verified successful authentication by logging out and logging back in with the new credentials.
- Ensured elevated `root` sessions do not rely on standard default passwords.

---

### 3.5 Configuring an Isolated Lab Network (NAT Network)

VirtualBox's default **NAT** mode places each virtual machine in its own isolated network sandbox. Under standard NAT, VMs cannot communicate with each other, preventing essential multi-machine penetration testing workflows (e.g., Kali attacking a target VM).

**Implementation:** Configured a dedicated **NAT Network** (`NatNetwork`) allowing all lab machines to share a private virtual subnet while retaining outbound internet connectivity for OS updates and security tool installation.

**VirtualBox Network Manager Settings (`File → Tools → Network Manager → NAT Networks`):**
- **Network Name:** `NatNetwork`
- **IPv4 Subnet Prefix:** `10.0.2.0/24`
- **DHCP Server:** Enabled
- **IPv6 Support:** Disabled

**VM Network Adapter Configuration:**
- **Attached to:** NAT Network (`NatNetwork`)
- **Promiscuous Mode:** `Allow All`
  > Setting Promiscuous Mode to *Allow All* ensures packet-sniffing and traffic-analysis tools (Wireshark, tcpdump) can capture traffic passing through the shared virtual network segment, not just packets addressed directly to the VM.

---

### 3.6 Verifying Network Connectivity

Validated network interface status and IP address assignment from within the Kali terminal using `ifconfig`:

```bash
ifconfig
```

**Verification Output:**
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
      inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
      inet6 fe80::ddfa:72a4:12f:8f4a  prefixlen 64  scopeid 0x20<link>
      ether 08:00:27:5a:87:bc  txqueuelen 1000  (Ethernet)
      RX packets 6  bytes 3010 (2.9 KiB)
      RX errors 0  dropped 0  overruns 0  frame 0
      TX packets 39  bytes 4872 (4.7 KiB)
      TX errors 0  dropped 0  overruns 0  carrier 0  collisions 0
```

- **Interface `eth0`:** Status confirmed **UP and RUNNING**.
- **Assigned IP:** `10.0.2.15` on `10.0.2.0/24` subnet.
- **Packet Integrity:** 0 RX/TX errors, 0 dropped packets.

---

### 3.7 Clean Session Shutdown

Performed a graceful VM shutdown via the desktop power menu (`Log Out → Shut Down`) to verify the virtual machine closes cleanly without file system corruption, preparing it for upcoming lab modules.

---

## ✅ Task Checklist

| # | Task Description | Verification | Status |
|:---:|---|---|:---:|
| 1 | Download & extract official Kali Linux 2026.2 VirtualBox image | Verified archive integrity | ✔ Completed |
| 2 | Identify & remove duplicate nested extracted files | Reclaimed ~15+ GB disk space | ✔ Completed |
| 3 | Import Kali VM into VirtualBox via `.vbox` configuration | Linked to 80.09 GB VDI | ✔ Completed |
| 4 | First boot verification & desktop GUI login | Successfully reached desktop | ✔ Completed |
| 5 | Security hardening: change default `kali` and `root` passwords | Verified new credentials | ✔ Completed |
| 6 | Create isolated NAT Network (`NatNetwork` – `10.0.2.0/24`) | DHCP enabled in VirtualBox | ✔ Completed |
| 7 | Attach VM adapter & configure Promiscuous Mode to *Allow All* | Sniffing capability enabled | ✔ Completed |
| 8 | Verify network interface status and IP address via `ifconfig` | `eth0` active at `10.0.2.15/24` | ✔ Completed |
| 9 | Graceful shutdown and session restart test | Verified clean power cycle | ✔ Completed |

---

## 🌐 Lab Subnet & IP Addressing Plan

| Host / VM | Role | IP Address | Subnet | Adapter Mode |
|---|---|---|---|---|
| **Host Machine** | Windows 10/11 (Physical) | N/A (Host) | Host LAN | Isolated |
| **Virtual Gateway** | VirtualBox NAT Engine | `10.0.2.1` | `10.0.2.0/24` | NAT Network |
| **Kali Linux 2026.2** | Attacker Machine | `10.0.2.15` | `10.0.2.0/24` | NatNetwork (DHCP) |
| **Metasploitable 2** | Victim Machine (Planned – W2+) | `10.0.2.x` | `10.0.2.0/24` | NatNetwork (DHCP) |
| **Windows Target** | Victim Machine (Planned – W2+) | `10.0.2.x` | `10.0.2.0/24` | NatNetwork (DHCP) |

---

## 💡 Observations & Key Learnings

- **VM Configuration Links:** `.vbox` XML and `.vdi` disk files must be kept together; moving or renaming one breaks the link within the VirtualBox registry.
- **Network Isolation vs Inter-Connectivity:** Default VirtualBox NAT isolates VMs from one another. Using **NAT Network** enables inter-VM communication (Attacker ↔ Victim) while still protecting the host's physical network from lab traffic.
- **Promiscuous Mode Requirement:** Packet capture tools like Wireshark require Promiscuous Mode enabled (*Allow All*) on the virtual NIC to inspect non-unicast traffic on the virtual segment.
- **Credential Hardening:** Pre-built VM images must always have default credentials updated immediately after first boot to prevent unauthorized access.

---

## 🔭 Next Steps (Week 2 Preview)

With the baseline attacker machine and isolated `10.0.2.0/24` lab subnet established, the next phase will cover:
- Importing target vulnerable virtual machines (Metasploitable 2) into the `NatNetwork`.
- Conducting reconnaissance, OSINT, and footprinting (Maltego, theHarvester, GHDB).
- Performing network host discovery and port scanning with **Nmap** and **Zenmap**.
- Compiling formal Penetration Testing documentation.

---

## 🐞 Troubleshooting Log

| Issue Encountered | Root Cause | Resolution |
|---|---|---|
| **Duplicate file structure after archive extraction** | Archive extracted into a nested folder of the same name, containing an identical inner copy of the `.vbox` and `.vdi` files (~15+ GB redundant data). | Identified duplicate paths, removed the redundant nested folder, and re-extracted the archive cleanly before importing the primary `.vbox` configuration. |
| **"Invalid settings detected" in Network tab** | NAT Network adapter type was selected, but no specific network name had been chosen from the "Name" dropdown. | Created the `NatNetwork` via VirtualBox's Network Manager first, then re-selected it from the VM's **Network → Name** dropdown. |

---

## ⚖️ Ethical Statement & Disclaimer

> All activities documented in this report are conducted exclusively for **educational and authorized security testing purposes** within an isolated virtual lab environment. No unauthorized external networks, systems, or third-party devices were scanned or accessed.

---

## 🔗 References & Documentation

- 📄 **Submitted Report:** [Week 1 Lab Setup Report (PDF)](../Reports/Week1_Lab_Setup_Report.pdf)
- 🐉 **Kali Linux:** [Official Downloads](https://kali.org/get-kali)
- 🧰 **Oracle VirtualBox:** [Downloads & Documentation](https://virtualbox.org/wiki/Downloads)
- 🛡️ **NetworkWalks Academy:** [networkwalks.com](https://www.networkwalks.com/)

---

<p align="center">
  <strong>NetworkWalks Academy</strong> · Cybersecurity Internship Batch B082 · August 2026<br>
  <em>Instructor: Waqas Karim (CCIE) · Intern: Mithun Kumar Rajak</em>
</p>
