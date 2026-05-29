# 🛠️ Penetration Testing Methodology & Scope

## 1. Technical Assessment Frameworks
To guarantee absolute regulatory alignment and industry-standard delivery, this penetration testing engagement directly incorporates the rulesets defined within:
* **OWASP Top 10 Application Security Framework:** Used directly to scan, test, and isolate application-layer flaws such as injection vectors, broken authentications, and cross-site scripts.
* **NIST SP 800-115 Technical Guide to Information Security Testing:** Applied to manage system scope definitions, sequence defensive validation audits, and govern safe data exploitation procedures.

## 2. Engagement Scope Boundary
All activities were conducted exclusively inside a strictly isolated, host-only laboratory testing segment.

| Target Parameter | Specific Scope Matrix Details |
| :--- | :--- |
| **Attacker Platform** | Kali Linux Infrastructure (IP: `192.168.56.101`) |
| **Target Host Segment** | Damn Vulnerable Web App / bWAPP Deployments (IP: `192.168.56.102`) |
| **Testing Constraints** | Zero production system impact. Denial of Service (DoS) modules explicitly restricted. |

## 3. Technical Testing Sequence Phases
* **Phase 1: Reconnaissance & Target Discovery:** Passive or active data harvesting sweeps using network scanning equipment to map exposed system services.
* **Phase 2: Vulnerability Analysis:** Comparing target service banners against known public exploit records to establish verified entry vectors.
* **Phase 3: Exploitation Run:** Attempting controlled structural system entries via safe code execution bugs to verify the true impact of vulnerabilities.
* **Phase 4: Post-Exploitation Metrics:** Reviewing internal permission layers, running process contexts, and data security controls to assess the depth of potential compromise.
