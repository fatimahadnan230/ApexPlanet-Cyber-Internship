# 🐧 Linux Systems & Security Reference Manual

**Project:** ApexPlanet Cybersecurity Internship  
**Phase:** Task 3 — System Auditing, Log Analysis & Hardening  

---

## 📜 I. Advanced Log Analysis & Forensic Artifacts

| Command | Technical Function | Security Use Case |
| :--- | :--- | :--- |
| **`tail -f /var/log/auth.log`** | Real-time Auth Monitoring | Detecting brute-force SSH attacks. |
| **`grep "Failed password" /var/log/auth.log`** | Filter Auth Failures | Identifying specific attacker IPs. |

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
