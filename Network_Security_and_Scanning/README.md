# Network Security and Scanning
**Intern:** Fatimah Adnan  
**Organization:** ApexPlanet  

## 📌 Task Overview
This project involved a full-cycle security assessment. I performed reconnaissance, vulnerability scanning, and traffic analysis to identify and mitigate risks on a target system.

## 🛠 Tools & Methodology
* **Reconnaissance:** Used `Nmap` to identify open ports (21, 23, 445, etc.).
* **Vulnerability Scanning:** Used `OpenVAS/GVM` to find a **10.0 Critical** backdoor.
* **Traffic Analysis:** Used `Wireshark` to sniff plaintext FTP credentials.
* **Network Defense:** Used `iptables` to block unauthorized traffic.

## 📑 Technical Evidence
| Task | Result |
| :--- | :--- |
| **Nmap Scan** | Discovered 20+ vulnerable services. |
| **OpenVAS** | Confirmed vsFTPd 2.3.4 Backdoor (Critical). |
| **Wireshark** | Intercepted username: `msfadmin` / password: `msfadmin`. |
| **Firewall** | Successfully filtered Port 21 via CLI. |

---
*Generated as part of the ApexPlanet Cybersecurity Internship.*
