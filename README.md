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

- We then retrieve the list of usernames and hashed passwords and save the data to files on the local machine.

![Password Hashes](https://github.com/user-attachments/assets/146aeb2c-2134-4165-96c4-c5a7c91de601)

- Crack the MD5 hashes using hashes.com and save the results to hashcracked.txt.

![Hashes decrypted](https://github.com/user-attachments/assets/830dbd85-d7d7-4346-bac7-55c56c816d82)

- create files for both **usernames** (username.txt) and the newly cracked **passwords** (password.txt.

## Gaining Access 🕸️ ##

- Use Metasploit module for brute forcing the POP3 service: 

  - msfconsole
  - use auxiliary/scanner/pop3/pop3_login
  - set RHOSTS 10.10.110.111
  - set USER_FILE username.txt
  - set PASS_FILE password.txt
  - exploit

![set options in metasploit](https://github.com/user-attachments/assets/ecf9f1c0-aacf-4024-a540-1dfd6e234e04)

