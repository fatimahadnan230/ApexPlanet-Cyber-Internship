📑 **Notes**

Task 1 - Foundation & Environment Setup
Timeline: Days 1–12

Internship: ApexPlanet Cybersecurity Program (2026)

Objective: Build strong fundamentals in cybersecurity, networking, and cryptography while establishing a professional hacking lab.

🛡️ 1. Cybersecurity Basics & Theory
The "Theoretical Core" of all security operations.

The CIA Triad
Confidentiality: Protecting data from unauthorized access (Encryption).

Integrity: Ensuring data hasn't been tampered with (Hashing).

Availability: Ensuring systems and data are accessible when needed (Uptime/Redundancy).

Threats & Attack Vectors
Common Threats: Phishing (Social Engineering), Malware (Viruses/Worms), DDoS (Flooding networks), SQL Injection (Database manipulation), and Ransomware.

Attack Vectors: The "path" an attacker takes, such as unpatched software, weak wireless protocols, or insider threats.

🏗️ 2. Lab Environment Setup
Creating a "Sandboxed" environment to safely perform penetration testing.

Virtualization: Used VirtualBox to run multiple Operating Systems on one physical machine.

Attacker Machine: Kali Linux (Pre-loaded with security tools).

Target Machine: Metasploitable2 (Intentionally vulnerable for practice).

Network Configuration: Set to Host-Only Adapter. This isolates the lab from the internet while allowing the Attacker and Target to communicate.

<img width="638" height="477" alt="image" src="https://github.com/user-attachments/assets/88750418-6666-4bae-965d-006ea2833a55" />
<img width="717" height="396" alt="image" src="https://github.com/user-attachments/assets/33f64784-f034-4d7b-b100-c45c60b5e84e" />


🐧 3. Linux Fundamentals
The terminal is the primary interface for security professionals.

Navigation: pwd (print working directory), ls -la (list all files with permissions), cd (change directory).

Permissions: chmod (change permissions, e.g., chmod 700 for private files) and chown (change owner).

System Management: apt update (package updates) and sudo (administrative privileges).

Network Tools: ifconfig/ip addr (view IP), ping (check connectivity), netstat (view active connections).

🌐 4. Networking Basics
Understanding how data moves across the "wire."

OSI Model: A 7-layer framework. We focused on Layer 3 (Network - IP) and Layer 4 (Transport - TCP/UDP).

TCP/IP Suite: The standard for internet communication.

Protocols: * DNS: Translates names (https://www.google.com/search?q=google.com) to IPs.

HTTP/HTTPS: Web traffic (Port 80/443).

Subnetting: Dividing a network into smaller, manageable segments for security.

🔐 5. Cryptography Basics
Protecting information using mathematical principles.

Symmetric Encryption: Uses one key for both encryption and decryption (e.g., AES).

Asymmetric Encryption: Uses a Public Key to encrypt and a Private Key to decrypt (e.g., RSA).

Hashing: A one-way function used for integrity.

MD5: Older, faster, but less secure.

SHA-256: Industry standard for verifying file integrity.

Hands-on: Used OpenSSL to encrypt a message and sha256sum to verify a file's fingerprint.

🛠️ 6. Tool Familiarization
The "Big Four" tools used in this phase:

Wireshark: A packet sniffer used to analyze live network traffic.

Nmap: A network mapper used to find open ports and running services.

Burp Suite: A web proxy used to intercept and modify web requests.

Netcat (nc): The "Swiss Army Knife" of networking used for debugging and manual connections.

<img width="658" height="700" alt="01 04 2026_23 56 40_REC" src="https://github.com/user-attachments/assets/babb7793-9c13-425a-b57f-115e3ac0ae37" />

Additional Screenshots:
<img width="669" height="286" alt="02 04 2026_01 03 25_REC" src="https://github.com/user-attachments/assets/ffd394c2-0b2f-41ed-bab2-0306f1e68ee4" />

<img width="673" height="553" alt="02 04 2026_00 57 36_REC" src="https://github.com/user-attachments/assets/733120b8-1696-4aec-acc6-4c21d42d2b2e" />

<img width="952" height="930" alt="01 04 2026_23 43 51_REC" src="https://github.com/user-attachments/assets/fd54d8f9-b082-4d09-9adf-9e003d11800e" />

<img width="1830" height="792" alt="02 04 2026_01 19 47_REC" src="https://github.com/user-attachments/assets/34b5203c-9068-47e1-a337-94a6be92ab61" />


🏁 Task 1 Deliverables Checklist
[ ] Lab Setup Report: PDF containing all technical steps.

[ ] GitHub Repo: This repository, including these Notes and the Linux Cheat-Sheet.

[ ] Video Walkthrough: 5-minute demo showing the lab in action.
