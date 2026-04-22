# 🌐 Network Security

---

## Quick-Reference Questions (No Answers)

- What is the difference between a hub, switch, and router?
- Explain the OSI Model and its layers.
- What is TCP/IP? How is it different from OSI?
- What are the common ports for HTTP, HTTPS, FTP, and SSH?
- How does ARP work?
- What is a VLAN?
- Explain the difference between TCP and UDP.

---

## Q&A

### What is the OSI Model? Explain each layer.

The Open Systems Interconnection (OSI) model is a conceptual framework that describes how data communication functions across a network, independent of the underlying technology.

| Layer | Name | Responsibility |
|-------|------|----------------|
| 7 | Application | Interface between the application and the network (HTTP, FTP, DNS) |
| 6 | Presentation | Data formatting, encoding, encryption/decryption |
| 5 | Session | Establishes, manages, and terminates sessions between applications |
| 4 | Transport | End-to-end communication, segmentation, flow control (TCP/UDP) |
| 3 | Network | Packet forwarding and routing (IP, ICMP, ARP) |
| 2 | Data Link | Node-to-node data transfer, MAC addressing, error detection |
| 1 | Physical | Transmission of raw bits over a physical medium |

---

### What is the TCP/IP Model? How does it differ from OSI?

The TCP/IP model is the practical model used on the internet. It has **4 layers**:

1. Application Layer
2. Transport Layer
3. Internet Layer
4. Network Access Layer

**Difference:** OSI is a theoretical 7-layer model; TCP/IP is a practical 4-layer implementation. OSI separates Presentation and Session as distinct layers; TCP/IP merges them into the Application layer.

---

### What is a three-way handshake?

TCP uses a three-way handshake to establish a reliable connection:

1. **SYN** — Client sends a synchronize packet to the server to initiate a connection.
2. **SYN-ACK** — Server acknowledges and responds with its own SYN.
3. **ACK** — Client acknowledges the server's response, and the connection is established.

---

### What are the differences between TCP and UDP?

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (acknowledgments, retransmission) | Unreliable (no guarantee of delivery) |
| Speed | Slower | Faster |
| Use cases | HTTP, HTTPS, SSH, FTP | DNS, streaming, VoIP, gaming |

---

### What is the difference between a hub, switch, and router?

- **Hub:** Broadcasts data to all devices on the network. Operates at Layer 1 (Physical). No intelligence.
- **Switch:** Forwards data only to the intended device using MAC addresses. Operates at Layer 2 (Data Link).
- **Router:** Routes data between different networks using IP addresses. Operates at Layer 3 (Network).

---

### What are common ports used in networking?

| Port | Protocol/Service |
|------|-----------------|
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3389 | RDP |
| 445 | SMB |
| 21 | FTP |

---

### What is ARP and how does it work?

ARP (Address Resolution Protocol) maps an IP address to a physical MAC address on a local network.

When a device needs to communicate with another device on the same network, it broadcasts an ARP request asking "Who has IP x.x.x.x?" The device with that IP responds with its MAC address, which is then cached in the ARP table.

---

### What is DHCP?

DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses and other network parameters (subnet mask, gateway, DNS) to devices on a network using a client-server model.

---

### What is DNS and how can it be abused?

DNS (Domain Name System) translates human-readable domain names (e.g., google.com) into IP addresses.

**Abuse techniques:**
- **DNS Tunneling:** Encoding data inside DNS queries to exfiltrate data or establish C2 channels while bypassing firewalls.
- **C2 over DNS:** Malware receives commands via DNS responses, evading network controls.
- **DNS Spoofing/Poisoning:** Manipulating DNS responses to redirect traffic to malicious sites.
- **DNS Exfiltration:** Sending stolen data out through DNS queries, which are often not deeply inspected.

---

### What is a VLAN?

A VLAN (Virtual Local Area Network) logically segments a physical network into separate broadcast domains without requiring separate physical infrastructure. VLANs improve security and reduce congestion by isolating traffic between groups (e.g., separating guest Wi-Fi from corporate traffic).

---

### What is a DMZ in a network, and why is it used?

A DMZ (Demilitarized Zone) is a network segment that hosts public-facing services (web servers, mail servers) while isolating them from the internal network. It acts as a buffer zone — if a public-facing server is compromised, attackers don't gain direct access to internal systems.

---

### What is the difference between IDS and IPS?

| Feature | IDS (Intrusion Detection System) | IPS (Intrusion Prevention System) |
|---------|----------------------------------|-----------------------------------|
| Action | Monitors and alerts (passive) | Monitors and blocks (active) |
| Placement | Out-of-band | Inline with traffic |
| Response | Human review required | Automatic blocking |

---

### What is the difference between HIDS and NIDS?

- **HIDS (Host Intrusion Detection System):** Installed on individual hosts. Monitors local system activity, files, and logs.
- **NIDS (Network Intrusion Detection System):** Deployed on the network. Monitors traffic across all devices on the network.

---

### What is a proxy server and how is it used in cybersecurity?

A proxy server acts as an intermediary between clients and the internet. It provides anonymity, content filtering, and security by inspecting and controlling outbound traffic. SOC teams monitor proxy logs to detect malicious domains, data exfiltration, or access to blocked content.

---

### How can you protect yourself from Man-in-the-Middle (MITM) attacks?

- Use **VPN** to encrypt traffic.
- Enforce **HTTPS** with HSTS.
- Use **strong WPA2/WPA3** encryption on wireless networks.
- Deploy **certificate pinning** in applications.
- Monitor for ARP spoofing with **Intrusion Detection Systems**.

---

### What is port scanning, and how do SOC teams detect it?

Port scanning is a technique used to identify open ports and services on a host. Attackers use it to find potential entry points.

SOC detection methods:
- Firewall and IDS/IPS alerts for rapid sequential connection attempts
- Unusual traffic patterns in SIEM logs
- NetFlow analysis showing connections to many ports from a single source

---

### What is the role of NetFlow in network monitoring?

NetFlow provides metadata about network traffic — source/destination IPs, ports, protocol, and traffic volume — without capturing full packet contents. It helps analysts identify anomalies, detect data exfiltration, and understand traffic baselines.

---

### Why is time synchronization important in SOC operations?

Accurate time synchronization (via NTP) across all devices ensures that log timestamps are consistent. This is critical for:
- Correlating events across different systems
- Accurate forensic timelines
- Compliance with regulatory requirements
