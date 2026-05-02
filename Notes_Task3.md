# 📓 Task 3 Web Application Security Notes
**Project:** Network Security & Scanning (Days 13–24)  
**Status:** Completed & Verified  
**Intern:** Fatimah Adnan


---

## 1. SQL Injection (SQLi)
*   **The Mechanism:** Occurs when untrusted data is inserted into a database query. This allows an attacker to manipulate query logic to bypass authentication or extract sensitive data.
*   **Mitigation:** Use **Prepared Statements** (Parameterized Queries) to ensure input is treated as data, not code.

## 2. Cross-Site Scripting (XSS)
*   **Stored XSS:** Malicious scripts are permanently stored on the server (e.g., in a database via a comment field).
*   **Reflected XSS:** Scripts are "reflected" off the web app to the victim’s browser, typically via a crafted URL.
*   **Mitigation:** Implement **Output Encoding** and a strong **Content Security Policy (CSP)**.

## 3. Cross-Site Request Forgery (CSRF)
*   **The Mechanism:** Forcing an authenticated user to execute unwanted actions on a web application where they are currently logged in.
*   **Mitigation:** Use unique **Anti-CSRF Tokens** and set cookies to `SameSite=Strict`.

## 4. File Inclusion (LFI/RFI)
*   **Local File Inclusion (LFI):** Tricking the application into exposing sensitive local files (e.g., `/etc/passwd`).
*   **Remote File Inclusion (RFI):** Forcing the application to load and execute a script from a remote URL.
*   **Mitigation:** Disable `allow_url_include` and use an "Allow List" for file paths.

## 5. Brute Force
*   **The Mechanism:** An automated attack that attempts every possible combination of passwords or usernames until the correct one is found.
*   **Mitigation:** Implement **Account Lockout Policies**, **Rate Limiting**, and mandatory **Multi-Factor Authentication (MFA)**.

## 6. Command Injection
*   **The Mechanism:** An attacker executes arbitrary operating system (OS) commands on the server through a vulnerable application interface (e.g., a "Ping" tool that doesn't sanitize input).
*   **Mitigation:** Avoid calling OS commands directly. Use built-in language APIs or strictly validate input against a regex pattern.

---

## Professional Tooling & Analysis
*   **Burp Suite:** Used for Intercepting, Intruder (fuzzing), and Repeater (manual testing) functions.
*   **Security Headers:** Implementation of `X-Frame-Options` and `HSTS` to prevent clickjacking and force secure connections.
