#Project CYP

## Installation
https://github.com/abdelrahman-elyan/FinalProjectCYP
# Final Project: CYS Penetration Testing

## Executive Summary

### Purpose of the Test
- Learn to apply penetration testing techniques.
- Identify vulnerabilities in any website.

### Main Results
- Successfully logged in as an admin.
- Discovered the administration path.
- Found XSS and SQL injection vulnerabilities.
- Gained access to the database of products.
- Performed brute-force attacks to crack the admin password.

---

## Scope and Methodology

### Scope
- *OWASP Juice Shop* (localhost:3000).

### Approach
- Black Box Testing.

### Tools Used
- Burp Suite
- OWASP ZAP
- Dirb

---

## Vulnerability Findings

### 1. SQL Injection
#### Details:
- In the login page, use the following:
- admin' OR 1=1;--
- or:
admin' OR 'a'='a';--

#### Impact:
- These inputs grant admin access to the site.

#### Mitigation:
- Use input validation (e.g., regular expressions) to restrict user inputs.
- Implement prepared statements to treat user input as data, not executable code.
- Limit database privileges and use a Web Application Firewall (WAF).

---

### 2. Cross-Site Scripting (XSS)
#### Details:
- Inject the following in the search bar:
```html
<img src=x onerror=alert('TEST')>
or:
<a href="javascript:alert('TEST')">Click me</a>
Impact:
An alert box appears when the user interacts with the injected elements.
Mitigation:
Sanitize and validate inputs to block harmful content.
Implement Content Security Policy (CSP) to restrict allowed scripts.
3. Brute-Force Attack
Details:
Using Burp Suite, the admin password was cracked:
admin123

Details:
The administration path was found:
bash
Copy code
http://localhost:3000/#/administration
Impact:
Exposes user information, feedback, and account details.
Mitigation:
Restrict access to the administration path by verifying user permissions.
http://localhost:3000/#/administration
Impact:
Exposes user information, feedback, and account details.
Mitigation:
Restrict access to the administration path by verifying user permissions.
Attachments
Video:
Video Link
https://drive.google.com/file/d/1iSQ18C1d2K-XKCXWQltghn0LbSvD6MKo/view?usp=drivesdk
GitHub Repository:
Repository Link



