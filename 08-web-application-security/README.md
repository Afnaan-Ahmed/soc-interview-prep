# 🌐 Web Application Security

---

## Q&A

### What are HTTP response codes?

| Range | Meaning |
|-------|---------|
| 1xx | Informational |
| 2xx | Success (200 OK, 201 Created) |
| 3xx | Redirection |
| 4xx | Client-side error (404 Not Found, 403 Forbidden, 401 Unauthorized) |
| 5xx | Server-side error (500 Internal Server Error) |

---

### What is the OWASP Top 10?

The OWASP Top 10 is a standard awareness document listing the most critical security risks to web applications. Current top risks include:

1. Broken Access Control
2. Cryptographic Failures
3. Injection (SQL, LDAP, OS)
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable and Outdated Components
7. Identification and Authentication Failures
8. Software and Data Integrity Failures
9. Security Logging and Monitoring Failures
10. Server-Side Request Forgery (SSRF)

---

### What is SQL Injection (SQLi)?

SQL Injection occurs when a web application includes unsanitized user input directly in SQL queries, allowing attackers to manipulate the database.

**Types:**
- **In-band (Classic):** Query and result use the same channel. Easiest to exploit.
- **Blind/Inferential:** No visible result; attacker infers data from application behavior.
- **Out-of-band:** Results returned through a different channel (e.g., DNS, HTTP request).

**Prevention:**
- Use **prepared statements / parameterized queries**
- Validate and sanitize all user input
- Implement a **Web Application Firewall (WAF)**
- Apply least privilege to database accounts

---

### What is XSS (Cross-Site Scripting)?

XSS occurs when an attacker injects malicious scripts into web pages viewed by other users. The scripts execute in the victim's browser.

**Types:**
- **Reflected (Non-Persistent):** Payload is in the URL or request; reflected back to the user immediately.
- **Stored (Persistent):** Payload is stored in the database and served to all users who view the page. Most dangerous.
- **DOM-Based:** Payload manipulates the DOM client-side without going to the server.

**Prevention:**
- Validate and sanitize all user input
- Encode output (HTML entity encoding)
- Use Content Security Policy (CSP) headers
- Use a WAF

---

### What is IDOR (Insecure Direct Object Reference)?

IDOR is a vulnerability where an application exposes internal object references (IDs, filenames) directly to users without proper authorization checks. An attacker can manipulate these references to access other users' data.

Example: Changing `/user/profile?id=123` to `/user/profile?id=124` to view another user's profile.

IDOR is ranked #1 in OWASP 2021 as "Broken Access Control."

---

### What is CSRF (Cross-Site Request Forgery)?

CSRF tricks an authenticated user into unknowingly submitting a malicious request to a web application. The attacker crafts a request (via link, image, or form) that the victim's browser sends with their credentials.

**Prevention:**
- Use CSRF tokens (unique, unpredictable values per session)
- Check `Origin` and `Referer` headers
- Use `SameSite` cookie attribute

---

### What is the difference between LFI and RFI?

- **LFI (Local File Inclusion):** A vulnerability where the application includes files from the local server based on user-supplied input without validation. Attackers can read sensitive files like `/etc/passwd`.
- **RFI (Remote File Inclusion):** The application includes files from a **remote** server, allowing attackers to execute their own code.

LFI is limited to the local filesystem; RFI allows remote code execution.

---

### What is a WAF (Web Application Firewall)?

A WAF filters and monitors HTTP traffic between a web application and the internet. It protects against:
- SQL injection
- XSS
- CSRF
- File inclusion attacks
- DDoS at the application layer

A WAF operates at OSI Layer 7 and is not designed to block all attack types — it complements, not replaces, secure coding practices.

---

### What is a DDoS attack and how would you mitigate it?

A Distributed Denial of Service (DDoS) attack floods a target with traffic from many sources, causing it to become unavailable to legitimate users.

**Types:**
- **Volumetric:** Overwhelm bandwidth (UDP floods)
- **Protocol:** Exhaust server resources (SYN floods)
- **Application layer:** Target specific services (HTTP floods)

**Mitigation:**
- Deploy rate-limiting and traffic filtering
- Use CDNs (Cloudflare, Akamai, AWS Shield)
- Work with your ISP to blackhole malicious traffic
- Implement anti-DDoS appliances or services

---

### What is your approach to identifying and mitigating a SQL injection attack?

1. Review logs for unusual SQL patterns (SELECT, UNION, OR 1=1, etc.)
2. Check for application error messages leaking database info
3. Block malicious requests with a WAF
4. Apply input validation and parameterized queries in the code
5. Notify the development team for permanent remediation
