# 🛡️ Case Study: 	SOC165 - Possible SQL Injection Payload Detected.

## 📝 Executive Summary
**Verdict:** True Positive |
**Source IP:** 167.99.169.17 |
**Date:** Feb, 25, 2022, 11:34 AM

---

## 🔍 Investigation Steps:

A WebServer1001 was hit with SQL attack. The **Web Application Firewall** triggered the alert. This is the request that triggered this alert: https[:]//172[.]16[.]17[.]18/search/?q=%22%20OR%201%20%3D%201%20--%20-

<img width="1580" height="439" alt="alert" src="https://github.com/user-attachments/assets/96852d40-e015-447e-a076-cc35e2bbc9d4" />

**Decoded version of the URL that triggered the alert**
<img width="762" height="190" alt="url_decod_trig" src="https://github.com/user-attachments/assets/f4ef67ec-9864-4d9e-872b-93c24fd3a676" />

The severity of the alert is **High** and we can see the device action is **Allowed**

I checked the IP address on Virustotal and found it malicious.
<img width="1304" height="563" alt="virus_tot" src="https://github.com/user-attachments/assets/b95cc4c9-2ae1-4f82-ba82-c34285b8d4b7" />


<br><br>

## HTTP Traffic Investigation:

<img width="806" height="578" alt="exa_http" src="https://github.com/user-attachments/assets/68eb71a1-5318-4c72-93f9-29c1dd390ce4" />
<br><br>

Lets check the **Log Management** tab for more infomation about the IP address.

<img width="1879" height="536" alt="log_man_http" src="https://github.com/user-attachments/assets/cdffe277-6bad-477a-8fd4-966de0117014" />
The malicious IP sent 6 request to the webserver. You can see them in the above screenshot
<br><br>

### The Raw Logs show that only 1 request had **HTTP Status 200**, The rest of them got **HTTP Status 500**. Meaning that the attack was pretty much contained by the WAF.

<img width="619" height="358" alt="con_in" src="https://github.com/user-attachments/assets/d5548617-2d28-444c-9341-d4f4f8c42c8d" />
<img width="602" height="357" alt="http_500" src="https://github.com/user-attachments/assets/8e567777-2693-440e-8138-d4206412e515" />

---

### Here are the decoded payloads that were used in this attack:
<img width="771" height="399" alt="extra_sql_atp" src="https://github.com/user-attachments/assets/a6e35a27-677b-45aa-bf5b-4cfcdff9a0d2" />

---

## Playbook
### Lets begin the playbook and answer the necessary questions
<img width="804" height="542" alt="data_col" src="https://github.com/user-attachments/assets/742d41ca-e91a-4b79-add3-c1df8f249451" />

We collected the Data of IP and the payloads.

<img width="796" height="549" alt="plan_test" src="https://github.com/user-attachments/assets/0a0124f6-0a13-4d7c-8221-ba991587f883" />

It was not a **Planned Test** as there was no mail or notification mentioned about it.

<img width="808" height="422" alt="dir_traf" src="https://github.com/user-attachments/assets/61e64b75-220d-43b2-b7df-03595e0d42cd" />

The **Traffic of request** was coming from the Internet.

<img width="800" height="435" alt="traf_mal" src="https://github.com/user-attachments/assets/1a52e21a-6949-4f9e-bfc6-e1f407cf15be" />

The traffic was indeed **Malicious** since the request had SQL payloads in them.

<img width="803" height="618" alt="socl2esc" src="https://github.com/user-attachments/assets/356ab5dc-1e85-402b-b5b6-99549623ca9b" />

I don't need to escalate the alert further to Soc L2 since the attack was contained and it was a basic SQL payload attack.

---

## Closing the alert.

### Analysis Note:

<img width="799" height="465" alt="ana_note" src="https://github.com/user-attachments/assets/28ba8e84-dd4e-4651-bb92-ba796be2a801" />

### Artifacts:

<img width="804" height="524" alt="arti" src="https://github.com/user-attachments/assets/26cdcfd1-9fd4-4e7f-9bb7-102c87e614d0" />

### Closing comment and Selection of alert nature:

<img width="607" height="431" alt="clos_alr" src="https://github.com/user-attachments/assets/606dc173-49fd-47c1-bc09-2fc1fac83f3b" />

---

## Investigation Successful:

<img width="1603" height="509" alt="suc_inves" src="https://github.com/user-attachments/assets/44a6b683-d5f8-466a-990f-59733fd32dc9" />
