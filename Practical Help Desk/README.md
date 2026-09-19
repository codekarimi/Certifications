# 🎧 Practical Help Desk — TCM Security Academy

> Certificate of completion for a 16.5-hour, hands-on course covering entry-level IT support: hardware repair, Windows and Linux administration, networking, remote support, ticketing, security basics, and a full Active Directory lab.

![Provider](https://img.shields.io/badge/Provider-TCM%20Security-C2185B?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Introductory-blue?style=for-the-badge)
![CEUs](https://img.shields.io/badge/Duration-16.5%20CEU%20Hours-0A7E8C?style=for-the-badge)
![Date](https://img.shields.io/badge/Completed-August%202026-informational?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Earned-success?style=for-the-badge)



---

## 📋 Certificate Details

| Field | Value |
|-------|-------|
| **Certificate Name** | Certificate in Practical Help Desk |
| **Issuing Organization** | TCM Security, an Educate 360 brand |
| **Completion Date** | August 18, 2026 |
| **Credential ID** | Completion Number: `djU4OTE4Ni0zMjQ` <!-- transcribed from the image; please double-check --> |
| **Certificate Type** | Course Completion (16.5 CEU hours) |
| **Validity** | No expiration stated on the certificate |
| **Verification** | No public verification link available; the completion number above is printed on the certificate <!-- add a URL if TCM Academy provides one --> |
| **Course Difficulty** | Introductory (no prerequisites) |
| **Instructor** | Andrew Bellini |
| **My Context** | IT Support professional transitioning into Cloud Networking |

> **📝 Transparency note:** This is a **certificate of completion** for the Practical Help Desk *course*. It is **not** the [Practical Help Desk Associate (PHDA)](https://certifications.tcm-sec.com/phda/) exam certification, which is a separate hands-on exam.

---

## 📚 What I Learned

The course has 16 sections, with **7+ hours of hands-on labs** (marked 🖥️) and "Ticket Interrupt" scenarios (🎟️) that simulate real support requests. I grouped the sections below into ten modules.

<!-- Trim the hands-on bullets to what you personally practiced. -->

### Module 1 — Intro to IT, Help Desk Roles & Soft Skills

This module explained what IT departments do and where the help desk fits. It included a review of real help desk job postings and a soft-skills section on communication and applying for jobs.

**🧠 Key Concepts**
- Purpose of IT in a modern business and how an IT department is organized
- Common IT roles (help desk, sysadmin, network, security) and how they escalate to each other
- Help desk tiers, responsibilities, and what employers ask for in job postings
- Ticket etiquette: clear documentation, prioritization, and professional communication
- Why note-taking is a core professional habit

**🛠️ Hands-on Skills Gained**
- I can read a help desk job posting and map each requirement to a skill I can demonstrate
- I can explain what a Level 1 technician does versus what gets escalated
- I can document an issue and its resolution so someone else can follow it

**Tools/Technologies:** Job posting analysis, note-taking workflows, Discord community for help

---

### Module 2 — Intro to Computing

A low-level look at how computers represent and process information. This is the foundation for understanding why hardware, operating systems, and networks behave as they do.

**🧠 Key Concepts**
- Binary and number systems, bits and bytes
- Character encoding (how text becomes bits)
- How a CPU computes, step by step (two-part walkthrough)
- Compilers and layers of abstraction from machine code to applications
- Why file sizes, IP addresses, and permissions all trace back to binary

**🛠️ Hands-on Skills Gained**
- I can convert between binary, decimal, and hexadecimal
- I can explain bytes, kilobytes, and megabytes and why storage sizes appear differently to the OS and to manufacturers
- I can explain how a program becomes instructions the CPU can run

**Tools/Technologies:** Binary/hex conversion, ASCII/Unicode

---

### Module 3 — Desktop & Laptop Hardware Repair

Physical troubleshooting: identifying components, working safely, and replacing parts in both desktops and laptops.

**🧠 Key Concepts**
- ESD precautions and safely opening a computer
- CPU, RAM, storage drives, PSU, GPU, and motherboard roles
- Ports, cables, and peripherals
- POST and the BIOS/UEFI
- Laptop-specific parts: battery, RAM, drives, and CMOS battery

**🛠️ Hands-on Skills Gained**
- I can identify and replace RAM, drives, and batteries in desktops and laptops
- I can use POST behavior and BIOS settings to narrow down a hardware fault
- I can tell a failing component from a software problem

**Tools/Technologies:** Antistatic gear, BIOS/UEFI, standard screwdriver sets

---

### Module 4 — Operating Systems & Virtualization

This module covered what an operating system does and how to build a safe, repeatable lab using virtual machines.

**🧠 Key Concepts**
- Kernel vs. userland, and the role of the OS
- File systems and file types
- Virtual machines, hypervisors, and containers
- Advantages of virtualization: isolation, snapshots, cost, and quick rebuilds

**🛠️ Hands-on Skills Gained** 🖥️
- I can install a hypervisor (VirtualBox) and create VMs
- I can allocate CPU, RAM, and disk sensibly for a lab
- I can explain when to use a VM vs. a container

**Tools/Technologies:** VirtualBox, VM snapshots, file systems (NTFS, ext4 concepts)

---

### Module 5 — Windows Administration

The largest hands-on module. I built a Windows 11 VM and worked through the everyday tools a support technician uses.

**🧠 Key Concepts**
- Local vs. domain accounts
- Local file permissions
- Windows Update behavior
- Event Viewer logs and Device Manager
- Task Manager, Services, and the Registry
- Task Scheduler and the Command Prompt

**🛠️ Hands-on Skills Gained** 🖥️ 🎟️
- I can install Windows 11 in a VM and use snapshots to roll back a broken configuration
- I can create, modify, and disable local user accounts and set file permissions
- I can install and remove software, manage updates, and troubleshoot services
- I can use Event Viewer and Task Manager to locate the cause of slowness or crashes
- I can schedule recurring tasks

**Tools/Technologies:** Windows 11, `eventvwr.msc`, `services.msc`, `regedit`, Task Manager, Task Scheduler, cmd

```bat
net user
net user jdoe /active:no
sfc /scannow
sc query wuauserv
tasklist | findstr /i chrome
taskkill /IM chrome.exe /F
schtasks /query /fo LIST
```

---

### Module 6 — Linux Administration

An introduction to running Ubuntu from the terminal, including users, permissions, scripting, scheduling, and updates.

**🧠 Key Concepts**
- Linux distributions and the GNU/Linux model
- User levels and `sudo`
- Filesystem hierarchy (`/etc`, `/var`, `/home`, and others)
- File permissions (read/write/execute for user, group, other)
- Bash scripting fundamentals
- Cron scheduling and package management with `apt`

**🛠️ Hands-on Skills Gained** 🖥️ 🎟️
- I can install Ubuntu in a VM and navigate it from the terminal
- I can create users and manage their privileges (Ticket Interrupt scenario)
- I can read and change permissions with `chmod` and `chown`
- I can write simple Bash scripts and schedule them with cron
- I can keep a system patched with `apt`

**Tools/Technologies:** Ubuntu, Bash, `sudo`, `crontab`, `apt`

```bash
sudo adduser jdoe
sudo usermod -aG sudo jdoe
ls -l /etc/passwd
chmod 640 report.txt
crontab -e            # e.g. 0 2 * * * /home/jdoe/backup.sh
sudo apt update && sudo apt upgrade -y
```

---

### Module 7 — Networking Fundamentals

From the OSI model to subnetting to diagnosing real connectivity issues.

**🧠 Key Concepts**
- OSI model layers and where common problems appear
- IP addresses, subnet masks, and CIDR notation
- Hubs, switches, ARP, and routers
- Ports and common services
- VPNs and the OpenVPN client
- Systematic network troubleshooting

**🛠️ Hands-on Skills Gained** 🖥️ 🎟️
- I can calculate network ranges and host counts from CIDR notation
- I can configure a small office/home office (SOHO) router
- I can use command-line tools to isolate DNS, gateway, and connectivity faults
- I can connect to a VPN using OpenVPN

**Tools/Technologies:** OpenVPN, SOHO router configuration, `ipconfig`, `ping`, `tracert`, `nslookup`, `arp`, `netstat`

```bat
ipconfig /all
ping 8.8.8.8
nslookup example.com
tracert example.com
arp -a
netstat -ano
```

---

### Module 8 — Remote Support & Ticketing

How support is delivered when the user isn't in the room, and how requests are tracked from open to close.

**🧠 Key Concepts**
- SSH, RDP, and VNC, and when each is appropriate
- Third-party remote support tools
- Phone support techniques
- Why ticketing systems matter: accountability, history, SLAs, and reporting
- Ticket lifecycle: create, comment, assign, escalate, and close

**🛠️ Hands-on Skills Gained** 🖥️ 🎟️
- I can connect to Linux and Windows machines using SSH and RDP
- I can run my own self-hosted ticketing system (Peppermint) using Docker
- I can create, assign, comment on, and close tickets
- I can handle a support call calmly and gather the right details

**Tools/Technologies:** OpenSSH, RDP (`mstsc`), VNC, Docker, Peppermint

```bash
ssh jdoe@192.168.56.101
docker ps
docker compose up -d
```

---

### Module 9 — Security Fundamentals

The security basics that every IT support person needs, including how to spot and report threats.

**🧠 Key Concepts**
- CIA triad (confidentiality, integrity, availability)
- Firewall, antivirus, EDR, and SIEM and how each fits together
- IAM, MFA, and SSO
- Social engineering and phishing
- Secure device disposal

**🛠️ Hands-on Skills Gained** 🎟️
- I can recognize a phishing attempt and escalate it correctly
- I can explain why MFA and least privilege reduce risk
- I can describe what each layer of defensive tooling does
- I can follow secure disposal practices for retired devices

**Tools/Technologies:** Security tooling concepts (firewall, AV, EDR, SIEM), IAM/MFA/SSO

---

### Module 10 — Capstone: Active Directory Lab

I built a Windows domain from scratch, the same environment I'll support in most business settings.

**🧠 Key Concepts**
- What Active Directory is and what a domain controller does
- Domain users, OUs, and security groups
- Group Policy Objects (GPOs) for centralized configuration
- PowerShell fundamentals and automation
- Resetting passwords in a domain environment

**🛠️ Hands-on Skills
