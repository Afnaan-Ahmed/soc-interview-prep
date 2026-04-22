# 🚨 Incident Response

---

## Quick-Reference Questions (No Answers)

- Explain the incident response lifecycle.
- What are Indicators of Compromise (IoCs), and why are they important?
- What is the process for responding to a zero-day vulnerability?
- How do you measure SOC performance using metrics like MTTR or MTTD?
- What are the key components of a SOC?
- What is a SOC playbook?

---

## Q&A

### What is the role of a SOC?

A Security Operations Center (SOC) is responsible for monitoring, detecting, investigating, and responding to security threats in real time. It acts as the central hub for managing cybersecurity incidents, ensuring that the organization's digital assets are protected from cyberattacks.

**Core functions:**
- Continuous monitoring of security events
- Alert triage and incident investigation
- Threat hunting
- Vulnerability management
- Digital forensics and incident response
- Threat intelligence analysis

---

### What are the key components of a SOC?

- **People:** Analysts (Tier 1, 2, 3), incident responders, threat hunters, SOC managers
- **Processes:** SOPs, playbooks, escalation paths, communication protocols
- **Technology:** SIEM, EDR, IDS/IPS, firewalls, threat intelligence platforms, SOAR

---

### Explain the incident response lifecycle.

The standard IR lifecycle (NIST SP 800-61):

| Phase | Description |
|-------|-------------|
| **Preparation** | Build policies, tools, team capabilities, and playbooks |
| **Detection & Analysis** | Identify and validate the incident using logs and alerts |
| **Containment** | Isolate affected systems to prevent further spread |
| **Eradication** | Remove the root cause (malware, backdoor, compromised credentials) |
| **Recovery** | Restore systems to normal operation safely |
| **Post-Incident Activity** | Lessons learned, documentation, detection improvements |

---

### What is the role of a SOC Analyst Tier 1?

A Tier 1 SOC Analyst is the first line of defense. Responsibilities include:
- Monitoring alerts from the SIEM
- Performing initial triage
- Escalating verified incidents to Tier 2
- Creating and updating incident tickets
- Documenting daily activity

---

### What is incident triage, and what are the main steps?

Incident triage is the rapid assessment of security alerts to determine their priority and legitimacy.

Steps:
1. Identify the rule/alert source
2. Check associated log data (user, IP, file, time)
3. Assess context — is this normal behavior for this user/system?
4. Correlate with other logs and threat intel
5. Classify: false positive, true positive, or needs escalation
6. Escalate or close with documentation

---

### What are MTTR and MTTD?

| Metric | Full Name | Meaning |
|--------|-----------|---------|
| **MTTD** | Mean Time to Detect | Average time from incident start to detection |
| **MTTR** | Mean Time to Respond | Average time from detection to containment/resolution |

Both are key SOC performance metrics. Reducing them limits attacker dwell time and business impact.

---

### What is a SOC playbook?

A SOC playbook is a predefined set of steps guiding analysts in responding to a specific incident type (e.g., phishing, ransomware, data exfiltration). Playbooks ensure:
- Consistent and repeatable responses
- Faster resolution times
- Reduced risk of mistakes under pressure
- Compliance with policy and legal requirements

---

### What is the principle of least privilege (PoLP)?

PoLP ensures that users, applications, and systems have only the minimum access necessary to perform their tasks. This minimizes the attack surface and limits potential damage if an account or system is compromised.

---

### How do you prioritize alerts in a SOC?

Priority is based on:
- **Severity** of the threat
- **Criticality** of the affected asset
- **Context** — Is the IP/domain known malicious? Is this user admin-level?
- **Correlation** with other recent events
- **Potential business impact** (data exposure, service disruption)

---

### What is dwell time and why does it matter?

Dwell time is the duration between an initial compromise and its detection. The longer an attacker remains undetected, the more damage they can cause (data exfiltration, lateral movement, persistence). Reducing dwell time is a primary goal of effective threat detection.

---

### How do you respond to a suspected data breach?

1. Identify and contain affected systems.
2. Analyze logs and network traffic for anomalies.
3. Identify compromised data and attack vectors.
4. Preserve evidence for forensic investigation.
5. Notify stakeholders and legal/compliance teams.
6. Remediate the root cause.
7. Assess regulatory notification requirements (GDPR, HIPAA, etc.).

---

### What is zero trust architecture?

Zero trust assumes no implicit trust for any entity inside or outside the network. Every access request must be verified. Key principles:
- **Verify explicitly** — Always authenticate and authorize based on all available data
- **Use least privilege** — Limit access to only what is needed
- **Assume breach** — Minimize blast radius and segment access

---

### What are the key stages of the Cyber Kill Chain?

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command and Control (C2)
7. Actions on Objectives

---

### What is lateral movement and how can it be detected?

Lateral movement is the process of an attacker moving through a network after gaining initial access, seeking higher privileges or more valuable targets.

**Detection methods:**
- Monitor for unusual authentication attempts between hosts
- Alert on privilege escalation activity
- Track abnormal file-sharing traffic
- Review Windows Event IDs 4624 (logon), 4648 (explicit credential use), 4672 (special privileges)

---

### What is a golden ticket attack and how can it be detected?

A golden ticket attack uses a forged Kerberos ticket-granting ticket (TGT) created with the KRBTGT account hash, granting unlimited access to Active Directory resources.

**Detection:**
- Monitor for Kerberos tickets with abnormally long lifetimes
- Alert on use of accounts not associated with recent domain controller logins
- Use Windows Event IDs 4769 (Kerberos service ticket request) and 4768 (TGT request)

---

### What is lateral phishing?

Lateral phishing uses a compromised internal email account to send phishing emails to colleagues within the same organization. Because the sender is a trusted internal contact, these are highly effective.

**Prevention:** Email anomaly detection, MFA, behavioral analysis on email sending patterns.

---

### How do you handle a credential stuffing attack?

1. Monitor for repeated login attempts from the same IP across many accounts
2. Block malicious IPs and enable CAPTCHA
3. Require password resets for affected accounts
4. Enforce MFA across all accounts
5. Notify users and educate about password reuse risks
