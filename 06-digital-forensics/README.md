# 🔬 Digital Forensics

---

## Quick-Reference Questions (No Answers)

- What tools are commonly used for digital forensics?
- Explain the steps in a digital forensic investigation.
- What is data acquisition in forensics?
- How do you ensure chain of custody for digital evidence?
- What is volatile vs non-volatile data?

---

## Q&A

### What is digital forensics?

Digital forensics is the process of collecting, preserving, analyzing, and presenting digital evidence from computers, networks, and storage devices. It is used to:
- Reconstruct past events during incident investigations
- Identify perpetrators and attack methods
- Support legal proceedings and regulatory compliance
- Understand the scope and impact of a breach

---

### What is the difference between volatile and non-volatile data?

| Type | Description | Examples |
|------|-------------|----------|
| **Volatile** | Data that is lost when the system is powered off | RAM, running processes, network connections, open files, clipboard |
| **Non-Volatile** | Data that persists after power loss | Hard drive data, registry, event logs, file system |

**Forensic priority:** Volatile data must be captured first as it disappears when the system shuts down.

---

### What are the steps in a digital forensic investigation?

1. **Identification** — Determine what evidence exists and where it is located
2. **Preservation** — Secure the scene; prevent alteration of evidence
3. **Collection** — Acquire forensic images using write blockers; capture volatile data
4. **Examination** — Extract relevant data from forensic images
5. **Analysis** — Interpret data to reconstruct events and identify findings
6. **Reporting** — Document findings in a clear, factual report
7. **Presentation** — Present evidence in legal or organizational proceedings

---

### What is chain of custody?

Chain of custody is the documented record of who collected, handled, transferred, and analyzed digital evidence at every stage. It ensures:
- Evidence integrity is maintained
- Evidence is admissible in legal proceedings
- Tampering or accidental modification can be detected or ruled out

Key documentation: Who collected it, when, where, how it was stored, and who had access.

---

### What is data acquisition in forensics?

Data acquisition is the process of creating an exact copy (forensic image) of digital media for analysis. Key principles:
- Use a **write blocker** to prevent any changes to the original media
- Verify integrity using hash values (MD5, SHA-256) before and after imaging
- Prefer **bit-level copies** over logical copies to capture deleted files and unallocated space

**Common tools:** FTK Imager, dd, Autopsy, Guymager

---

### What is memory forensics, and when is it used?

Memory forensics involves analyzing the contents of a system's RAM to uncover:
- Running malware (including fileless malware)
- Encryption keys
- Active network connections
- Credentials and tokens in memory
- Injected processes

It is used when disk-based analysis may miss threats that only exist in memory, or when a live system is suspected of compromise.

**Tools:** Volatility, Rekall

---

### What tools are commonly used for digital forensics?

| Tool | Use |
|------|-----|
| Autopsy / Sleuth Kit | Disk forensics, file system analysis |
| FTK (Forensic Toolkit) | Evidence processing, disk imaging |
| Volatility | Memory forensics |
| Wireshark | Network packet analysis |
| EnCase | Enterprise forensic investigation |
| KAPE | Triage and artifact collection |
| Sysinternals Suite | Windows live system analysis |
| Cellebrite | Mobile device forensics |

---

### What is the difference between live forensics and dead-box forensics?

- **Live Forensics (Live Response):** Performed on a running system. Captures volatile data (RAM, processes, connections). Risk of evidence being modified.
- **Dead-box Forensics:** Performed on a powered-off system or forensic image. Stable evidence, but volatile data is already lost.

---

### How do you preserve evidence from a compromised server?

1. **Do not power off** the system (volatile data will be lost).
2. Capture a memory image using a forensic tool (e.g., Volatility's winpmem).
3. Isolate the system from the network (pull network cable or firewall rule).
4. Take a forensic image of all storage drives using a write blocker.
5. Hash all images and document the process.
6. Maintain chain of custody throughout.

---

### What is a forensic hash and why is it important?

A forensic hash (MD5, SHA-1, SHA-256) is a unique digital fingerprint of a file or disk image. It:
- Verifies that evidence has not been altered since collection
- Proves integrity to legal or regulatory bodies
- Allows comparison of files against known malware databases

If the hash of the acquired image matches the original, the evidence is considered intact.
