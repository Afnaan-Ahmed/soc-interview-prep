# 💻 Endpoint Security

---

## Quick-Reference Questions (No Answers)

- What are the key features of EDR (Endpoint Detection and Response)?
- How would you investigate a malware infection on a user's machine?
- What is the role of antivirus and how does it detect threats?
- Explain the difference between signature-based and behavior-based detection.
- What steps would you take if a user reports ransomware on their endpoint?

---

## Q&A

### What is EDR (Endpoint Detection and Response), and how does it differ from traditional antivirus?

| Feature | EDR | Traditional Antivirus |
|---------|-----|-----------------------|
| Detection method | Behavioral + signature | Primarily signature-based |
| Visibility | Real-time process, file, network activity | File scanning |
| Response | Automated isolation, forensic data | Quarantine/delete |
| Threat coverage | Known + unknown threats | Primarily known threats |
| Examples | CrowdStrike, Carbon Black, SentinelOne | Norton, McAfee, Avast |

---

### What is the role of an antivirus solution in a SOC?

Antivirus solutions detect, quarantine, and remove known malware on endpoints. In a SOC context, they generate alerts and logs that feed into the SIEM, assist in incident investigation, and provide a baseline layer of defense for known threats.

---

### What is the difference between signature-based and behavior-based detection?

- **Signature-Based:** Detects threats by comparing files or traffic against a database of known malware signatures. Fast and accurate for known threats, but blind to novel or zero-day attacks.
- **Behavior-Based:** Identifies threats by monitoring actions (e.g., process injection, registry modification) and flagging deviations from normal behavior. Effective against unknown threats but can produce more false positives.

---

### What are common types of malware?

| Type | Description |
|------|-------------|
| Virus | Attaches to legitimate files and spreads when executed |
| Worm | Self-replicates across networks without user interaction |
| Ransomware | Encrypts files and demands payment for decryption |
| Trojan | Disguises itself as legitimate software |
| Spyware | Silently collects user data (keystrokes, credentials) |
| Rootkit | Hides its presence in the OS to maintain persistent access |
| Fileless malware | Resides in memory; uses legitimate tools like PowerShell |
| Botnet | Network of compromised devices controlled by an attacker |

---

### How would you respond to a ransomware attack?

1. **Isolate** infected systems immediately to prevent spread.
2. **Identify** the ransomware variant (file extensions, ransom note, ID Ransomware tool).
3. **Restore** from the latest clean backups if available.
4. **Notify** stakeholders, management, and legal/compliance teams.
5. **Investigate** the attack vector (phishing, exploit, credential theft).
6. **Patch** vulnerabilities and harden defenses.
7. **Document** findings and conduct post-incident analysis.

---

### How do you detect and mitigate fileless malware?

Fileless malware resides in memory and abuses legitimate tools (PowerShell, WMI, LOLBins) to avoid disk-based detection.

**Detection:**
- Monitor for anomalous PowerShell execution (e.g., encoded commands, `Invoke-WebRequest`)
- Use Sysmon to log process creation, network connections, and registry changes
- Analyze memory dumps
- Review EDR telemetry for unusual parent-child process relationships

**Mitigation:**
- Enable PowerShell Constrained Language Mode
- Use application whitelisting
- Enable Script Block Logging and Module Logging for PowerShell

---

### How do you differentiate between legitimate and malicious PowerShell scripts?

Red flags for malicious PowerShell:
- **Obfuscation:** Base64-encoded commands (`-EncodedCommand`), string concatenation, `[char]` casting
- **Download cradles:** `Invoke-WebRequest`, `IEX (New-Object Net.WebClient).DownloadString()`
- **Execution policy bypass:** `-ExecutionPolicy Bypass`
- **Unusual parent process:** PowerShell spawned by Word, Excel, or a browser
- **Outbound connections:** Unexpected network activity to unknown IPs/domains

---

### What is DNS sinkholing in cybersecurity?

DNS sinkholing redirects DNS queries for known malicious domains to a controlled server instead of the real malicious destination. This:
- Prevents infected endpoints from reaching C2 servers
- Identifies infected machines (they'll show up in sinkhole logs)
- Aids in malware analysis

---

### What steps would you take to respond to a malware outbreak in the network?

1. Isolate affected systems from the network.
2. Identify the malware using sandbox analysis and threat intelligence.
3. Deploy EDR tools to identify all infected endpoints.
4. Contain the outbreak by blocking associated IOCs (hashes, IPs, domains) at firewalls and proxies.
5. Apply patches and update antivirus signatures.
6. Restore clean systems from backups.
7. Conduct post-incident review and implement preventive controls.

---

### What are common BYOD (Bring Your Own Device) security risks?

- Unauthorized access to corporate resources
- Data leakage from unmanaged devices
- Malware infection spreading from personal devices to corporate network
- Lack of visibility and control over device security posture
- Loss or theft of device containing corporate data

**Mitigations:** MDM (Mobile Device Management), network segmentation, VPN with MFA, DLP policies.

---

### What are some general endpoint security product categories?

- **Antivirus (AV):** Signature-based malware detection
- **EDR (Endpoint Detection & Response):** Real-time behavioral monitoring and response
- **XDR (Extended Detection & Response):** Extends EDR across network, cloud, and email
- **DLP (Data Loss Prevention):** Prevents unauthorized data transfers
