# 🛡️ Case Study: 	SOC137 - Malicious File/Script Download Attempt.

## 📝 Executive Summary

**Verdict:** True Positive 

**Source IP:** 172.16.17.37 

**Date:** Mar, 14, 2021, 07:15 PM

<img width="810" height="497" alt="1" src="https://github.com/user-attachments/assets/6039e3a7-11c7-4ac9-b60f-cebf3aab924c" />

## 🔍 Investigation: A user attempted to download a malicious file but was blocked by anti virus.
<img width="1597" height="515" alt="2" src="https://github.com/user-attachments/assets/181ab154-dc3c-41f1-bde0-524522da2c8c" />
The severity of the alert is Medium and we can see the device action is Blocked


After getting the MD5 hash of the file, I ran the hash on virustotal and here are the results.
<img width="1885" height="726" alt="12" src="https://github.com/user-attachments/assets/a5206d1d-a1a2-400a-a242-56691b4f0c02" />


The file tried to run some commands on the host device and here is the proof of it.
<img width="1227" height="521" alt="3" src="https://github.com/user-attachments/assets/3331da61-736c-49a1-bcc6-c98fcae9180e" />

---
## **PLAYBOOK:**

The Device was quarantined/blocked by the antivirus.
<img width="805" height="414" alt="4" src="https://github.com/user-attachments/assets/4f5b7ca2-9179-4d5c-9e1f-66032afed3f0" />

After anaylizing the file, we found it was malicious.
<img width="805" height="441" alt="5" src="https://github.com/user-attachments/assets/6f6c5549-4725-4611-80ed-7d1fffa2c9ec" />

The C2 connection was not accessed by anyone becauase the file was blocked.
<img width="799" height="437" alt="6" src="https://github.com/user-attachments/assets/b848d6b2-166b-4182-8e86-1f2472ff35f5" />

---
## **Artifacts:**

<img width="799" height="536" alt="7" src="https://github.com/user-attachments/assets/e9097f89-c342-4717-a2fc-ec2b7f8d1c05" />

These are the artifacts that I found while investigating.

## **Analysis Note:**
<img width="798" height="466" alt="8" src="https://github.com/user-attachments/assets/4de7ba79-8578-4d42-861a-759571823ff7" />

---

## **Verdict:**
<img width="599" height="431" alt="10" src="https://github.com/user-attachments/assets/26a687de-bd57-43c0-beb5-1e11ee6cb88b" />

<img width="1579" height="495" alt="11" src="https://github.com/user-attachments/assets/7e56b105-576f-4548-aa94-5e55b3ed6bf3" />

