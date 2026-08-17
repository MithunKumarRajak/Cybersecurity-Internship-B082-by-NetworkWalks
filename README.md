# 🛡️ Cybersecurity & Ethical Hacking — Internship B082

[![Program](https://img.shields.io/badge/NetworkWalks-B082_Internship-0a66c2?style=for-the-badge&logo=shield&logoColor=white)](https://www.networkwalks.com)
[![Week](https://img.shields.io/badge/Current-Week_1-28a745?style=for-the-badge)](Week-1-Lab-Setup/)
[![Status](https://img.shields.io/badge/Status-In_Progress-f0ad4e?style=for-the-badge)](Week-1-Lab-Setup/)

> A 4-week remote cybersecurity internship by **[NetworkWalks Academy](https://www.networkwalks.com)**, guided by CCIE-certified industry experts. This repository documents my hands-on work — from lab setup to full penetration testing.

---

## 📌 Program at a Glance

|               | Detail                                      |
|---------------|---------------------------------------------|
| **Batch**     | B082 — August 2026                          |
| **Duration**  | 4 Weeks                                     |
| **Mode**      | 100% Remote + Weekly LIVE Zoom Sessions     |
| **Instructor**| Waqas Karim (CCIE)                          |
| **Focus**     | Penetration Testing, VAPT, Network Security |

---

## 📂 Repository Structure

```
.
├── README.md                  ← You are here
└── Week-1-Lab-Setup/
    └── README.md              ← Lab setup documentation & screenshots
```

> Weeks 2–4 will be added as each project is completed and submitted.

---

## 📆 Progress Tracker

| Week | Project                                                      | Track          | Status        |
|:----:|--------------------------------------------------------------|:--------------:|:-------------:|
|  1   | [Lab Setup — Kali + VirtualBox](Week-1-Lab-Setup/)           | 🔧 Essentials  | 🟡 In Progress |
|  2   | Footprinting, Scanning & Report Writing                      | 🔴 Red Team    | ⬜ Upcoming    |
|  3   | Cracking & Attacking (Metasploit, JTR)                       | 🔴 Red Team    | ⬜ Upcoming    |
|  4   | Full Pentest + Wireshark SOC Analysis                        | 🔴🔵 Red + Blue | ⬜ Upcoming    |

---

## 🖥️ Lab Environment

```
┌────────────────────────────────────────────────────┐
│                 HOST - Windows 10                  │
│          8 GB RAM / 256 GB SSD / Core i5           │
│                                                    │
│  ┌──────────────────────────────────────────────┐  │
│  │     VirtualBox - NATNetwork 10.0.0.0/24      │  │
│  │                                              │  │
│  │  ┌──────────┐   ┌──────────┐   ┌──────────┐  │  │
│  │  │   Kali   │   │  Win 10  │   │ Metaspl  │  │  │
│  │  │ 10.0.0.2 │   │10.0.0.10 │   │10.0.0.11 │  │  │
│  │  │ Attacker │   │  Victim  │   │  Victim  │  │  │
│  │  └──────────┘   └──────────┘   └──────────┘  │  │
│  └──────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────┘
```

| VM               | IP Address    | Role     |
|------------------|---------------|----------|
| Kali Linux       | `10.0.0.2/24` | Attacker |
| Windows 10       | `10.0.0.10/24`| Victim   |
| Metasploitable 2 | `10.0.0.11/24`| Victim   |
| Windows 7        | `10.0.0.16/24`| Victim   |

---

## 🛠️ Tools & Technologies

| Category       | Tools                     |
|----------------|---------------------------|
| Pentesting OS  | Kali Linux                |
| Scanning       | Nmap, Zenmap, Nessus      |
| Exploitation   | Metasploit, Burp Suite    |
| OSINT          | Maltego, theHarvester     |
| Analysis       | Wireshark                 |
| Cracking       | John The Ripper, Hydra    |

---

## ⚖️ Disclaimer

> **All work in this repository is strictly for educational purposes.**
> Testing is performed exclusively on **owned lab machines** within an isolated virtual environment.
> Unauthorized access to any system is illegal. I accept full responsibility for my actions.

---

## 🔗 Quick Links

| Resource              | Link                                                 |
|-----------------------|------------------------------------------------------|
| NetworkWalks Website  | [networkwalks.com](https://www.networkwalks.com)     |
| Instructor LinkedIn   | [Waqas Karim CCIE](https://linkedin.com/in/waqaskarim/) |
| NetworkWalks LinkedIn | [Follow](https://linkedin.com/company/networkwalks/) |

---

<p align="center">
  <strong>NetworkWalks Academy</strong> · Batch B082 · August 2026<br>
  <em>Instructor: Waqas Karim — CCIE</em>
</p>
