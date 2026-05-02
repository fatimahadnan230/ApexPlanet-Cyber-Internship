# 🐧 Linux Systems & Security Reference Manual

**Project:** ApexPlanet Cybersecurity Internship  
**Phase:** Task 3 — System Auditing, Log Analysis & Hardening  
**Classification:** Technical Documentation  

---

## 📜 I. Advanced Log Analysis & Forensic Artifacts

| Command | Technical Function | Security Use Case |
| :--- | :--- | :--- |
| **`tail -f /var/log/auth.log`** | Real-time Auth Monitoring | Detecting brute-force SSH attacks as they happen. 🛡️ |
| **`grep "Failed password" /var/log/auth.log`** | Filter Auth Failures | Identifying specific IPs attempting unauthorized entry. 🚫 |
| **`journalctl -xe`** | Systemd Error Logs | Debugging services that failed to start due to errors. 🛠️ |
| **`dmesg | grep -i "usb"`** | Kernel Ring Buffer | Detecting "BadUSB" or unauthorized hardware. 🔌 |
| **`lastlog`** | User Login History | Checking when a specific user last accessed the system. 👤 |

---

## 🔍 II. System Auditing & Resource Profiling

* **`top` / `htop`**: Real-time process monitoring. 📊
* **`ps -ef --forest`**: Visualizes the process hierarchy to identify suspicious relationships. 🌳
* **`lsof -i`**: List Open Files to map processes to active network connections. 🕵️‍♂️
* **`df -Th`**: Monitoring for Disk Exhaustion attacks. 💾
* **`free -m`**: Analyzing memory consumption to detect memory-resident malware. 🧠

---

## 🛡️ III. System Hardening & Service Configuration

### 1. Service Control
* **`systemctl list-unit-files --type=service`**: Audit all installed services. 📋
* **`systemctl disable --now bluetooth.service`**: Attack surface reduction. 📉

### 2. Kernel Hardening
* **`sysctl -w net.ipv4.conf.all.accept_redirects=0`**: Preventing ICMP redirection (MitM) attacks. 🛣️
* **`sysctl -p`**: Applying hardening changes permanently from `/etc/sysctl.conf`. 💾

---

## 🧪 IV. Advanced Text Wrangling for Reports

**Extract Top Attackers:**
`awk '{print $1}' access.log | sort | uniq -c | sort -nr`  
Identifies the most frequent IP addresses in a web log to pinpoint potential DoS sources. 🧮

**Identify SUID Binaries:**
`find / -perm -4000 -type f 2>/dev/null`  
Locates files with the SUID bit set—prime targets for Privilege Escalation exploits. 🚩

**Batch Configuration Edit:**
`sed -i 's/PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config`  
Directly modifies the SSH configuration to prevent root-level remote access. 🔒

---

## 📂 V. Secure Data Handling & Backup

* **`tar -cvpzf backup_etc.tar.gz /etc`**: Creates a compressed backup. 📦
* **`diff original.conf modified.conf`**: Compares changes to ensure no syntax errors. ⚖️
* **`umask 077`**: Sets default permissions so new files are private. 🌑
* **`shasum -a 256 [file]`**: Generates a hash to verify file integrity. 🔡
