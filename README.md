# 🛡️ ApexPlanet Cybersecurity Internship
> **Phase:** Foundation & Environment Setup  
> **Timeline:** Days 1–12  
> **Objective:** Establishing a virtualized penetration testing lab and demonstrating core security principles.

---

## 📂 1. Project Overview
This repository contains the technical documentation for Task 1. The goal was to build a secure environment for future security testing and to master the fundamentals of Linux, Networking, and Cryptography.

## 🏗️ 2. Lab Architecture & Setup
I configured a private, isolated virtual network to ensure "Air-Gapped" security testing.
- **Hypervisor:** VirtualBox / VMware
- **Attacker:** Kali Linux (2026.x)
- **Target:** Metasploitable2 (Vulnerable Linux VM)
- **Networking:** Host-Only Adapter (Subnet: 192.168.56.0/24)

## 🛡️ 3. The CIA Triad Implementation
I applied the three pillars of cybersecurity within this lab setup:
* **Confidentiality:** Demonstrated by using **OpenSSL (AES-256-CBC)** to encrypt sensitive data.
* **Integrity:** Verified by generating **SHA-256 Hashes** to ensure files were not tampered with.
* **Availability:** Confirmed by using **ICMP (Ping)** and **Nmap** to ensure services were reachable.

## 🛠️ 4. Technical Deliverables
- **[Linux-Cheat-Sheet.md](./Linux-Cheat-Sheet.md):** A comprehensive reference guide for system administration.
- **Lab_Setup_Report.pdf:** Official report containing screenshots of the environment, Nmap scans, and Wireshark captures.
- **5-Minute Walkthrough:** [Link to your LinkedIn Featured Video]


## Task 3: Web Application Penetration Testing (DVWA)

In this task, I performed security testing on a web application environment to identify and exploit common vulnerabilities.

### 🛡️ Vulnerabilities Exploited
* **SQL Injection (SQLi):** Used `' OR '1'='1` to bypass authentication and dump the user database.
* **Cross-Site Scripting (XSS):**
    * **Reflected:** Triggered immediate browser alerts via URL parameters.
    * **Stored (Persistent):** Bypassed HTML character limits to inject a permanent script into the guestbook database.
* **Cross-Site Request Forgery (CSRF):** Crafted a malicious URL to force a password change without user consent.
* **Local File Inclusion (LFI):** Exploited path traversal to read sensitive system files (`/etc/passwd`).

### 🛠️ Remediation & Defense
* Configured PHP settings (`php.ini`) to enable/disable specific security flags.
* Tested "Impossible" security levels to verify the effectiveness of **Anti-CSRF tokens**, **PDO Prepared Statements**, and **Input Sanitization**.

[View Task 3 Report](./ApexPlanet_Task3_Report.pdf)


---
*Submitted by: Fatimah Adnan* *ApexPlanet Internship Program - 2026*
