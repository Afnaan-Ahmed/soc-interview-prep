# 🔐 Cryptography

---

## Q&A

### What is cryptography?

Cryptography is the practice of securing information by transforming it into an unreadable format, ensuring that only authorized parties can access it.

---

### What are encoding, hashing, and encryption?

| Concept | Purpose | Reversible? |
|---------|---------|-------------|
| **Encoding** | Converts data into a different format for compatibility (e.g., Base64) | Yes (not for security) |
| **Hashing** | Produces a fixed-size digest to verify integrity | No (one-way) |
| **Encryption** | Protects data confidentiality with a key | Yes (with key) |

---

### What is the difference between symmetric and asymmetric encryption?

| Feature | Symmetric | Asymmetric |
|---------|-----------|------------|
| Keys | Same key for encryption and decryption | Public key encrypts; private key decrypts |
| Speed | Fast | Slower (computationally intensive) |
| Use case | Bulk data encryption | Key exchange, digital signatures, TLS handshake |
| Algorithms | AES, DES, 3DES, RC4 | RSA, ECC, Diffie-Hellman |

---

### What is hashing and how does it differ from encryption?

**Hashing** converts input data into a fixed-length digest using a hash function (e.g., MD5, SHA-256). It is a **one-way function** — the original data cannot be recovered from the hash.

**Encryption** is **two-way** — data can be decrypted back to plaintext with the correct key.

**Hashing is used for:** Password storage, file integrity verification, digital signatures.
**Encryption is used for:** Protecting data in transit and at rest.

---

### What are salted hashes?

A **salt** is a random value added to a password before hashing. This:
- Ensures two users with the same password produce different hashes
- Defends against rainbow table attacks and precomputed hash attacks
- Increases complexity without requiring users to choose longer passwords

Example: `hash(password + salt)` → unique hash per user even for identical passwords.

---

### What is SSL/TLS?

- **SSL (Secure Sockets Layer):** Legacy protocol for encrypting web traffic. Now considered insecure and deprecated.
- **TLS (Transport Layer Security):** The modern, secure successor to SSL. Provides:
  - **Encryption** of data in transit
  - **Authentication** via certificates
  - **Integrity** using MACs

TLS is what HTTPS uses today. When people say "SSL certificate," they typically mean a TLS certificate.

---

### What is the difference between data protection in transit vs at rest?

| Type | Description | Methods |
|------|-------------|---------|
| **In transit** | Data being transmitted over a network | TLS/HTTPS, VPN, SSH |
| **At rest** | Data stored on a disk or database | AES encryption, BitLocker, encrypted databases |

Both are required for a comprehensive data protection strategy.

---

### What is 2FA (Two-Factor Authentication)?

2FA adds a second layer of verification beyond a username and password. The second factor is something:
- **You know:** PIN, security question
- **You have:** OTP from authenticator app, hardware token, SMS
- **You are:** Biometric (fingerprint, face)

2FA significantly reduces the risk of account compromise even if credentials are stolen.

---

### What is a CIA Triad?

The CIA Triad is the foundational model for information security:

| Principle | Description |
|-----------|-------------|
| **Confidentiality** | Ensuring data is accessible only to authorized parties |
| **Integrity** | Ensuring data is accurate and unaltered |
| **Availability** | Ensuring data and systems are accessible when needed |
