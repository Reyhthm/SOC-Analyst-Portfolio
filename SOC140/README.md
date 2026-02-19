# 🛡️ Case Study: 	SOC140 - Phishing Mail Detected - Suspicious Task Scheduler

## 📝 Executive Summary

**Verdict:** True Positive

**Host:** EmilyComp (172.16.17.49)

**Date:** 2021/03/22

---

## 🔍 Investigation Steps:

A user received a phishing email which was blocked by the anti-spam system. Here is the detailed infomation of the alert that was triggered.
<img width="1533" height="476" alt="Incident-under-analysis" src="https://github.com/user-attachments/assets/abcfe997-39fb-4243-be3c-d065a279580c" />

The severity of the alert is **Medium** and we can see the device action is **Blocked**
<br><br>

## **Email sample:**
<br>
<img width="1543" height="460" alt="email" src="https://github.com/user-attachments/assets/f3fb16d4-4d29-4293-b843-7f0d240f26cb" />
<br>
The email is short and it says **Open it now!**, hmm thats suspicious. There is also a attachment to this mail. Lets begin our analysis.
<br><br>

<br><br>
These are the following infomation that we need to extract from the mail, EDRs and log analysis.
<br>
<img width="797" height="459" alt="infoneed" src="https://github.com/user-attachments/assets/9101c045-f856-4529-a228-59a853d5cf92" />
<br>



After analysis of hash of email attachment, we can confirm that the attached file is **malicious**.

<img width="1348" height="804" alt="virustotal" src="https://github.com/user-attachments/assets/1c327f68-4c96-4e22-8257-b73c88b78605" />


---


When we run the file, the content is unreadable and it will open a new URL. The malicious URL was found to be hosting illegal content and has since been taken down by the hosting provider.

<img width="892" height="538" alt="suslink" src="https://github.com/user-attachments/assets/31f02f6b-1525-4e3d-b268-3b581de62204" />


---


## **Artifacts:**
<br><br>
<img width="800" height="595" alt="artifacts" src="https://github.com/user-attachments/assets/bbf123e4-7e34-454b-a706-ea433e3fa703" />
---
<br><br>
## **PLAYBOOK:**

<img width="1574" height="353" alt="playbook" src="https://github.com/user-attachments/assets/a5ff0960-b72e-41ff-a769-fdab875ccfbb" />
Lets start the playbook now.
<br><br>

<img width="1567" height="604" alt="e1" src="https://github.com/user-attachments/assets/dcc99b47-bac7-4b33-b799-8afd3cb49a07" />

We have an attachment so we going to select **YES**.


<img width="1233" height="632" alt="e2" src="https://github.com/user-attachments/assets/9e8b2c9c-3165-4b81-87d0-09c0db992e23" />

The attachment is indeed **Malicious** so we are going to select it.


<img width="801" height="468" alt="analysisnote" src="https://github.com/user-attachments/assets/7c589946-df05-4a63-98e3-d42901417f63" />


---

### **Lets close the alert now**

<br>
Action Taken: True Positive - Remediation Successful.
<br><br>
<img width="607" height="440" alt="closealert" src="https://github.com/user-attachments/assets/6643cb92-4e58-4715-a740-2e62c56d0ba7" />

---

## Final Result:

The analysis was a success, I found all the artifacts. We aced the report!

<img width="1601" height="538" alt="success" src="https://github.com/user-attachments/assets/17188d90-2fea-40b7-9d13-dee0d3a0af9f" />
