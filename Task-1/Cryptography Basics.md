# **Symmetric Encryption**
- **Speed:** Fast (bulk data)
    
- **Key Problem:** Secure distribution (how to share the key?)
    
- **Algorithms:** AES-256, ChaCha20 (secure); 3DES (deprecated)
    
- **CIA Target:** **Confidentiality**
    
- **Attack:** Brute-force, key leakage
    
- **Use:** File encryption, VPNs, disk encryption (BitLocker)
    

---
# **Asymmetric Encryption**
- **Speed:** Slow (100-1000x slower) – used for small data
    
- **Key Problem:** Solved (public keys are shared openly)
    
- **Algorithms:** RSA, ECC, Diffie-Hellman (key exchange)
    
- **CIA Target:** **Confidentiality** + **Integrity/Non-repudiation** (signatures)
    
- **Attack:** Quantum computing, MITM (if public key not verified)
    
- **Use:** TLS handshake, SSH, email encryption (PGP)
    

---
# **Hashing**
|Algorithm|Bits|Status|
|---|---|---|
|MD5|128|❌ Broken (collisions) – avoid|
|SHA-1|160|❌ Broken – avoid|
|SHA-256|256|✅ Secure (standard)|
|SHA-512|512|✅ Secure (enterprise)|
# **SSL/TLS**
- **SSL:** Deprecated (vulnerable) – use **TLS 1.2 or 1.3**
    
- **Handshake (simplified):** ClientHello → ServerHello + Certificate + KeyExchange → ClientKeyExchange → Finished
    
- **CIA Target:** **Confidentiality** (encryption), **Integrity** (MAC), **Authentication** (certs)
    
- **Attack:** Downgrade attacks (force weak cipher), MITM, weak ciphers
    
- **Defense:** TLS 1.3, HSTS, disable weak ciphers, cert pinning
# **Digital Certificates**
- **Format:** X.509 standard
    
- **Contents:** Public key, issuer, validity period, digital signature
    
- **Issuer:** Certificate Authority (CA) – trusted third party
    
- **Chain:** Root CA → Intermediate CA → Server Certificate
    
- **CIA Target:** **Authentication** (identity verification) + **Integrity** (signed)
    
- **Attack:** MITM (if cert not validated), expired/revoked certs, CA compromise
    
- **Defense:** Validate certs, HSTS, monitor Certificate Transparency logs
    

---

# **OpenSSL Hands-On – Quick Commands**
|Task|Command|
|---|---|
|**Symmetric encrypt**|`openssl enc -aes-256-cbc -salt -in file.txt -out file.enc -pass pass:123`|
|**Symmetric decrypt**|`openssl enc -d -aes-256-cbc -in file.enc -out file.txt -pass pass:123`|
|**Generate RSA private key**|`openssl genrsa -out private.pem 2048`|
|**Extract public key**|`openssl rsa -in private.pem -pubout -out public.pem`|
|**Asymmetric encrypt** (small file)|`openssl rsautl -encrypt -inkey public.pem -pubin -in msg.txt -out msg.enc`|
|**Asymmetric decrypt**|`openssl rsautl -decrypt -inkey private.pem -in msg.enc -out msg.txt`|
|**SHA-256 hash**|`openssl dgst -sha256 file.txt`|
|**Digital signature**|`openssl dgst -sha256 -sign private.pem -out sig.bin file.txt`|
|**Verify signature**|`openssl dgst -sha256 -verify public.pem -signature sig.bin file.txt`|
|**View certificate**|`openssl x509 -in cert.pem -text -noout`|
|**Fetch & view Google's cert**|`openssl s_client -connect google.com:443 -showcerts < /dev/null \| openssl x509 -text -noout`|
