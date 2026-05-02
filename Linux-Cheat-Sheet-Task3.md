# 🐧 Linux Systems & Security Reference Manual

**Project:** ApexPlanet Cybersecurity Internship  
**Phase:** Task 3 — System Auditing, Log Analysis & Hardening  
**Classification:** Technical Documentation  

---

## 📜 I. Advanced Log Analysis & Forensic Artifacts

In Task 3, logs serve as the primary telemetry for detecting unauthorized access or system anomalies.

| Command | Technical Function | Security Use Case |
| :--- | :--- | :--- |
| `tail -f /var/log/auth.log` | Real-time Auth Monitoring | Detecting brute-force SSH attacks as they happen. 🛡️ |
| `grep "Failed password" /var/log/auth.log` | Filter Auth Failures | Identifying specific IP addresses attempting unauthorized entry. 🚫 |
| `journalctl -xe` | Systemd Error Logs | Debugging services that failed to start due to misconfiguration. 🛠️ |
| `dmesg | grep -i "usb"` | Kernel Ring Buffer | Detecting "BadUSB" or unauthorized hardware insertions. 🔌 |
| `lastlog` | User Login History | Checking when a specific user last accessed the system. 👤 |

---

## 🔍 II. System Auditing & Resource Profiling

Auditing ensures the environment is free of malicious background processes (cryptominers, reverse shells) that drain system resources.

*   **`top` / `htop`**: Real-time process monitoring. Identify high CPU usage from unfamiliar binaries. 📊
*   **`ps -ef --forest`**: Visualizes the process hierarchy to identify suspicious parent-child process relationships. 🌳
*   **`lsof -i`**: **L**ist **O**pen **F**iles. Crucial for mapping processes to active network connections. 🕵️‍♂️
*   **`df -Th`**: Monitoring for "Disk Exhaustion" attacks where logs are flooded to crash the system. 💾

---

## 🛡️ III. System Hardening & Service Configuration

Focuses on reducing the attack surface by managing background services and securing kernel variables.

### 1. Service Control (systemctl)
*   `systemctl list-unit-files --type=service`: Audit all installed services to find unnecessary or "orphan" services. 📋
*   `systemctl disable --now bluetooth.service`: Attack surface reduction—disabling unused wireless protocols. 📉

### 2. Kernel Hardening (sysctl)
*   `sysctl -w net.ipv4.conf.all.accept_redirects=0`: Preventing ICMP redirection (Man-in-the-Middle) attacks. 🛣️
*   `sysctl -p`: Applying hardening changes permanently from the `/etc/sysctl.conf` file. 💾

---

## 🧪 IV. Advanced Text Wrangling for Reports

Utilizing "one-liners" to extract actionable intelligence from raw system data.

**Extract Top Attackers:**
```bash
awk '{print $1}' access.log | sort | uniq -c | sort -nr
