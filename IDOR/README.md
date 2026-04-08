🔓 Lab: Insecure Direct Object References (IDOR)

🚀 Overview

This lab is from PortSwigger Web Security Academy and demonstrates a classic IDOR (Insecure Direct Object Reference) vulnerability caused by missing access control checks.

⸻

🧪 Step 1 – Interacting with the application

I started by using the Live Chat feature and sent a normal message.

Then I clicked:
👉 View transcript

⸻

🔍 Step 2 – Observing the request

The application generated the following request:

```http
GET /download-transcript/2.txt
```
Using Burp Suite, I noticed:

 • The application uses a numeric ID
 • No authorization validation is implemented

⸻

🤔 Step 3 – Testing ID manipulation

I modified the ID in the URL:

```http
GET /download-transcript/1.txt
```
⸻

💥 Step 4 – Result

The request succeeded:

 • I accessed another user’s transcript
 • No access control was enforced

⸻

🔐 Step 5 – Impact (Lab Scenario)

Inside the transcript:

 • Sensitive data was exposed
 • User credentials were visible

This allowed me to log into the victim’s account.


⸻

🧠 Root Cause

 • Missing access control checks
 • Direct use of user-controlled input (ID)
 • No validation of resource ownership

👉 This leads to Broken Access Control (IDOR)

⸻

💣 Impact

 • Unauthorized access to user data
 • Sensitive information disclosure
 • Account takeover (within lab environment)

⸻

🛡️ Mitigation

 • Enforce authorization on every request
 • Validate user ownership
 • Avoid predictable identifiers
 • Use indirect references (UUIDs)

⸻

🎯 Key Takeaway

If user input controls access to resources:

👉 It must always be validated.

⸻

⚠️ Disclaimer

This test was conducted in a legal lab environment (PortSwigger Web Security Academy) for educational purposes only.

⸻

👨‍💻 Author

Ahmed Khader
Cybersecurity | Penetration Tester 
