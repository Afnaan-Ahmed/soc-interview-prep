# 📊 SIEM (Security Information and Event Management)

---

## Quick-Reference Questions (No Answers)

- What is a SIEM?
- How does a SIEM help in threat detection?
- Explain correlation rules in a SIEM.
- What are false positives and how do you handle them in a SIEM?
- How would you investigate a failed login attempt in a SIEM?
- Explain the difference between an event and an incident.

---

## Q&A

### What is a SIEM?

A SIEM (Security Information and Event Management) is a platform that:
- **Collects and normalizes** logs and events from across an organization's IT environment
- **Correlates** events to identify patterns indicative of threats
- **Generates alerts** for suspicious activity
- **Provides dashboards and reports** for compliance and visibility

Examples: Splunk, IBM QRadar, Microsoft Sentinel, Wazuh, Elastic SIEM.

---

### What types of logs does a SIEM collect?

- Windows Event Logs
- Linux Syslogs
- Firewall and IDS/IPS logs
- Antivirus and EDR alerts
- VPN and proxy logs
- Authentication logs (SSH, RDP, Active Directory)
- Cloud service logs (AWS CloudTrail, Azure Activity Logs)
- Application and web server logs

---

### What is a SIEM use case, and how do you create one?

A SIEM use case is a predefined detection rule or scenario targeting a specific threat behavior.

**How to create one:**
1. Define the objective (e.g., detect brute-force login attempts)
2. Identify the relevant log sources
3. Specify the conditions and thresholds (e.g., >5 failed logins in 60 seconds)
4. Define the alert action and severity
5. Test the rule against real and simulated data
6. Document and tune over time

---

### What are correlation rules in a SIEM?

Correlation rules combine multiple events or log entries from different sources to identify patterns that suggest a security incident. For example:
- A single failed login is an event
- 50 failed logins followed by a successful login from the same IP within 5 minutes triggers a brute-force correlation rule

---

### What is the difference between an event and an incident?

- **Event:** Any observable action or log entry in the environment (normal or abnormal). Example: a user login.
- **Alert:** An event that matches a suspicious pattern and is flagged for review.
- **Incident:** A confirmed security event that requires a response. Example: a confirmed account compromise.

---

### What are false positives and false negatives?

| Term | Definition | Example |
|------|------------|---------|
| **False Positive** | A benign activity flagged as malicious | A security scanner triggering an IDS rule |
| **False Negative** | A malicious activity that goes undetected | Malware that evades detection |
| **True Positive** | A genuine threat correctly detected | Ransomware triggering an alert |
| **True Negative** | Benign activity correctly not flagged | Normal web traffic passing through |

**Handling false positives:**
- Investigate to confirm the classification
- Tune detection rules or adjust thresholds
- Add exceptions or whitelists for known-good behavior
- Document findings to improve future accuracy

---

### What is log normalization in a SIEM?

Log normalization standardizes log data from various sources into a consistent format, making it easier to correlate events across different systems (e.g., normalizing Windows and Linux auth logs into a common schema with consistent field names).

---

### What is log aggregation, and why is it important?

Log aggregation collects and centralizes logs from multiple systems into a single platform. This is critical for:
- **Correlation:** Connecting events across systems for threat detection
- **Efficiency:** Analysts work from one interface instead of many
- **Retention:** Centralized storage for compliance and forensic investigations

---

### What is the role of a correlation engine in a SIEM?

The correlation engine processes incoming events and applies rules to identify relationships between them. It looks for patterns — such as an IP scanning multiple hosts, or multiple failed logins from different accounts — that indicate complex threats that no single event would reveal alone.

---

### What is risk-based alerting in a SOC?

Risk-based alerting prioritizes alerts based on the potential impact and likelihood of an incident, considering factors like:
- The criticality of the affected asset
- The severity of the behavior detected
- Contextual threat intelligence (is this IP/domain known malicious?)
- Historical patterns (has this user done this before?)

This reduces alert fatigue by ensuring analysts focus on what matters most.

---

### How do you handle a situation where the SIEM generates too many alerts?

1. **Tune rules:** Adjust thresholds and conditions to reduce noise for known-good behavior.
2. **Correlate alerts:** Group related alerts to reduce volume and provide context.
3. **Prioritize:** Implement a tiered alerting system based on severity and asset criticality.
4. **Whitelist:** Add exceptions for legitimate, recurring activities (e.g., scheduled jobs).
5. **Review use cases:** Retire or update low-value detection rules regularly.

---

### What is SOAR and what role does it play in a SOC?

SOAR (Security Orchestration, Automation, and Response) platforms:
- **Integrate** disparate security tools into unified workflows
- **Automate** repetitive tasks like alert triage, IOC lookups, and ticket creation
- **Orchestrate** multi-step response actions across tools
- **Provide playbooks** for consistent incident handling

Examples: Splunk SOAR (Phantom), Palo Alto Cortex XSOAR, IBM SOAR.

**Benefit:** Reduces analyst workload on routine tasks, allowing focus on complex investigations.

---

### What is a log retention policy, and why is it critical?

A log retention policy specifies how long logs are stored. It is critical for:
- **Compliance:** Regulations like GDPR, HIPAA, and PCI-DSS mandate minimum retention periods
- **Investigations:** Historical logs are needed to reconstruct past incidents
- **Threat hunting:** Long-term patterns require access to historical data

---

### How does a SIEM help with compliance requirements?

SIEM systems support compliance by:
- Centralizing log collection required by auditors
- Generating out-of-the-box compliance reports for GDPR, HIPAA, PCI-DSS, SOX
- Alerting on policy violations (e.g., access to sensitive data outside business hours)
- Maintaining audit trails of who accessed what and when
