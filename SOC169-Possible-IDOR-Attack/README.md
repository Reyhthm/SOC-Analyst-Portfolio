# 🛡️ Case Study: 	SOC169 - Possible IDOR Attack.

## 📝 Executive Summary

**Verdict:** True Positive 

**Source IP:** 134.209.118.137 

**Date:** Feb, 28, 2022, 10:48 PM

## 🔍 Investigation: 
On Feb, 28, 2022, 10:48 PM an IP address initiated an IDOR attack on web server with IP: 172.16.17.15. The attack was successful as the device permission was permitted and HTTP status code is 200. As well as the HTTP response size are between 180-350. The device has been quarantined.

<img width="1563" height="437" alt="1" src="https://github.com/user-attachments/assets/1536cf41-3a14-4ccc-a527-ac29b47b1831" />

The severity of attack is **HIGH**. Before we start investigation, let's understand what is IDOR attack.

---

**⚠️An IDOR (Insecure Direct Object Reference) attack occurs when an application exposes a direct reference (like a database key, file path, or user ID) to an internal object.⚠️**

---

Now we know what IDOR is, Lets begin with the investigation.

This is the requested URL by the attacker: 
Requested URL : https://172.16.17.15/get_user_info/
The attacker was trying to get information from different user#

## 🕵🏼‍♂️ Findings: 

**DETECTION**
This ip address is out of company network with origins from US and has been flagged as malicious.
<img width="631" height="512" alt="ip" src="https://github.com/user-attachments/assets/e7e807b5-c4e2-403f-8822-8c32e6e758ed" />

The traffic is indeed malicious, that's why the rule was triggered.
<img width="801" height="438" alt="3" src="https://github.com/user-attachments/assets/70828686-37a1-49be-9545-83e7b03b3277" />

<img width="801" height="418" alt="6" src="https://github.com/user-attachments/assets/b82323c1-c439-46df-b35a-579ed28d16a6" />

Let's take a look at the logs in **Log Management**:
<img width="1578" height="455" alt="8" src="https://github.com/user-attachments/assets/609ee57b-c773-4692-8be2-fe104790c642" />

5 events were found based on our search. Let’s take a look at some of these events.
<img width="602" height="366" alt="9" src="https://github.com/user-attachments/assets/b25560fa-1f53-4efe-a17d-d8bc7e7845b5" />
<img width="602" height="361" alt="11" src="https://github.com/user-attachments/assets/39666805-785b-4528-b688-9f9b45c398d6" />
<img width="603" height="373" alt="10" src="https://github.com/user-attachments/assets/cb1f736b-018b-40d7-8fa4-a16d0efa61f4" />

**The attacker is sending multiple request with different “user_id=#” included.**
<img width="800" height="365" alt="12" src="https://github.com/user-attachments/assets/e6fb4dbf-8190-4bb6-be48-d357cf043145" />
The attacker had several successful requests according to the logs reporting the “200” status.

---

There was no email about a planned test so this was definitely an attack.
<img width="799" height="556" alt="5" src="https://github.com/user-attachments/assets/3fc409f1-6bde-4842-902e-49eb643d0168" />

Based on the indicators identified during the investigation, containment of the affected server endpoint is recommended to prevent additional compromise and limit potential damage.
<img width="1230" height="507" alt="14" src="https://github.com/user-attachments/assets/468ecf85-3b5e-4e87-bcce-41a9b5d44f65" />
<img width="805" height="593" alt="13" src="https://github.com/user-attachments/assets/cedbc994-4ca5-400c-a528-37c17ab5ed06" />

## Closing the Alert.

Artifacts from the findings:
<img width="794" height="476" alt="15" src="https://github.com/user-attachments/assets/f855e441-9a94-44bd-b8f1-0c79fa05d5ff" />

Analyst Note:
<img width="796" height="478" alt="17" src="https://github.com/user-attachments/assets/e8399103-4a21-4d48-8c0c-335d61ad3ae2" />

Escalation to L2:
<img width="787" height="655" alt="16" src="https://github.com/user-attachments/assets/406b576e-fb18-4163-a756-b3787981f869" />

Closing the playbook:
<img width="641" height="454" alt="18" src="https://github.com/user-attachments/assets/d273d97c-0c30-4da2-9d6d-5786ccdc5924" />

Closing Alert:
<img width="602" height="431" alt="19" src="https://github.com/user-attachments/assets/e3ca2b72-fc51-4773-a55a-9dd32a5e1a1b" />

## Verdict:

<img width="1606" height="473" alt="20" src="https://github.com/user-attachments/assets/d17c7ea1-ce1d-48ac-bac4-fa5456dfeea2" />
