# 🔍 Threat Intelligence

---

## Quick-Reference Questions (No Answers)

- What is threat intelligence?
- How do you use threat feeds in a SOC environment?
- What is the MITRE ATT&CK framework?
- How would you analyze an IP flagged as malicious?
- What are the stages of a cyber kill chain?

---

## Q&A

### What is Cyber Threat Intelligence (CTI)?

Threat intelligence is the analysis of data using tools and techniques to generate actionable information about existing or emerging threats targeting an organization. It helps organizations:
- Make faster, more informed security decisions
- Shift from reactive to proactive defense
- Understand attacker tactics, techniques, and procedures (TTPs)

---

### What are the types of Threat Intelligence?

| Type | Description | Audience |
|------|-------------|----------|
| **Strategic** | High-level trends, risk landscape, geopolitical context | Executives, management |
| **Tactical** | TTPs, attacker methodologies | Security architects, red/blue teams |
| **Operational** | Details about specific planned attacks | Incident responders, SOC |
| **Technical** | IOCs (IPs, hashes, domains, URLs) | SOC analysts, SIEM rules |

---

### What is MITRE ATT&CK?

MITRE ATT&CK® is a globally accessible knowledge base of adversary tactics and techniques based on real-world observations. It organizes attacker behavior into:
- **Tactics:** The adversary's goal (e.g., Initial Access, Lateral Movement, Exfiltration)
- **Techniques:** How they achieve it (e.g., Phishing, Pass the Hash, DNS Tunneling)
- **Procedures:** Specific implementations observed in the wild

**SOC uses:**
- Map detected activity to known attack patterns
- Identify detection gaps
- Build and test detection rules
- Communicate threat context to stakeholders

---

### What is the Cyber Kill Chain?

Developed by Lockheed Martin, the Cyber Kill Chain® describes 7 stages of a cyberattack:

| Stage | Description |
|-------|-------------|
| 1. Reconnaissance | Attacker researches the target (OSINT, scanning) |
| 2. Weaponization | Creates malware or exploit payload |
| 3. Delivery | Delivers the payload (phishing, USB, watering hole) |
| 4. Exploitation | Exploits a vulnerability to execute the payload |
| 5. Installation | Establishes persistence (backdoor, rootkit) |
| 6. Command & Control (C2) | Establishes communication with the attacker |
| 7. Actions on Objectives | Achieves the goal (exfiltration, destruction, ransomware) |

**Value:** Understanding where in the kill chain an attack is allows defenders to disrupt it at the earliest possible stage.

---

### What are Indicators of Compromise (IOCs)?

IOCs are forensic artifacts that indicate a system may have been compromised or is under attack. They serve as digital fingerprints left by attackers.

| IOC Type | Example |
|----------|---------|
| IP Address | 185.220.101.4 (known C2) |
| File Hash | e99a18c428cb38d5f260853678922e03 (MD5) |
| Domain Name | evil-login[.]com |
| URL | http://malicious[.]site/payload.exe |
| Email Address | fakeadmin@spoofed-company.com |
| Registry Key | HKCU\Software\Microsoft\Windows\Run\bad.exe |
| Process Name | svhost.exe (misspelling of svchost.exe) |

---

### What are Indicators of Attack (IOAs)?

IOAs demonstrate the *intent* and *techniques* behind a cyberattack, focusing on behavior rather than artifacts. Unlike IOCs (which are reactive — evidence of past compromise), IOAs are proactive — they detect attack activity in progress.

Example: Detecting a process attempting to disable security tools is an IOA, even if no known malware hash is involved.

---

### What is TAXII?

TAXII (Trusted Automated eXchange of Intelligence Information) is a protocol that defines how cyber threat intelligence can be shared via services and message exchanges. It is commonly used alongside STIX (Structured Threat Information eXpression) for standardized CTI sharing.

---

### Name some Threat Intelligence Platforms (TIPs)

- IBM X-Force Exchange
- Cisco Talos
- OTX AlienVault
- MISP (Open Source)
- Anomali ThreatStream
- Recorded Future
- ThreatConnect

**Free tools for IOC lookups:**
- VirusTotal
- AbuseIPDB
- MalwareBazaar
- URLhaus

---

### How would you analyze an IP flagged as malicious?

1. **Reverse DNS lookup** — Identify what domain the IP resolves to
2. **WHOIS** — Check registration info, ASN, and ownership
3. **Geo-IP** — Determine geographic location
4. **Reputation check** — Query VirusTotal, AbuseIPDB, Cisco Talos
5. **Blocklist check** — Check Spamhaus, FireHOL, emerging threats lists
6. **SIEM correlation** — Review internal logs for any connections to/from this IP
7. **Threat intel context** — Has this IP been associated with known campaigns?

---

### What is threat hunting?

Threat hunting is a proactive, human-led process of searching for threats that have evaded automated detection. Unlike reactive alert monitoring, threat hunters:
- Form hypotheses based on threat intelligence
- Search for anomalies and behavioral patterns
- Use tools like EDR, SIEM, and network data
- Uncover hidden attackers that may have been present for weeks or months

---

### How is threat intelligence operationalized in a SOC?

- Integrate threat feeds into SIEM for automated IOC matching
- Update detection rules based on new TTPs from ATT&CK
- Enrich alerts with threat context during triage
- Use intelligence to prioritize vulnerability remediation
- Inform incident response plans and playbooks
- Share findings with the broader security community (ISACs)
