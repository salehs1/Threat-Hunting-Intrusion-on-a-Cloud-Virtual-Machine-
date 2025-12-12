<h1><stong>🚨 SOC Incident Report</stong></h1>

**Report ID:** `INC-2025-0002`  
**Analyst:** Saleh Mohammed Saleh  
**Investigation Date:** 11/27/2025  

---


# 💻 Scenario

> Financially motivated threat actor targeting import/export companies. Known for multi-week operations with eventual ransomware deployment following data theft. Moderate sophistication with preference for low-footprint techniques.

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
- **Analysis:** The attacker was staging the malware in the directory by using `attrib.exe` in the command to facilitate data for exfiltration


<img width="920" height="150" alt="Flag 4 query" src="https://github.com/user-attachments/assets/1f04be3b-4681-4f3e-8288-6b64a0ea5d90" />
<img width="931" height="239" alt="Flag 4 Result" src="https://github.com/user-attachments/assets/17cf6f0a-6227-4498-aaf8-532d77d2b0f1" />


<h2><strong>🚩 Flag 5: DEFENCE EVASION - File Extension Exclusions</strong></h2>

- **Answer:** `3`
- **Analysis:** The file extensions that were excluded from windows defender by including them in `Exclusions\Extensions` registry so the attacker can perform malicious actions without being detected


<img width="633" height="123" alt="Flag 5 query" src="https://github.com/user-attachments/assets/0f87e8de-3ded-4415-bc7f-fcac57d40097" />
<img width="523" height="162" alt="Flag 5 Result" src="https://github.com/user-attachments/assets/c19d93ab-476c-47dc-9c9f-e246693bdb23" />


<h2><strong>🚩 Flag 6: DEFENCE EVASION - Temporary Folder Exclusion</strong></h2>

- **Answer:** `C:\Users\KENJI~1.SAT\AppData\Local\Temp`
- **Analysis:** The attacker included the directory in the `Exclusions\Paths` in the registry key to avoid being detected by Windows Defender. By including `Paths` in the KQL query, the excluded temporary folder can be found.


<img width="650" height="136" alt="Flag 6 query" src="https://github.com/user-attachments/assets/19636a5b-8b6e-4677-a95b-80f20d08d717" />
<img width="724" height="174" alt="Flag 6 Result" src="https://github.com/user-attachments/assets/33c46c34-a591-46b4-bb8c-e29b89f6e2ad" />


<h2><strong>🚩 Flag 7: DEFENCE EVASION - Download Utility Abuse</strong></h2>

- **Answer:** `certutil.exe`
- **Analysis:** After the attacker excluded the files in Windows Defender Configuration, the attacker used and abused the built-in `certutil.exe` to download malicious files while not being detected. 


<img width="923" height="168" alt="Flag 7 query" src="https://github.com/user-attachments/assets/571acce7-3a4d-4073-8077-b16d1f537eea" />
<img width="941" height="465" alt="Flag 7 Result" src="https://github.com/user-attachments/assets/c867b32e-72c8-4183-b19e-2864254ede19" />


<h2><strong>🚩 Flag 8: PERSISTENCE - Scheduled Task Name</strong></h2>

- **Answer:** `Windows Update Check`
- **Analysis:** The scheduled task was created so the attacker can maintain long-term access into the system


<img width="925" height="179" alt="Flag 8 Query" src="https://github.com/user-attachments/assets/ac4519ac-9ea0-4573-85ad-1a1e18479a70" />
<img width="1070" height="246" alt="Flag 8 Result" src="https://github.com/user-attachments/assets/2ee83ddf-109e-48b8-9b2c-e6ef12ee5df4" />


<h2><strong>🚩 Flag 9: PERSISTENCE - Scheduled Task Target</strong></h2>

- **Answer:** `C:\ProgramData\WindowsCache\svchost.exe`
- **Analysis:** The `Windows Update Check` scheduled task is configured in the location `C:\ProgramData\WindowsCache\svchost.exe` for the attacker to maintain persistence on the system.


<img width="921" height="146" alt="Flag 9 Query" src="https://github.com/user-attachments/assets/ac787128-97fe-4ac2-9638-dd34fac47708" />
<img width="1054" height="253" alt="Flag 9 Result" src="https://github.com/user-attachments/assets/43cd0587-881b-495e-b0f3-88648c83e00a" />


<h2><strong>🚩 Flag 10: COMMAND & CONTROL - C2 Server Address</strong></h2>

- **Answer:** `78.141.196.6`
- **Analysis:** The attacker used the `certutil.exe` tool to download malicious files from the command and control server. By including the built-in tool in the KQL query, the IP address for the C2 server can be identified in the commandline being executed by the attacker.


<img width="930" height="128" alt="Flag 10 Query" src="https://github.com/user-attachments/assets/b3f1aae1-4b18-42dc-8cfd-cb189cd0eb0e" />
<img width="928" height="270" alt="Flag 10 Result" src="https://github.com/user-attachments/assets/28066403-8b5e-4530-96c8-f2c7b75dbd5e" />


<h2><strong>🚩 Flag 11: COMMAND & CONTROL - C2 Communication Port</strong></h2>

- **Answer:** `443`
- **Analysis:** The protocol shows that the attacker used `HTTPS` protocol to download files from the command and control server


<img width="881" height="134" alt="Flag  11 Query" src="https://github.com/user-attachments/assets/02c0dd5b-c676-4ab3-9167-59482fe4f4e1" />
<img width="817" height="136" alt="Flag 11 Result" src="https://github.com/user-attachments/assets/62c83760-75af-4adf-bd3a-d90e48595a3c" />


<h2><strong>🚩 Flag 12: CREDENTIAL ACCESS - Credential Theft Tool</strong></h2>

- **Answer:** `mm.exe`
- **Analysis:** The hacker was able to use the credential dumping tool to access and steal credentials from the `LSASS` process memory before exfiltration.



<img width="907" height="139" alt="Flag 12 query" src="https://github.com/user-attachments/assets/942dbdb0-5b9e-4d47-a7d0-d6c87d1aa7a4" />
<img width="998" height="236" alt="Flag 12 result" src="https://github.com/user-attachments/assets/bace8951-77a1-4243-bc0a-84d518a289e3" />


<h2><strong>🚩 Flag 13: CREDENTIAL ACCESS - Memory Extraction Module</strong></h2>

- **Answer:** `sekurlsa::logonpasswords`
- **Analysis:** The module used to extract passwords was used with the `mm.exe` credential dumping tool to extract credentials


<img width="898" height="148" alt="Flag 13 query" src="https://github.com/user-attachments/assets/d44f7fe4-deaa-4395-b427-6f1e65a00ad4" />
<img width="987" height="277" alt="Flag 13 Result" src="https://github.com/user-attachments/assets/9c28a129-95f3-4bcb-91aa-e8e93924a90f" />


<h2><strong>🚩 Flag 14: COLLECTION - Data Staging Archive</strong></h2>

- **Answer:** `export-data.zip`
- **Analysis:** The attacker compressed the stolen data and exfiltrated it using the `curl.exe` executable


<img width="930" height="156" alt="Flag 14 Query" src="https://github.com/user-attachments/assets/bd7190f8-7bf3-48e2-98c8-65efb58b6616" />
<img width="1586" height="287" alt="Flag 14 Result" src="https://github.com/user-attachments/assets/bbaa61e6-6410-4ea1-acff-941420233309" />


<h2><strong>🚩 Flag 15: EXFILTRATION - Exfiltration Channel</strong></h2>

- **Answer:** `discord`
- **Analysis:** The attacker exfiltrated the `export-data.zip` to `discord`


<img width="974" height="156" alt="Flag 15 Query" src="https://github.com/user-attachments/assets/3a59422f-4434-4497-8946-64a0d7512aa0" />
<img width="1566" height="297" alt="Flag 15 result" src="https://github.com/user-attachments/assets/d207903c-9f17-4c92-b9a3-2c66087e7596" />


<h2><strong>🚩 Flag 16: ANTI-FORENSICS - Log Tampering</strong></h2>

- **Answer:** `Security`
- **Analysis:** The attacker first cleared the security logs using `wevutil.exe` tools to get rid of traces that can be used for investigation


<img width="933" height="156" alt="Flag 16 query" src="https://github.com/user-attachments/assets/1e77b2fd-e527-4a8a-9ebf-e4b43dd29c94" />
<img width="1161" height="350" alt="Flag 16 Result" src="https://github.com/user-attachments/assets/613adc84-d3ec-41ef-a026-8b909706c9d5" />


<h2><strong>🚩 Flag 17: IMPACT - Persistence Account</strong></h2>

- **Answer:** `support`
- **Analysis:** The administrator account was created using the executable `net.exe` to provide a backdoor for attacker if needed to perform malicious activities


<img width="929" height="158" alt="Flag 17 Query" src="https://github.com/user-attachments/assets/99d9c0b0-bbd3-4709-80a2-c5de08d751ad" />
<img width="1053" height="232" alt="Flag 17 Result" src="https://github.com/user-attachments/assets/49a4fee2-0d67-439e-bdff-75b2cd074b34" />


<h2><strong>🚩 Flag 18: EXECUTION - Malicious Script</strong></h2>

- **Answer:** `wupdate.ps1`
- **Analysis:** The attacker downloaded a malicios script from the C2 server the IP address of `78.141.196.6`


<img width="723" height="136" alt="Flag 18 query" src="https://github.com/user-attachments/assets/09c04cdb-1af1-4df6-887a-9fcd14ed6621" />
<img width="1489" height="178" alt="Flag 18 Result" src="https://github.com/user-attachments/assets/c3c1fe7b-4a6e-4051-8987-47af06a0b32d" />


<h2><strong>🚩 Flag 19: LATERAL MOVEMENT - Secondary Target</strong></h2>

- **Answer:** `10.1.0.188`
- **Analysis:** The targeted device with the IP address `10.1.0.188` was accessed remotely via RDP.


<img width="953" height="134" alt="Flag 19 Query" src="https://github.com/user-attachments/assets/5c468bb0-b0fa-4696-8ce0-f8800a4e4830" />
<img width="1041" height="247" alt="Flag 19 Result" src="https://github.com/user-attachments/assets/45ff7187-e07d-43a7-b074-2ac6a0952fac" />


<h2><strong>🚩 Flag 20: LATERAL MOVEMENT - Remote Access Tool</strong></h2>

- **Answer:** `mstsc.exe`
- **Analysis:** The command tool was used to connect to '10.1.0.188' via RDP


<img width="852" height="175" alt="Query flag 20" src="https://github.com/user-attachments/assets/e4475f0b-97e5-4963-9cad-c5b533cdc023" />
<img width="1035" height="246" alt="Flag 20 Result" src="https://github.com/user-attachments/assets/3db8be81-6fcb-434d-8023-90946a30e958" />## **KEY FINDINGS**


# 🔎 KEY FINDINGS:

- Malicious IPs: `78.141.196.6`,`88.97.178.12`
- Malicious Files: `wupdate.ps1`, `export-data.zip`
- Compromised Accounts: `kenji.sato`
- C2 Infrastructure: `78.141.196.6`




















