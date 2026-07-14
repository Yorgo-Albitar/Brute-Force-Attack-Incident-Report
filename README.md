# 🚨 Security Incident Report — Brute Force Attack & Malicious File Distribution

A full security incident investigation involving a brute force attack, credential compromise, source code tampering, and malicious file distribution via HTTP. Completed as part of the Google Cybersecurity Professional Certificate.

## 📖 Project Overview

Investigated a complex security incident where a **former employee** used a brute force attack to compromise an admin account, modified the website's source code to distribute malware to customers, and redirected legitimate traffic to a malicious domain. Documented the attack chain, identified the protocols involved, and recommended remediation to prevent future incidents.

## 🎯 Incident Timeline

**Attack Start Time:** `14:18:32.192571`

## 🔍 Section 1: Network Protocol Involved

### Primary Protocol: **HTTP (HyperText Transfer Protocol)**

The incident centered around HTTP traffic to the compromised website (`yummyrecipesforme.com`). Analysis showed:

- 🌐 The attacker used **HTTP** to access and manipulate the website
- 📊 Log analysis revealed **abnormal traffic patterns** consistent with a malicious file being served
- 🔄 High volumes of inbound and outbound traffic tied to the malicious file distribution
- 📚 HTTP operates at the **Application Layer** of the TCP/IP model

### Evidence From Logs

```
IP your.machine.56378 > greatrecipesforme.com.http:
```

This shows redirection of client traffic from the legitimate site to the attacker-controlled domain.

## 📋 Section 2: Incident Documentation

### 👤 Attacker Profile
A **former employee** with prior knowledge of the company's systems, particularly the admin credentials being set to a **weak/default password**.

### 🔓 Attack Chain

#### **Step 1: Initial Access — Brute Force Attack**
- Attacker used a **brute force method** to guess the admin password
- Success indicates the password was **weak or default**
- After gaining access, the attacker **changed the password** to lock out legitimate admins

#### **Step 2: Source Code Modification**
- Attacker modified the website's source code
- Injected code that **prompted customers to download a malicious file**
- Also implemented a redirect to a fake domain (`greatrecipesforme.com`)

#### **Step 3: Malware Distribution**
- Legitimate customers received prompts to download files
- Downloading the file **redirected them to the malicious domain**
- Victim machines began showing signs of infection:
  - Unusual system behavior
  - Slow performance
  - Unexpected domain name changes

#### **Step 4: DNS & Server Compromise Evidence**
- Logs showed the attacker **obtaining the server IP via DNS protocol**
- Attacker **established persistent connection** with the server
- HTTP methods were used to serve the malicious download

### 🧪 Sandbox Verification
- The website was tested in a **sandbox environment**
- Confirmed the same malicious behavior:
  - File download prompt appeared
  - Redirect to `greatrecipesforme.com` occurred
- A **senior analyst confirmed** the website was compromised

### 🎯 Root Cause
The attacker successfully executed a brute force attack because:
- The admin password was set to a **default/weak value**
- No account lockout policies were in place
- No multi-factor authentication was enforced

## 💡 Section 3: Remediation Recommendations for Brute Force Attacks

### 🔐 1. Enforce Strict Password Policies
- **Minimum 10+ characters**
- Combination of **uppercase, lowercase, numbers, and special characters**
- Applied especially strictly to **admin accounts**
- Disallow common or default passwords

### 🛡️ 2. Implement Multi-Factor Authentication (MFA)
- Require **two or more authentication factors** for all admin accounts
- Even if the password is compromised, the attacker cannot access the account without the second factor
- Options include:
  - Authenticator apps (Google Authenticator, Authy)
  - Hardware tokens (YubiKey)
  - SMS/email codes (least secure but better than nothing)

### 🚫 3. Prohibit Password Reuse
- No password should ever be reused, regardless of how much time has passed
- The attacker gained access through a previously used default password
- Implement password history enforcement in the identity system

### 🔒 4. Additional Recommendations
- **Account lockout policies** — lock accounts after a set number of failed login attempts
- **Rate limiting** — slow down repeated login attempts from the same IP
- **Monitoring & alerting** — trigger alerts on unusual login patterns (e.g., brute force attempts)
- **Regular password rotation** for privileged accounts
- **Revoke access for former employees** immediately upon separation

## 🛠️ Skills Demonstrated

- **Security Incident Investigation**
- **HTTP / DNS Protocol Analysis**
- **Log Analysis** for attack evidence
- **Brute Force Attack Recognition**
- **Insider Threat Awareness** (former employee scenario)
- **Sandbox Analysis** for malware verification
- **TCP/IP Model** understanding
- **Password Policy Design**
- **MFA Implementation Recommendations**
- **Professional Incident Reporting**

## 💡 Key Concepts Applied

- **Brute Force Attack** — repeated password guessing to gain unauthorized access
- **HTTP (HyperText Transfer Protocol)** — application layer protocol for web traffic
- **DNS (Domain Name System)** — translates domain names to IP addresses
- **Source Code Injection** — malicious modification of legitimate website code
- **Malware Distribution** — using compromised infrastructure to spread malicious files
- **Sandbox Environment** — isolated system for safely analyzing suspicious content
- **Insider Threat** — attacks originating from current or former employees
- **Multi-Factor Authentication (MFA)** — layered authentication using multiple factors

## 🎓 Lessons Learned

- **Default passwords are a critical vulnerability** — always change them immediately
- **Former employees pose ongoing risk** — access must be revoked promptly upon separation
- **MFA can stop most credential-based attacks** — even if passwords are compromised
- **Sandbox analysis is essential** — confirms attacker behavior in a safe environment
- **Log analysis is the backbone of incident response** — every action leaves traces
- **Attack chains often use multiple techniques** — recognizing them requires broad knowledge

## 🛡️ Real-World Applications

The skills applied here are directly used in real SOC roles:

- 🚨 **Investigating suspicious login patterns** (brute force detection)
- 🔍 **Analyzing HTTP/DNS logs** for evidence of compromise
- 📊 **Correlating events across multiple data sources**
- 🧪 **Malware analysis in sandbox environments**
- 📝 **Writing formal incident reports** for stakeholders
- 💡 **Recommending controls** to prevent recurrence

## 📚 Certificate Context

This project was completed as part of the **Google Cybersecurity Professional Certificate** on Coursera, demonstrating practical application of incident response methodology, protocol analysis, and security recommendations in a simulated enterprise scenario.

## 👤 Author

**Yorgo Albitar**
Cybersecurity Student | Aspiring SOC Analyst
📧 Email: Yorgobitar59@gmail.com
🔗 GitHub: https://github.com/Yorgo-Albitar
