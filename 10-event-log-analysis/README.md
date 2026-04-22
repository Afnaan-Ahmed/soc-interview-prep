# 📋 Event Log Analysis

---

## Q&A

### Which event logs are available by default on Windows?

| Log | Description |
|-----|-------------|
| **Security** | Audit logs: logon events, privilege use, account management, object access |
| **System** | Windows system component events (driver failures, startup, shutdown) |
| **Application** | Events from installed applications and services |

Access via: `Windows Key + R` → `eventvwr.msc` → Windows Logs

---

### Key Windows Security Event IDs

| Event ID | Description |
|----------|-------------|
| **4624** | Successful logon |
| **4625** | Failed logon |
| **4648** | Logon using explicit credentials |
| **4672** | Special privileges assigned to new logon (admin-level) |
| **4768** | Kerberos TGT request |
| **4769** | Kerberos service ticket request |
| **4771** | Kerberos pre-authentication failed |
| **4776** | NTLM credential validation |
| **4732** | Member added to a security-enabled local group |
| **4720** | User account created |
| **4726** | User account deleted |
| **4688** | New process created |
| **7045** | New service installed |

---

### How do you detect a successful RDP connection?

Use **Event ID 4624** and filter for **Logon Type 10** (RemoteInteractive). This indicates an RDP logon.

Key fields to review:
- `Account Name` — who logged in
- `Source Network Address` — IP of the connecting client
- `Logon Type` — must be 10 for RDP

---

### How do you detect failed logons?

Use **Event ID 4625** (failed logon). Investigate:
- The source IP address
- The target account name
- The frequency and time pattern (many failures in short time = brute force)
- Logon Type (3 = network, 10 = RDP, 2 = interactive)

---

### Where are logs stored in Linux?

All major logs are located under `/var/log/`:

| File | Contents |
|------|----------|
| `/var/log/auth.log` | Authentication events (SSH, sudo, PAM) — Debian/Ubuntu |
| `/var/log/secure` | Authentication events — RHEL/CentOS |
| `/var/log/syslog` | General system messages |
| `/var/log/messages` | General system messages — RHEL/CentOS |
| `/var/log/kern.log` | Kernel messages |
| `/var/log/apache2/` | Apache web server logs |
| `/var/log/nginx/` | Nginx logs |

**Useful commands:**
```bash
tail -200 /var/log/auth.log           # Recent auth events
grep "Failed password" /var/log/auth.log   # Failed SSH logins
grep "Accepted" /var/log/auth.log          # Successful SSH logins
```

---

### How would you investigate unauthorized SSH access attempts on a Linux server?

1. Review `/var/log/auth.log` for failed and successful SSH attempts
2. Identify source IPs and check for patterns (many failures = brute force)
3. Check for changes to SSH configuration files (`/etc/ssh/sshd_config`)
4. Look for new authorized keys (`~/.ssh/authorized_keys`)
5. Review recently created or modified user accounts
6. Restrict access via firewall rules and implement MFA
7. Consider `fail2ban` to auto-block repeated failed attempts

---

### What is Sysmon and why is it useful?

Sysmon (System Monitor) is a Windows system service and device driver that provides detailed logging beyond standard Windows Event Logs. Key events:
- Process creation with full command line (Event ID 1)
- Network connections (Event ID 3)
- File creation time changes (Event ID 2)
- Registry changes (Event ID 13)
- DLL loading (Event ID 7)

Sysmon dramatically improves visibility for threat hunting and forensic investigations.
