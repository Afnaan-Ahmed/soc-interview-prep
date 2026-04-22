# 🎯 Scenario-Based SOC Interview Questions

These scenarios test your ability to apply knowledge in real-world situations. Each has a structured, step-by-step answer.

---

## Scenario 1: Potential DDoS Attack

**You receive an alert indicating unusual traffic toward a web server that looks like a DDoS attack. What steps do you take?**

**Step 1 — Verify the alert**
Check if the traffic pattern is legitimate or anomalous using tools like Wireshark or netstat to inspect traffic flow.

**Step 2 — Identify the source**
Determine if traffic originates from a few IPs (simpler attack) or globally distributed (botnet-based DDoS).

**Step 3 — Mitigate**
Implement rate limiting, block malicious IPs, and engage cloud-based DDoS protection (Cloudflare, AWS Shield).

**Step 4 — Monitor**
Continue monitoring after mitigations to confirm the attack is neutralized.

**Step 5 — Document**
Write an incident report with findings, actions taken, and impact.

**Follow-up: How do you prioritize this if multiple high-priority alerts arrive simultaneously?**
Assess potential business impact. A DDoS is serious but may be contained quickly. A confirmed data breach or active exfiltration would take higher priority. Delegate and run parallel response tracks with the team.

---

## Scenario 2: Malware Infection on an Endpoint

**During a routine scan, you notice a potential malware infection on an endpoint. You have not confirmed if it's a false positive. How do you proceed?**

**Step 1 — Isolate**
Immediately disconnect the endpoint from the network to prevent potential spread.

**Step 2 — Analyze**
Use EDR tools (CrowdStrike, Carbon Black) to check for IOCs and unusual behavior.

**Step 3 — Check for compromise signs**
Examine system logs, running processes, network connections, and recently created files.

**Step 4 — Confirm or rule out**
If malware is confirmed, remove it and restore from a clean backup.

**Step 5 — Escalate if needed**
If the malware is part of a larger campaign or indicates a broader breach, escalate to Tier 2/IR team.

---

## Scenario 3: Zero-Day Vulnerability in Production Software

**You receive a threat intelligence feed reporting a zero-day in software widely used by your company. How do you respond?**

**Step 1 — Verify**
Cross-check against CVE databases, vendor advisories, and trusted security sources.

**Step 2 — Prioritize patching**
Work with IT to apply the vendor patch or workaround to affected systems immediately.

**Step 3 — Monitor for exploitation**
Update IDS/IPS and SIEM rules to detect exploitation attempts targeting the specific vulnerability.

**Step 4 — Apply compensating controls**
If patching can't happen immediately: firewall rules, network segmentation, disable the vulnerable feature.

**Step 5 — Communicate**
Notify relevant departments and management about the threat, mitigation steps, and timeline.

---

## Scenario 4: Suspicious Login from Unusual IP

**A user's account shows multiple failed logins followed by a successful login from an unusual IP. What logs do you analyze?**

**Step 1 — Review authentication logs**
Check login timestamps, source IPs, and failure/success patterns in AD/LDAP or SIEM.

**Step 2 — Investigate the IP**
Geolocate the IP, check its reputation on VirusTotal/AbuseIPDB, look for TOR/VPN indicators.

**Step 3 — Check for lateral movement**
Look for subsequent access to sensitive files, privilege escalation, or unusual account changes.

**Step 4 — Examine endpoint logs**
Check the device the user logged in from for signs of malware or credential theft.

**Step 5 — Contain**
Lock the account, force a password reset, and implement MFA.

---

## Scenario 5: Phishing Email Reported by Employee

**A user reports a phishing email containing a malicious link. How do you investigate?**

**Step 1 — Collect evidence**
Obtain the email including headers, URLs, and any attachments.

**Step 2 — Analyze the link**
Check the URL in a sandboxed environment (VirusTotal, URLScan.io) to confirm it's malicious.

**Step 3 — Block the URL**
Work with the network team to block the domain/URL across web filters and firewalls.

**Step 4 — Check for victims**
Search proxy/email logs to see if any other users clicked the link or received the same email.

**Step 5 — Notify and train**
Send a security awareness alert to the organization and schedule phishing awareness training.

---

## Scenario 6: Forensic Evidence from a Compromised Server

**A suspicious activity alert triggers on a server. You suspect a larger breach. How do you preserve evidence?**

**Step 1 — Isolate**
Disconnect the server from the network to stop further compromise.

**Step 2 — Capture volatile data**
Image RAM before powering off. Use a write blocker for disk imaging.

**Step 3 — Document everything**
Record every action taken, with timestamps, to maintain chain of custody.

**Step 4 — Hash all images**
Compute and record MD5/SHA-256 hashes of all acquired images.

**Step 5 — Analyze**
Once secured, analyze the forensic image to identify the breach scope and attacker actions.

---

## Scenario 7: High Volume of Alerts — Managing SOC Workflow

**Multiple alerts are flooding the system and it's difficult to distinguish real threats from false positives. How do you prioritize?**

**Step 1 — Triage by severity**
Categorize alerts by potential business impact and asset criticality.

**Step 2 — Automate**
Use SOAR playbooks to filter out low-confidence false positives automatically.

**Step 3 — Assign by expertise**
Route complex alerts to senior analysts; have junior analysts handle well-understood, lower-severity alerts.

**Step 4 — Focus on high-priority**
Ensure the most critical incidents receive dedicated attention while others are queued.

**Step 5 — Review and improve**
After the surge, review alert tuning opportunities and update detection rules.

---

## Scenario 8: Ransomware Attack

**Your company is hit with ransomware encrypting critical data on several servers. How do you handle this?**

**Step 1 — Isolate affected systems**
Disconnect all infected systems immediately to prevent further encryption spread.

**Step 2 — Identify the ransomware**
Analyze the ransom note and file extensions using tools like ID Ransomware.

**Step 3 — Restore from backup**
Begin restoring affected systems from the latest clean backups.

**Step 4 — Notify stakeholders**
Inform management, legal, compliance, and potentially affected customers.

**Step 5 — Investigate the attack vector**
Determine how ransomware entered (phishing, exposed RDP, vulnerable software) and patch it.

**Step 6 — Forensic analysis and reporting**
Collect and preserve evidence. Document the full timeline and response for legal and regulatory purposes.

---

## Scenario 9: Insider Threat — Employee Accessing Files Off-Hours

**SIEM alerts that an employee accessed sensitive files during off-hours without a clear reason. How do you investigate?**

**Step 1 — Verify the alert**
Confirm accuracy in SIEM logs. Check which files were accessed and whether it matches normal patterns.

**Step 2 — Review user activity**
Examine login history, devices, IPs, and behavior across the day/week.

**Step 3 — HR involvement**
If activity is unexplained, involve HR. Do not confront the employee directly without proper governance.

**Step 4 — Assess intent**
Determine if access was benign (legitimate work reason) or suspicious (bulk downloads, unusual destinations).

**Step 5 — Mitigate and document**
If malicious: revoke access, escalate to management, document for compliance.

---

## Scenario 10: Malware Using Novel Evasion Techniques

**A piece of malware is detected using an unknown evasion method. How do you analyze it?**

**Step 1 — Contain**
Isolate the affected system immediately.

**Step 2 — Reverse engineer**
Use IDA Pro or Ghidra to disassemble and understand the malware's behavior and evasion logic.

**Step 3 — Extract IOCs**
Identify file hashes, C2 domains/IPs, mutex names, registry keys.

**Step 4 — Apply mitigations**
Update endpoint detection rules, block IOCs at the firewall/proxy, deploy updated YARA rules.

**Step 5 — Report and share**
Document findings, update threat intelligence feeds, and share with the team and possibly the broader community.

---

## Scenario 11: Multiple Simultaneous Incidents

**Your SOC receives alerts for a DDoS, a phishing attempt, and a system compromise simultaneously. How do you prioritize?**

**Priority order:**
1. **System compromise** — highest priority if active exfiltration or lateral movement is occurring
2. **DDoS** — route to network team for mitigation while IR focuses on compromise
3. **Phishing** — investigate for credential theft; may elevate in priority if credentials were captured

**Key actions:**
- Isolate the compromised system immediately
- Engage network team for DDoS mitigation in parallel
- Check if the phishing led to the compromise (they may be related)
- Keep communication open with all relevant teams
- Document each incident independently
