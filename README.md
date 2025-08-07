# 🛡️ 2025 Target WiCyS Challenge (Tier 1) – Writeup

**CTF Name:** 2025 Target WiCyS Challenge  
**Date:** July, 1 - August, 14  
**Total Challenges:** 12  
**Completed:** 12/12  
**Points:** 3010/3010   
**Place:** 7th   
**Participants:** 1000+  

> **Point System:**
🟢 100 points – Easy
🟡 300 points – Medium
🔴 500 points – Hard

This challenge simulates a cyberattack against a tech company, where participants play both defender (Tier 1) and threat actor (Tier 2) roles. The challenge focuses on incident response, threat detection, and threat intelligence.

---

## 📚 Table of Contents

[D1. Mystery Mail (Easy, Email Forensics)](#d1-mystery-mail)  
[D2. Not-so-Simple Mail Protocol (Easy, Log Analysis)](#d2-not-so-simple-mail-protocol)  
[D3. Ransom Wrangler (Easy, Social Engineering/Incident Response)](#d3-ransom-wrangler)  

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

After opening the attached file in the text editor, we are able to see the sender’s IP address.  
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

First, I searched the sender’s IP address, but there is only a letter from the previous task in the results. In that email we can trace the email path and other IP addresses indicating a server that handled the email.
<img width="857" height="271" alt="Sender IP2" src="https://github.com/user-attachments/assets/a9146be6-e264-48f7-88fb-06cd76441fe9" />  
Search for the second IP reveals the previous email.
<img width="2038" height="818" alt="First email" src="https://github.com/user-attachments/assets/1aaf46cc-d126-484f-92cd-db1ab6a34105" />  

**Flag:** tharris456@tgwnaagm.co

---

## D3. Ransom Wrangler

**Category:** Social Engineering / Incident Response  
**Points:** 100  
**Solves:** 638  
**Description:**  
> _Here the task is to simulate communication with a ransomware actor to validate claims of a data breach, obtain proof, and negotiate terms including ransom reduction and deadline extension. You will need to collect three flags to complete the challenge: email from stolen data, ransom reduction code and deadline extension code. Flag submiting format: email@example.com:CTF-RAN-XXXXXXXX:CTF-DEA-XXXXXXXX_

**Tools Used:**  
- Custom email interface
- Social Engineering & Negotiation skills

**Solution:**  
The key principles I followed were:
- Show cooperation, not confrontation.
- Acknowledge concessions.
- Present internal policies as non-negotiable, rather than personal choices.
- Emphasize that agreement enables a fast, clean outcome.

The goal is to make the attacker feel like reducing demands is in their best interest, not a loss, but a smart move toward a guaranteed payout.

**Step 1**  
We started by requesting a verifiable sample of the allegedly stolen data.  

Email Sent:
>We have received your message. We understand the gravity of your claims.
>
>Before we can engage in any substantive discussions regarding your demands, it is an absolute necessity for our security and legal teams to independently verify your claims of data exfiltration.
>
>To facilitate this, we require a small, specific sample of the allegedly stolen data. Specifically, we request a single customer email address from the dataset you claim to possess.
>
>Please provide this specific email address. Once verified, we can discuss next steps.
>
>Sincerely,  
>Lead Incident Responder  
>Personalyz.io Security Team

Result:
The attacker responded with full customer data, including an email address:
lelandRowland13058@live.com.au.
This confirmed the breach. Flag 1 collected.

**Step 2**  
Next, we pushed to extend the deadline from 48 to 96 hours, citing internal approval constraints and legal review requirements.  

Email sent:
>We've verified the data sample. This allows us to move forward.
>
>However, your proposed terms present significant practical challenges for us as a regulated entity.
>
>45 BTC requires extensive internal approvals and compliance checks, which we cannot complete within 48 hours.
>
>We require:
>- Deadline Extension: 96 hours from this email.
>- Revised Demand: We're prepared to discuss a figure below 30 BTC.
>
>Sincerely,  
>Lead Incident Responder  
>Personalyz.io Security Team  

Attacker’s Response:  
They first counter-offered 72 hours, but we pushed again:

Follow-Up:  
>While 72 hours is an improvement, achieving the full 96 hours would significantly streamline our ability to proceed efficiently.
>
>Is there any possibility of stretching to the full 96 hours?
>
>We also need to finalize a figure below 30 BTC.
>
>Sincerely,  
>Lead Incident Responder  
>Personalyz.io Security Team

Result:  
Attacker agreed to the 96-hour extension. Flag 3 collected: CTF-DEA-B3B7CB48.

**Step 3**   
Finally, we returned to price negotiation, stating we could not process anything over 30 BTC.

Email Sent:
>Thank you for agreeing to the 96-hour deadline.
>
>Regarding the financial demand, while 35 BTC is a move in the right direction, it's still higher than we can realistically process.
>
>We need to settle on a figure below 30 BTC to proceed.
>
>Sincerely,  
>Lead Incident Responder  
>Personalyz.io Security Team

The attacker countered with 32 BTC. We escalated again:  

Final Push:  
>We appreciate your further movement on the price. The 32 BTC offer, combined with the 96-hour deadline, shows a willingness to find common ground.
>
>However, our internal approval process has a very firm threshold. We absolutely need to finalize this transaction below 30 BTC.
>
>Reaching an agreement just under 30 BTC guarantees immediate action and a swift conclusion for both parties.
>
>Sincerely,  
>Lead Incident Responder  
>Personalyz.io Security Team

Result:  
The attacker accepted a ransom under 30 BTC. Flag 2 collected.  

**Flag:** lelandRowland13058@live.com.au:CTF-RAN-EA602D6D:CTF-DEA-B3B7CB48

```bash
# commands you ran
