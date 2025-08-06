# 🛡️ 2025 Target WiCyS Challenge (Tier 1) – Writeup

**CTF Name:** 2025 Target WiCyS Challenge  
**Date:** July, 1 - August, 14  
**Total Challenges:** 12  
**Completed:** 12/12  
**Points:** 3010/3010   
**Place:** 7th   
**Participants:** 1000+  

This challenge simulates a cyberattack against a tech company, where participants play both defender (Tier 1) and threat actor (Tier 2) roles. The challenge focuses on incident response, threat detection, and threat intelligence.

---

## 📚 Table of Contents

[D1. Mystery Mail](#d1.-mystery-mail)  
2. [Challenge 2: NAME](#challenge-2-name)
3. [Challenge 3: NAME](#challenge-3-name)
4. [Challenge 4: NAME](#challenge-4-name)
5. [Challenge 5: NAME](#challenge-5-name)
6. [Challenge 6: NAME](#challenge-6-name)
7. [Challenge 7: NAME](#challenge-7-name)
8. [Challenge 8: NAME](#challenge-8-name)
9. [Challenge 9: NAME](#challenge-9-name)
10. [Challenge 10: NAME](#challenge-10-name)
11. [Challenge 11: NAME](#challenge-11-name)
12. [Challenge 12: NAME](#challenge-12-name)

---

## D1. Mystery Mail

**Category:** Email Forensics  
**Points:** 100  
**Solves:** 800  
**Description:**  
> _As a member of the Personalyz.io cybersecurity team, you receive a ransom email threatening to leak stolen data unless demands are met within 48 hours. Your task is to perform initial forensic analysis and extract the sender's original IP address from the email file to assist in incident response._

**Tools Used:**  
- Text Editor

**Solution:**  

**Step 1**  After opening the attached file in the text editor, we are able to see the sender’s IP address.  
<img width="857" height="271" alt="Sender IP" src="https://github.com/user-attachments/assets/cf36b622-d6a2-4bbf-a4ea-c698db902512" />  
The first "Received: from" line (when reading from the bottom up) usually indicates the origin of the message or the server from which the sender's mail client connected. The "From:" address is sgreen123@gwagm.co. This strongly suggests that gwagm.co is the sending domain, and the IP 252.44.98.29 is the server or client that initiated the send to gwagm.co's mail system.

**Flag:** 252.44.98.29

---

## D2. Not-so-Simple Mail Protocol

**Category:** Log Analysis  
**Points:** 100  
**Solves:** 679  
**Description:**  
> _After receiving a ransom email threatening to leak stolen data, your task is to trace earlier attempts by the threat actor to send the same message. Using the Insightful Horizon (OpenSearch Dashboard), identify the first extortion email sent and submit the sender's email address as the flag._

**Tools Used:**  
- OpenSearch Dashboards

**Solution:**  

**Step 1**  
First, I searched the sender’s IP address, but there is only a letter from the previous task in the results. In that email we can trace the email path and other IP addresses indicating a server that handled the email.
<img width="857" height="271" alt="Sender IP2" src="https://github.com/user-attachments/assets/a9146be6-e264-48f7-88fb-06cd76441fe9" />  
Search for the second IP reveals the previous email.
<img width="2038" height="818" alt="First email" src="https://github.com/user-attachments/assets/1aaf46cc-d126-484f-92cd-db1ab6a34105" />  

**Flag:** tharris456@tgwnaagm.co

```bash
# commands you ran
