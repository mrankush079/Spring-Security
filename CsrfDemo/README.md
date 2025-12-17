
CSRF Demo: Understanding Cross-Site Request Forgery
This project is a hands-on demonstration of a Cross-Site Request Forgery (CSRF) attack. It illustrates how an attacker can trick a victim's browser into performing unwanted actions on a different website where the victim is currently authenticated.

📌 Project Overview
The demo consists of two main components:

The Vulnerable Web App: A simple banking or profile application that performs actions (like changing an email or transferring funds) using insecure HTTP requests.

The Attacker's Site: A malicious page designed to trigger a hidden request to the vulnerable app without the user's knowledge.

🚀 Getting Started
Prerequisites
Node.js / Python / Docker (adjust based on your actual tech stack)

Two different browser sessions (or use Incognito mode)

Installation
Clone the repository:

Bash

git clone https://github.com/mrankush079/csrfdemo.git
cd csrfdemo
Install dependencies:

Bash

npm install  # or pip install -r requirements.txt
Start the servers:

Bash

npm run start
🛠 The Attack Scenario
Login: Log into the Vulnerable App (localhost:3000) to establish a session cookie.

The Trap: While logged in, open a new tab and visit the Attacker's Site (localhost:4000).

The Trigger: The attacker's site automatically sends a POST request to the vulnerable server using your active session.

The Result: Check the Vulnerable App; you will see that an action (e.g., password change) occurred without your consent.

🛡️ How to Prevent CSRF
To secure this application, we can implement the following defenses:

1. Anti-CSRF Tokens (Recommended)
The server generates a unique, cryptographically strong token for the user session. This token must be included in any state-changing request.

2. SameSite Cookie Attribute
Set the SameSite attribute on session cookies to Lax or Strict to prevent the browser from sending cookies with cross-site requests.

JavaScript

res.cookie('sessionID', '12345', { sameSite: 'strict', secure: true });
3. Verifying Origin/Referer Headers
Check the Origin or Referer HTTP headers to ensure the request is coming from a trusted domain.

⚠️ Disclaimer
This project is for educational purposes only. Never use these techniques on systems you do not own or have explicit permission to test.
