# **OSI Model (7 Layers)**
|#|Layer|Function|Example Protocols|Security Relevance|
|---|---|---|---|---|
|7|**Application**|User-facing services|HTTP, DNS, SMTP|Where **Phishing**, **Malware** payloads enter|
|6|**Presentation**|Data formatting, encryption, compression|SSL/TLS, JPEG, ASCII|**Confidentiality** via encryption; **Integrity** via hashing|
|5|**Session**|Establishes/manages connections|NetBIOS, RPC|Session hijacking, **Insider Threats** via reused tokens|
|4|**Transport**|End-to-end communication, segmentation|TCP, UDP|Port scanning (**Recon**), **DDoS** (SYN flood)|
|3|**Network**|Routing & logical addressing|IP, ICMP, ARP|**Spoofing**, **DDoS** (IP spoofing), man-in-the-middle|
|2|**Data Link**|Physical addressing, error detection|Ethernet, MAC, PPP|MAC spoofing (**Wireless Attacks**), switch flooding|
|1|**Physical**|Raw bit transmission over hardware|Cables, radio, fiber|Physical tapping, signal jamming (**Availability**)|
# **TCP/IP Protocol Suite**
|TCP/IP Layer|OSI Equivalent|Key Protocols|Security Focus|
|---|---|---|---|
|**Application**|Layers 5-7|HTTP, HTTPS, DNS, FTP, SSH|Encrypt with TLS (HTTPS), validate DNS|
|**Transport**|Layer 4|TCP (reliable), UDP (fast)|TCP: handshake attacks; UDP: amplification **DDoS**|
|**Internet**|Layer 3|IP, ICMP, ARP|IP spoofing, ICMP tunneling, ARP poisoning|
|**Network Access**|Layers 1-2|Ethernet, Wi-Fi, PPP|MAC filtering, rogue AP detection|
# Dns
| Aspect                      | Detail                                                                 | Security Implication                                                           |
| --------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Function**                | Resolves `example.com` → `93.184.216.34`                               | **Availability** critical (if DNS fails, users can't find you)                 |
| **Port**                    | UDP 53 (default), TCP 53 (for large responses)                         | UDP makes it vulnerable to **DNS Amplification DDoS**                          |
| **Record Types**            | A (IPv4), AAAA (IPv6), CNAME (alias), MX (mail), TXT (SPF/DKIM)        | Wrong records = **Integrity** issues (email spoofing)                          |
| **Attack: Spoofing**        | Attacker answers DNS query with fake IP                                | Redirects to malicious site = **Phishing**, **Malware** delivery               |
| **Attack: Cache Poisoning** | Corrupts resolver's cache with fake records                            | Widespread redirection, breaks **Integrity**                                   |
| **Defense**                 | DNSSEC (cryptographic signing), DoH/DoT (encrypted DNS), rate limiting | Protects **Confidentiality** (hides queries) & **Integrity** (verifies answers |
# **HTTP vs. HTTPS**
| Feature                  | HTTP                                                  | HTTPS                                                  |
| ------------------------ | ----------------------------------------------------- | ------------------------------------------------------ |
| **Full Name**            | HyperText Transfer Protocol                           | HTTP + **Secure** (SSL/TLS)                            |
| **Port**                 | 80                                                    | 443                                                    |
| **Encryption**           | None (plaintext)                                      | End-to-end encryption (TLS)                            |
| **CIA Impact**           | **Confidentiality** violated (eavesdropping)          | **Confidentiality** & **Integrity** preserved          |
| **Attack Vulnerable To** | Man-in-the-Middle, session hijacking, packet sniffing | Downgrade attacks (if TLS misconfigured), weak ciphers |
| **Verification**         | No server identity check                              | TLS certificate validates server = prevents spoofing   |
| **Key Defense**          | ⚠️ Deprecated for any sensitive data                  | Enforce HSTS (forces HTTPS), use TLS 1.3, valid certs  |
# **IP Addressing**
|Aspect|IPv4|IPv6|
|---|---|---|
|**Length**|32-bit (dotted decimal: `192.168.1.1`)|128-bit (hexadecimal: `2001:db8::1`)|
|**Classes (old)**|A-D (range-based), E (reserved)|No classes – uses CIDR exclusively|
|**Public IP**|Globally routable on the internet|Globally routable|
|**Private IP**|Reserved for internal use (not routed on internet)|`fc00::/7` (unique local)|
|**Security Relevance**|Private IPs = internal network, harder for external attackers to reach without NAT/port forwarding|Built-in IPsec support enhances **Confidentiality**/**Integrity**|

# Subnetting
|Concept|Explanation|Security Benefit|
|---|---|---|
|**CIDR Notation**|`192.168.1.0/24` = first 24 bits are network, last 8 are hosts (256 IPs)|Limits broadcast domains, reduces attack surface|
|**Subnet Mask**|`255.255.255.0` = /24 in decimal|Segments restrict lateral movement – an **Insider Threat** in one subnet can't easily reach another|
|**VLANs**|Virtual subnets at Layer 2|**Zero Trust** micro-segmentation – stops **Ransomware** spreading|
|**Use Case**|Put public-facing servers in one subnet, internal DBs in another|Even if webserver is compromised (**SQL Injection**), attacker can't reach DB directly|

# **NAT (Network Address Translation)**
| Type                               | How It Works                                                       | Security Impact                                                                                |
| ---------------------------------- | ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| **SNAT** (Source NAT)              | Multiple internal devices share one public IP for outbound traffic | Hides internal IP structure = obscures **Confidentiality**                                     |
| **DNAT** (Port Forwarding)         | Incoming traffic on public IP:port → specific internal IP          | Exposes only specific ports – reduces attack surface                                           |
| **PAT** (Port Address Translation) | Uses different source ports to distinguish connections             | Default stateful firewall – inbound unsolicited traffic is dropped (protects **Availability**) |