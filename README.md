# Web Application Security Assessment & Mitigation Report

## Overview
This repository documents security analysis and remediation strategies for common web application vulnerabilities tested in a local environment (DVWA / Apache).

---

## Vulnerabilities & Mitigations

### 1. SQL Injection (SQLi)
* **Scenario:** Dynamic database queries executed without proper parameterization.
* **Mitigation:** Use prepared statements and parameterized queries (PDO or Mysqli) to separate data from code.

### 2. Cross-Site Scripting (XSS)
* **Scenario:** Unsanitized user inputs reflected or stored in application pages.
* **Mitigation:** Context-aware output encoding (e.g., `htmlspecialchars()`) and implementing a strict Content Security Policy (CSP).

### 3. Cross-Site Request Forgery (CSRF)
* **Scenario:** Unauthorized state-changing commands executed on behalf of an authenticated user.
* **Mitigation:** Implement unique, cryptographically secure anti-CSRF tokens for form submissions and use `SameSite=Strict` cookies.

### 4. Local File Inclusion (LFI)
* **Scenario:** Unvalidated user input supplied to file inclusion path functions.
* **Mitigation:** Strict whitelisting of allowed files and path sanitization using `basename()`.

---

## Server Hardening (HTTP Security Headers)
Configured defensive security headers in Apache (`/etc/apache2/conf-available/security.conf`):
* `X-Frame-Options: SAMEORIGIN`
* `X-Content-Type-Options: nosniff`
* `Content-Security-Policy: default-src 'self';`
* `X-XSS-Protection: 1; mode=block`
* `Referrer-Policy: strict-origin-when-cross-origin`
