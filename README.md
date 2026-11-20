# NETWORKS-ALBERT-BO84-W3
# PENETRATION TESTING REPORT
**PASSWORD CRACKING & HASH ANALYSIS PHASE**  
**W3-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

---

### **Pentester Name (Cybersecurity Professional)**
Albert Kenney Sackitey

### **Program / Batch**
B084 - Networkwalks

### **Date**
20 November 2026

### **Modules Completed**
* **W3-PM1:** Password Cracking with John the Ripper (JTR) on Kali Linux
* **W3-PM2:** Password Cracking with Networkwalks Hash Calculator & Password Cracker Tools

### **Client / Target Scope**
1. Encrypted PDF Lab Files (`My Locked PDF1.pdf`, `My Locked PDF2.pdf`, `My Locked PDF3.pdf`) — Provided by Networkwalks for authorized lab testing
2. `My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf`

### **Permission Secured from Client?**
Yes (Authorized Educational Lab Scope)

### **Phases Covered**
* Phase 1 & 2: Reconnaissance & Network Scanning (Completed in Week 2)
* Phase 3: Password Auditing & Hash Cracking (Current)
* Phase 4–5: In Progress

---

## 1. Liability Disclaimer
I have performed these activities only on the systems, files, and devices where I had secured written permission or own myself. All materials are for educational and research purposes only. Do not use anything from here to break the law. The instructor, the authors, and Networkwalks are not responsible for any misuse of this knowledge. Every action taken is strictly my own responsibility. Unauthorized access is a crime even when no damage occurs.

---

## 2. Introduction
This report covers password auditing and offline/online hash cracking across two mandatory modules for Week 3 of the Networkwalks Cybersecurity & Ethical Hacking Internship:
1. **W3-PM1 (John the Ripper in Kali Linux):** Extracting cryptographic password hashes from locked PDF documents using `pdf2john` and recovering plaintext credentials via rule-based and wordlist (`rockyou.txt`) attacks.
2. **W3-PM2 (Networkwalks Online Security Tools):** Extracting PDF password hashes using the Networkwalks Hash Calculator and performing automated hash cracking via the Networkwalks Password Cracker.

Together, these modules demonstrate how weak or predictable passwords can be recovered once an attacker obtains an encrypted file or password hash.

---

## 3. Tools Used

| Tool | Purpose |
| :--- | :--- |
| **Kali Linux** | Primary penetration testing operating system used for hash extraction and offline cracking. |
| **pdf2john (`pdf2john.pl`)** | Utility used to extract password hashes from encrypted PDF files into a JTR-compatible format. |
| **John the Ripper (JTR)** | Fast offline password cracker supporting dictionary, rule-based, and brute-force attacks. |
| **rockyou.txt** | Standard security auditing wordlist containing common passwords used for dictionary attacks. |
| **Networkwalks Hash Calculator** | Web-based utility used to extract `$pdf$...` password hashes from locked PDF files. |
| **Networkwalks Password Cracker** | Web-based hash recovery tool used to crack extracted PDF hashes. |
| **Evince / PDF Viewer** | Used to open the encrypted PDF files and verify recovered passwords. |

---

## 4. Activities Performed

### 4.1 W3-PM1: Password Cracking with John the Ripper (Kali Linux)
1. **Hash Extraction:**
   Navigated to the directory containing the target encrypted PDF files and extracted the hashes using `pdf2john`:
   ```bash
   pdf2john "My Locked PDF1.pdf" > hash1.txt
   cat hash1.txt
(Repeated the process for My Locked PDF2.pdf and My Locked PDF3.pdf where applicable.)Wordlist Preparation & Hash Cracking:
Ensured rockyou.txt was extracted and executed John the Ripper against the extracted hash file:Bashjohn hash1.txt
# Or using explicit dictionary mode:
john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt
Credential Recovery & Verification:
Displayed the cracked plaintext password using the --show parameter:Bashjohn --show hash1.txt
Recovered Password (My Locked PDF1.pdf): password1 (Update with actual recovered passwords for PDF2/PDF3 if tested)Opened the locked PDF file and entered the recovered password to verify full document access.4.2 W3-PM2: Password Cracking with Networkwalks ToolsHash Extraction via Hash Calculator:Accessed the Networkwalks Hash Calculator (https://networkwalks.com/hash-calculator/).Uploaded My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf and copied the complete $pdf$... hash string.Hash Cracking via Password Cracker:Accessed the Networkwalks Password Cracker (https://networkwalks.com/password-cracker/).Submitted the extracted $pdf$... hash string and executed the cracking process.Recovered Password: password1Verification:Entered the recovered password into the locked PDF document and confirmed full read access.5. Risk Analysis / Impact#Risk / FindingEvidence / ObservationPotential ImpactRisk Level1Weak / Dictionary-Based Document Passwordspdf2john extracted the $pdf$ hash, and JTR / NW Tools cracked the password (password1) within seconds.Any unauthorized party who intercepts or accesses the file can unlock sensitive or confidential documents offline without triggering account lockouts.● High2Unsalted / Fast-to-Compute Legacy PDF EncryptionOlder PDF encryption algorithms allow high-speed offline hash guessing using CPU/GPU cracking tools.Attackers can test millions of password combinations per second offline.● MediumRisk Level Key: ● Critical | ● High | ● Medium | ● Low6. RecommendationsEnforce Strong Password Policies: Require minimum lengths of 14–16+ characters combining uppercase, lowercase, numbers, and special symbols. Avoid dictionary words or predictable patterns like password1.Use Modern Encryption Standards: Protect sensitive PDFs and archives using strong encryption algorithms (such as AES-256) rather than legacy RC4/MD5-based PDF protection.Implement Defense-in-Depth & Access Controls: Store sensitive documents inside encrypted, access-controlled repositories with Multi-Factor Authentication (MFA) rather than relying solely on file-level passwords.Periodic Password Auditing: Security teams should periodically audit organizational credentials and sensitive files using tools like John the Ripper to identify and remediate weak passwords proactively.7. ConclusionDuring Week 3 of the Cybersecurity & Ethical Hacking internship at Networkwalks, practical password auditing and hash cracking exercises were successfully completed using both John the Ripper on Kali Linux (W3-PM1) and the Networkwalks Hash Calculator & Password Cracker (W3-PM2).These labs demonstrated how easily weak, dictionary-based passwords can be recovered once an encrypted file's hash is extracted. Implementing strong passphrase complexity, modern AES-256 encryption, and strict access controls is essential to protecting sensitive organizational data.8. Evidences CollectedAll terminal screenshots (pdf2john, john, john --show), hash text files, browser captures from Networkwalks Tools, and unlocked PDF verifications are uploaded in this repository.
