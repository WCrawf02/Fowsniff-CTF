# Fowsniff-Capture The Flag 🔱

Welcome to the world of ethical hacking, where curiosity meets challenge and every keystroke brings you closer to uncovering hidden vulnerabilities. In this Capture the Flag (CTF) adventure, nicknamed **"Fowsniff"**, I'll be stepping into the shoes of a cyber sleuth, navigating through layers of digital defenses to expose the secrets of a vulnerable machine. From port scanning and online sleuthing to cracking hashes and brute-forcing logins, this project is more than just a test of technical skills—it's a journey into the heart of cybersecurity. Join me as I unravel the complexities of **Fowsniff**, one flag at a time. 😁

## Information Gathering 🤓 ## 
The target IP address is provided when the machine is deployed. For this walkthrough, the target IP address is 10.10.110.111.

## Scanning 🩻 ##
**Results**:
- **Port 22/tcp** - SSH - (OpenSSH 7.2p2)
- **Port 80/tcp** - HTTP - (Apache httpd 2.4.18)
- **Port 110/tcp)** - POP3 - (Dovecot pop3d)
- **Port 143/tcp)** - IMAP - (Dovecot imapd)

  ![initial nmap scan](https://github.com/user-attachments/assets/14302e40-3f1e-4e4f-aa0a-88422f970a5b)

## Enumeration 🔬 ##
Access the web server running on port 80 by visiting **htpp://<target_IP>** in the browser. The website reveals that attackers have dumped employee usernames and hashed passwords on Pastebin.

![enum website ](https://github.com/user-attachments/assets/a5865fcc-4eea-41b2-9c8e-bc2e076cf74d)

We then retrieve the list of usernames and hashed passwords and save the data to files on the local machine.

![Password Hashes](https://github.com/user-attachments/assets/6709da69-58fb-4492-b291-e01a7f362933)
