# 🚨 SOC Incident Report

**Report ID:** `INC-2025-XXXX`  
**Analyst:** Saleh Mohammed Saleh  
**Investigation Date:** 11/27/2025  

---

# 🧭 Executive Summary

> *Write this LAST — 3–5 sentences providing a clear overview of the incident, impact, and current state.*

---


# 🕵️‍♂️ Findings & Analysis

<h2><strong>🚩 Flag 1: INITIAL ACCESS - Remote Access Source</strong></h2>

- **Answer:** `88.97.178.12`
- **Analysis:** To find out the attacker's source IP address, it has to be found based on what IP source was able to successfully login to the device`azuki-sl`.

<img width="675" height="118" alt="Flag 1 Query" src="https://github.com/user-attachments/assets/5ba6e383-80a6-4de1-9a90-da46f3cd528b" />
<img width="870" height="245" alt="Flag 1 result" src="https://github.com/user-attachments/assets/4b8935b3-46dd-4f9d-b401-74fc50c390d4" />


<h2><strong>🚩 Flag 2: INITIAL ACCESS - Compromised User Account</strong></h2>

- **Answer:** `kenji.sato`
- **Analysis:** The compromised user account account was identified based on many successful logins from the source with IP address `88.97.178.12`.

<img width="708" height="142" alt="Flag 2 Query 2" src="https://github.com/user-attachments/assets/b7aee4f1-9256-43b4-858c-0bee2ebf11a5" />
<img width="712" height="180" alt="Flag 2 result" src="https://github.com/user-attachments/assets/74535744-d63c-4408-9678-707731398a43" />


<h2><strong>🚩 Flag 3: DISCOVERY - Network Reconnaissance</strong></h2>

- **Answer:** `"ARP.EXE" -a`
- **Analysis:** The attacker was trying to enumerate devices in the network to identify possible lateral movement and any value target using '"ARP.EXE" -a'.


<img width="800" height="143" alt="Flag 3 Query" src="https://github.com/user-attachments/assets/31eff53d-3f8e-450a-84fc-7212060f7a09" />
<img width="823" height="163" alt="Flag 3 Result" src="https://github.com/user-attachments/assets/f09906fb-bca2-4871-8c07-c933cebd8c15" />


<h2><strong>🚩 Flag 4: DEFENCE EVASION - Malware Staging Directory</strong></h2>

- **Answer:** `"C:\ProgramData\WindowsCache`
- **Analysis:**


<img width="920" height="150" alt="Flag 4 query" src="https://github.com/user-attachments/assets/1f04be3b-4681-4f3e-8288-6b64a0ea5d90" />
<img width="931" height="239" alt="Flag 4 Result" src="https://github.com/user-attachments/assets/17cf6f0a-6227-4498-aaf8-532d77d2b0f1" />


<h2><strong>🚩 Flag 5: DEFENCE EVASION - File Extension Exclusions</strong></h2>

- **Answer:** `3`
- **Analysis:**


<img width="633" height="123" alt="Flag 5 query" src="https://github.com/user-attachments/assets/0f87e8de-3ded-4415-bc7f-fcac57d40097" />
<img width="523" height="162" alt="Flag 5 Result" src="https://github.com/user-attachments/assets/c19d93ab-476c-47dc-9c9f-e246693bdb23" />

