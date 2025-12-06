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


<h2><strong>🚩 Flag 6: DEFENCE EVASION - Temporary Folder Exclusion</strong></h2>

- **Answer:** `C:\Users\KENJI~1.SAT\AppData\Local\Temp`
- **Analysis:**


<img width="650" height="136" alt="Flag 6 query" src="https://github.com/user-attachments/assets/19636a5b-8b6e-4677-a95b-80f20d08d717" />
<img width="724" height="174" alt="Flag 6 Result" src="https://github.com/user-attachments/assets/33c46c34-a591-46b4-bb8c-e29b89f6e2ad" />


<h2><strong>🚩 Flag 7: DEFENCE EVASION - Download Utility Abuse</strong></h2>

- **Answer:** `certutil.exe`
- **Analysis:**


<img width="923" height="168" alt="Flag 7 query" src="https://github.com/user-attachments/assets/571acce7-3a4d-4073-8077-b16d1f537eea" />
<img width="941" height="465" alt="Flag 7 Result" src="https://github.com/user-attachments/assets/c867b32e-72c8-4183-b19e-2864254ede19" />


<h2><strong>🚩 Flag 8: PERSISTENCE - Scheduled Task Name</strong></h2>

- **Answer:** `Windows Update Check`
- **Analysis:**


<img width="925" height="179" alt="Flag 8 Query" src="https://github.com/user-attachments/assets/ac4519ac-9ea0-4573-85ad-1a1e18479a70" />
<img width="1070" height="246" alt="Flag 8 Result" src="https://github.com/user-attachments/assets/2ee83ddf-109e-48b8-9b2c-e6ef12ee5df4" />


<h2><strong>🚩 Flag 9: PERSISTENCE - Scheduled Task Target</strong></h2>

- **Answer:** `C:\ProgramData\WindowsCache\svchost.exe`
- **Analysis:**


<img width="921" height="146" alt="Flag 9 Query" src="https://github.com/user-attachments/assets/ac787128-97fe-4ac2-9638-dd34fac47708" />
<img width="1054" height="253" alt="Flag 9 Result" src="https://github.com/user-attachments/assets/43cd0587-881b-495e-b0f3-88648c83e00a" />


<h2><strong>🚩 Flag 10: COMMAND & CONTROL - C2 Server Address</strong></h2>

- **Answer:** `C:\ProgramData\WindowsCache\svchost.exe`
- **Analysis:**


<img width="883" height="183" alt="Flag 10 Query" src="https://github.com/user-attachments/assets/6675c5b8-883e-4113-82ad-3cf6f90bdfac" />
<img width="928" height="270" alt="Flag 10 Result" src="https://github.com/user-attachments/assets/28066403-8b5e-4530-96c8-f2c7b75dbd5e" />





