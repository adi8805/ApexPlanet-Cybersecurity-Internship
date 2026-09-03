**Phishing**  
_Deceptive communication to steal credentials or data._

- **How:** Fake emails, texts, or websites impersonating trusted entities.
    
- **Targets:** **Confidentiality** (steals logins/credit cards) & **Integrity** (if used to plant false data).

- **Defense:** User training, email filtering, MFA (prevents stolen password from working alone).
    

---

**Malware**  
_Malicious software installed without consent._

- **How:** Viruses, worms, trojans, spyware, keyloggers.
    
- **Targets:** **All 3** – steals data (Confidentiality), corrupts files (Integrity), or slows/crashes systems (Availability).
    
- **Defense:** Antivirus/EDR, patch management, least-privilege accounts.
    

---

**DDoS (Distributed Denial of Service)**  
_Overwhelm a system with traffic to make it unusable._

- **How:** Botnet floods servers/network with fake requests.
    
- **Targets:** **Availability** (primary) – legitimate users locked out.
    
- **Defense:** Rate limiting, traffic filtering, cloud-based DDoS protection (e.g., Cloudflare), auto-scaling.
    

---

**SQL Injection**  
_Insert malicious code into database queries via input fields._

- **How:** Enter `' OR 1=1; --` into a web form to dump database contents.
    
- **Targets:** **Confidentiality** (data exfiltration) & **Integrity** (data alteration/deletion).
    
- **Defense:** Parameterized queries (prepared statements), input validation, least-privilege DB accounts.
    

---

**Brute Force**  
_Trial-and-error to guess passwords or encryption keys._

- **How:** Automated attempts using common passwords, dictionaries, or exhaustive search.
    
- **Targets:** **Confidentiality** (unauthorized access) – leads to data theft.
    
- **Defense:** Account lockouts, CAPTCHA, rate limiting, strong password policies, MFA.
    

---

**Ransomware**  
_Encrypts files and demands payment for decryption key._

- **How:** Typically delivered via phishing or exploit kits; encrypts local and network drives.
    
- **Targets:** **Availability** (denies access to files) **& Integrity** (data is altered/encrypted).
    
- **Defense:** Offline/air-gapped backups, endpoint protection, patch management, email filtering, user awareness.