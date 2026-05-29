📂 Web Application Penetration Test & Incident Response Simulation
Enterprise Capstone Project Portfolio > Prepared by: Fatimah Adnan

Internship ID: APSPL2631283

Organization: ApexPlanet

📌 Project Overview
This directory contains the end-to-end documentation, architectural data flows, and proof-of-concept verification artifacts for my final security capstone assessment. This project bridges the gap between offensive vulnerability exploitation and defensive incident response monitoring.

🗺️ Architecture & Data Relations
Below is the ER Data Model mapping out how our penetration testing phases, identified vulnerabilities, log outputs, and incident remediation steps correlate across the project lifecycle.

📂 Project Structure & Deliverables

🔬 1. Technical Execution Logs
Detailed Lab Execution Notes: The core command sequence, live session buffers, and dynamic system runtime telemetry traces covering all 6 execution phases.

📝 2. Formal Documentation Matrices
Executive Summary: High-level risk assessment and business-impact summary designed for non-technical stakeholders.

Methodology & Scope: Technical framework boundaries utilizing OWASP Top 10 guidelines and NIST testing standards.

Findings & Mitigations: Granular threat matrices defining risk scores, vulnerability vectors, and explicit patching instructions.

Post-Incident Report: Defensive timeline mapping log tracking analysis alongside system eradication steps.

🔬 Core Testing Phases Evaluated
📡 Phase 1: Reconnaissance & Target Mapping
Network service detection utilizing database-backed engines (db_nmap).

Identification of unpatched application interfaces and legacy daemons on Target IP 192.168.56.102.

🔓 Phase 2: Controlled Vulnerability Exploitation
Execution of remote code execution pathways against vulnerable daemons (UnrealIRCd).

Interactive shell upgrades and administrative privilege context audits (whoami -> root).

🔑 Phase 3: Password & Credential Attacks
Automated online dictionary sprays using Hydra against secure shell tunnels.

Local shadow copy file extractions and offline cryptographic hash decryption via John the Ripper.

🎯 Phase 4: Social Engineering Phishing Simulation
Engineering mock authentication portals using the Social-Engineer Toolkit (SET).

Harvesting credential variable arrays through an active local proxy handler.

📊 Phase 5: Behavioral Binary Diagnostics
Static extraction of code element markers via system strings.

Dynamic runtime interception of low-level kernel system calls using strace tracking sequences.

🧱 Phase 6: Defensive Infrastructure Hardening
Building zero-trust host perimeter firewall profiles using the Uncomplicated Firewall (UFW).

Minimizing application attack boundaries by isolating, stopping, and masking unnecessary background services.

🎥 Project Showcase Presentation
Final Presentation Video: [Watch the 12-Minute Technical Walkthrough](https://www.linkedin.com/posts/fatimah-adnan-02118a325_cybersecurity-penetrationtesting-incidentresponse-ugcPost-7466178554167316480-P7lY/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFIS55kBJTMTk76BGqeXITeogXHimnPC0U8)

Hosted Report Link: [Access Documentation Portal](https://github.com/fatimahadnan230/ApexPlanet-Cyber-Internship/blob/main/capstone-project/ApexPlanet%20Capstone%20Report.pdf)
