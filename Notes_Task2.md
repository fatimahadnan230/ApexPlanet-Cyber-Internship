# 📓 Task 2 Technical Audit Notes
**Project:** Network Security & Scanning (Days 13–24)  
**Status:** Completed & Verified  
**Intern:** Fatimah Adnan

---

### **1. Target Profile & Reconnaissance**
* **Target Machine:** Metasploitable 2 (Linux-based vulnerable VM)
* **Target IP:** `192.168.56.102`
* **Scan Profile:** Nmap aggressive service enumeration (`-sV -O -T4`)
* **Active Port Discovery:**
    * **Port 21:** vsFTPd 2.3.4 (Critical Risk)
    * **Port 23:** Telnet (Unencrypted Admin)
    * **Port 80:** Apache httpd 2.2.8
    * **Port 445:** Samba smbd 3.X (File Sharing)

### **2. Vulnerability Analysis (GVM/OpenVAS)**
* **Severity Score:** **10.0 (High/Critical)**
* **Vulnerability ID:** `CVE-2011-2523`
* **Description:** The vsFTPd 2.3.4 service contains a "backdoor" that responds with a shell on port 6200 when a specific username sequence is provided.
* **Verification:** Confirmed via automated GVM report and manual Nmap banner grabbing. Identification of this flaw allows for immediate root-level compromise.

### **3. Traffic Sniffing (Wireshark Evidence)**
* **Interface:** `eth0` (Host-Only Network)
* **Capture Filter:** `tcp.port == 21`
* **Technical Finding:** Observed plaintext FTP transmission during active login session.
* **Captured Data Strings:**
    * `USER: msfadmin`
    * `PASS: msfadmin`
* **Security Assessment:** Demonstrated that legacy protocols (FTP, Telnet) lack TLS/SSL encryption, making credentials vulnerable to interception on the local network.

### **4. Defensive Configuration (iptables)**
* **Objective:** Implement host-based packet filtering to mitigate the identified FTP attack vector.
* **Rule Applied:** `sudo iptables -A OUTPUT -p tcp --dport 21 -j DROP`
* **Validation Process:**
    1. Attempted manual FTP connection to `192.168.56.102`.
    2. Result: `Connection Timeout`.
    3. Nmap scan status: Changed from `Open` to `Filtered`.

### **5. Post-Action Summary**
* **System State:** Target remains vulnerable but external access is restricted via tactical firewall policy.
* **Next Steps:** Remediation via system patching and transitioning to encrypted protocols (SFTP/SSH).

---
*ApexPlanet Cybersecurity Internship - Documenting Professional Standards.*
