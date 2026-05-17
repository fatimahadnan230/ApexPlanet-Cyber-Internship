# 📝 Cybersecurity Lab Study Notes: Task 3

## 🧠 Core Concepts & Methodologies

### 1. Network Reconnaissance & Metasploit Integration
* **Database Persistence:** Using `msfdb init` before running scans allows Metasploit to store host data, services, and vulnerabilities directly in a PostgreSQL backend. This tracks data across complex engagements without re-running loud network sweeps.
* **Service Enumeration:** The command `db_nmap -sV -O` conducts version detection (`-sV`) and operating system fingerprinting (`-O`). Identifying exact banner versions is crucial for mapping targets to known CVEs.

### 2. Backdoor Exploitation (UnrealIRCd)
* **Mechanism:** The `unreal_ircd_3281_backdoor` targets a malicious modification historical attackers slipped into the UnrealIRCd source archive (version 3.2.8.1). Sending a specific trigger sequence sequence (like `AB`) prompts the server to execute arbitrary shell commands with the permissions of the running process.
* **Privilege Level:** Because legacy daemons often incorrectly run under high-privilege accounts, triggering this backdoor immediately dropped the session into a `root` context (`uid=0`), bypassing the need for local privilege escalation.

### 3. Credential Attacks: Online vs. Offline
| Attack Type | Tool Used | Mechanism | Noise Level | Key Constraint |
| :--- | :--- | :--- | :--- | :--- |
| **Online Brute Force** | `Hydra` | Repeatedly attempts active authentication over a live service protocol (e.g., SSH). | **High** (Triggers system logs like `auth.log`, easily caught by Fail2ban). | Network latency, rate-limiting, and account lockout policies. |
| **Offline Cracking** | `John the Ripper` | Computes hashes locally against stolen data (`/etc/shadow`) using wordlists. | **Zero** (Completely stealthy; no network footprints). | Computational power and the strength/entropy of the target password. |

* **The Unshadow Process:** Linux stores account metadata in `/etc/passwd` (readable by all) and cryptographic password hashes in `/etc/shadow` (readable only by root). The `unshadow` utility combines these two files into a unified format that cracking utilities can parse.

### 4. Social Engineering Cloner Dynamics
* **Credential Harvesting:** The Social-Engineer Toolkit (SET) clones a legitimate login portal page structure and spins up a local rogue HTTP proxy server. 
* **Data Exfiltration:** When a victim inputs data, the proxy intercepts the HTTP POST request payload, extracting the plain-text form parameters (`username` and `password`) before optionally redirecting the user back to the real site to avoid suspicion.

### 5. Malware Analysis Baselines
* **Static Analysis (`strings`):** Inspects binary printable character sequences without execution. It checks compiled dependencies (`libc.so.6`), embedded URLs, or system calls. If an unknown binary contains high-entropy randomness or references to raw socket headers, it suggests packers or malicious networking.
* **Dynamic Analysis (`strace`):** Intercepts low-level system calls (`execve`, `openat`, `mmap`, `write`) executed between the application and the Linux kernel at runtime. This provides behavioral visibility regardless of binary obfuscation.

### 6. Host Defensive Hardening
* **Zero-Trust Firewalling (`UFW`):** Restricting host attack surface starts with a strict default posture (`deny incoming`, `allow outgoing`). Explicit access rules are carved out only for verified business ports (SSH/22, HTTP/80).
* **Service Minimization:** Unused network-facing backgrounds or auxiliary kernel components (e.g., `ModemManager`) should be stopped, disabled from startup, and **masked** (linked to `/dev/null`) to permanently prevent other processes from accidentally triggering them.
