# 🐧 Linux Systems & Security Reference Manual
> **Project:** ApexPlanet Cybersecurity Internship  
> **Phase:** Task 1 - Core Fundamentals & Environment Setup  
> **Classification:** Technical Documentation

---

## 📂 I. File System & Navigation
*Precise navigation is the foundation of effective digital forensics and system auditing.*

| Command             | Technical Function      | Security Use Case                                         |
| :---                | :---                    | :---                                                      |
| `pwd`               | Print Working Directory | Verifying absolute paths for automated scripts.           |
| `ls -laSh`          | List All (Size Sorted)  | Identifying hidden backdoors (`.dotfiles`) or large logs. |
| `cd /etc`           | Configuration Root      | Accessing system-wide policies and user hashes.           |
| `cat /proc/version` | Kernel Identification   | Determining OS version for kernel-level exploit research. |

---

## 🔐 II. Permissions & Access Control
*Security is governed by the **Principle of Least Privilege (PoLP)**. Identifying misconfigurations is a key skill.*

### 1. Permission Notation (Octal)
- **4 (Read)**, **2 (Write)**, **1 (Execute)**
- **755:** Owner (Full), Group/Public (Read/Execute). Standard for binaries.
- **600:** Owner (Read/Write), Group/Public (None). Best practice for **SSH Private Keys**.

### 2. Core Management Commands
- `chmod [octal] [file]`: Modifies file mode bits to restrict or grant access.
- `chown [user]:[group] [file]`: Changes file ownership (e.g., reclaiming files from `root`).
- `sudo -i`: Escalate to a persistent **Superuser** environment for system-wide configuration.

---

## 🌐 III. Networking & Protocol Analysis
*Mapping the attack surface via Layer 3 and Layer 4 diagnostic utilities.*

| Command          | Protocol/Flag     | Cybersecurity Value                                        |
| :---             | :---              | :---                                                       |
| `ip addr show`   | **L3 Interface**  | Identifying the **Host-Only** private IP in a lab.         |
| `ping -c 5`      | **ICMP Echo**     | Verifying host availability and network latency.           |
| `netstat -plant` | **TCP/UDP Stack** | Identifying unauthorized listening services or backdoors.  |
| `traceroute -I`  | **ICMP Hops**     | Mapping network path and identifying NAT gateways.         |
| `nslookup`       | **DNS Query**     | Resolving domain names to IP addresses for reconnaissance. |

---

## 🛠️ IV. Package & Process Management
*Maintaining a clean and updated attack environment.*

- **Update Cycle:** `sudo apt update && sudo apt upgrade` 
  - *Ensures all security tools (Nmap, Burp Suite) are patched.*
- **Search:** `apt search [tool]` 
  - *Searching for specific binaries within the Kali repository.*
- **Manual Install:** `dpkg -i [.deb]` 
  - *Installation of standalone security software.*
- **Process Audit:** `ps aux | grep [process]` 
  - *Identifying running processes (e.g., checking if a listener is active).*

---

## 🛡️ V. Cryptographic Operations (OpenSSL)
*Hands-on verification of **Confidentiality** and **Integrity**.*

### 1. Data Integrity (Hashing)
```bash
# Verify file integrity using SHA-256
sha256sum lab_report.pdf

# Encrypting technical notes with AES-256-CBC
openssl enc -aes-256-cbc -salt -in notes.txt -out notes.enc
