# 🛡️ Case Study: 	SOC170 - Passwd Found in Requested URL - Possible LFI Attack.

## 📝 Executive Summary

**Verdict:** True Positive 

**Source IP:** 106.55.45.162 

**Date:** Mar, 01, 2022, 10:10 AM

## 🔍 Investigation:

A webserver recevied a GET request with a malicious LFI attack payload. Here is the detailed infomation of the alert that was triggered.
Payload used: https[:]//172.16.17.13/?file=../../../../etc/passwd
<img width="1597" height="500" alt="1" src="https://github.com/user-attachments/assets/a388df3c-a2b9-444f-9003-b6b0d55755b8" />

The severity of attack is **HIGH**. Before we start investigation, let's understand what is LFI attack.

---

**⚠️LFI ATTACK: A Local File Inclusion (LFI) attack exploits vulnerable web applications that improperly sanitize user input, allowing attackers to trick the server into executing or exposing files on the local file system.⚠️**

---

Now we know that LFI is a web application attack, Lets begin with the investigation.

<img width="1829" height="335" alt="4" src="https://github.com/user-attachments/assets/beedeae6-303a-4831-b2f3-1f4722d03190" />

The IP that sent the payload doesn't have a bad reputation. That doesn't mean its a good and trusted IP address.

---

The Log Management tab does have a registered log of the LFI attack payload:
<img width="1579" height="704" alt="3" src="https://github.com/user-attachments/assets/b7c2d947-9bf2-4aca-8063-0a5084e7bf61" />

## 🕵🏼‍♂️ Findings: 

The GET request had a LFI attack payload, which is a web application attack. The Payload was trying to get the password file from the webserver. In this case the traffic was **MALICIOUS**
<img width="808" height="438" alt="7" src="https://github.com/user-attachments/assets/f9a9fc02-f094-4671-b731-40e309371a27" />

---

The type of attack is **LFI** (Local File Inclusion):
* **Target:** Targets `/etc/passwd`, a sensitive configuration file located locally on the Linux server.
* **Method:** Uses the `../../../../` sequence, known as **Path Traversal** or "Dot-Dot-Slash" navigation.
* **Logic:** Each `../` tells the server’s operating system to move up one directory level to escape the web root.
<img width="800" height="376" alt="8" src="https://github.com/user-attachments/assets/63ab3ab4-f599-4316-ba68-992d03960419" />

---

The IP address that made the GET request was not registered to any of the company network. It came from the Internet. Thats why Im going to select [Internet -> Company network]
<img width="799" height="381" alt="10" src="https://github.com/user-attachments/assets/b73b9de3-3724-4075-8ebd-b85aa565ef8f" />

---

It was indeed blocked by the security solutions. The HTTP response size is **0** and the HTTP response status is **500**. Hence proving that the attack was not successful.
<img width="793" height="337" alt="12" src="https://github.com/user-attachments/assets/2a0c99fb-05e8-489d-bef5-70d2eb5fdec7" />

---

As the attack was successfully blocked by the security solutions, we do not need to escalate the alert to tier 2 for further investigation.

<img width="803" height="585" alt="14" src="https://github.com/user-attachments/assets/23b7bed6-2bc7-4e73-b31b-7f12a3bdcccb" />

## 🔍 Artifacts

<img width="796" height="411" alt="13" src="https://github.com/user-attachments/assets/4d44337b-5d58-43b3-aa90-244f0524fe05" />

---

**Analysis Notes:**

<img width="796" height="471" alt="15" src="https://github.com/user-attachments/assets/1c7890d6-bf6d-45ce-982d-096cc811446e" />

---

**Closing Alert:**

<img width="596" height="429" alt="16" src="https://github.com/user-attachments/assets/1726ade7-926d-444d-94b3-232a009c50ee" />

---
## ✅ Outcome:
<img width="1595" height="520" alt="17" src="https://github.com/user-attachments/assets/1d90a63c-2d92-426b-9264-e9bdf15a73fa" />
