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
