# Building a SIEM Dashboard Using Splunk

## 📌 Project Overview

This project demonstrates the development of a Security Information and Event Management (SIEM) dashboard using Splunk Enterprise.

A virtualized cybersecurity lab was created using Kali Linux, Ubuntu Linux, and Windows 11 Pro. Ubuntu was used as the log-generating server, Kali Linux was used for controlled security testing, and Windows 11 Pro hosted Splunk Enterprise.

The Splunk Universal Forwarder collected security and system logs from Ubuntu and forwarded them to Splunk Enterprise for analysis and visualization.

---

## 🏗️ Lab Architecture

```text
Kali Linux
192.168.52.128
Security Testing
       │
       │ Network Activity
       ▼
Ubuntu Linux
192.168.52.137
Log Source / Honeypot
       │
       │ Splunk Universal Forwarder
       │ TCP 9997
       ▼
Windows 11 Pro
192.168.52.136
Splunk Enterprise
       │
       ▼
SPL Analysis
       │
       ▼
SIEM Dashboard

```

💻 Lab Environment
| System         | IP Address     | Role              |
| -------------- | -------------- | ----------------- |
| Kali Linux     | 192.168.52.128 | Security testing  |
| Ubuntu Linux   | 192.168.52.137 | Log source        |
| Windows 11 Pro | 192.168.52.136 | Splunk Enterprise |



🛠️ Technologies Used
Kali Linux
Ubuntu Linux
Windows 11 Pro
OpenSSH
Apache2
vsftpd
iptables
Splunk Universal Forwarder
Splunk Enterprise
SPL
VMwares


📡 Log Sources

The Splunk Universal Forwarder monitors the following Ubuntu logs:
| Log Source                    | Sourcetype      |
| ----------------------------- | --------------- |
| `/var/log/auth.log`           | `linux_secure`  |
| `/var/log/apache2/access.log` | `apache:access` |
| `/var/log/apache2/error.log`  | `apache:error`  |
| `/var/log/kern.log`           | `linux_kernel`  |

🔎 Security Analysis

SPL queries were developed to analyze:

Failed SSH authentication
Source/attacker IP addresses
Apache HTTP status codes
Apache requests
Apache errors
Firewall-blocked traffic
Security activity over time

Example: SSH Failed Login Detection
~~~
index=ubuntulinux sourcetype=linux_secure "Failed password"
| rex "from\s+(?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| stats count by src_ip
| where count >= 3
| sort - count
~~~

📊 SIEM Dashboard

The Splunk dashboard provides centralized monitoring of:

SSH Failed Login Attempts
Apache HTTP Status Codes
SSH Authentication Activity Over Time
Top SSH Attacker IPs
Apache Web Requests Over Time
Apache Error Activity
Firewall Blocked Traffic
Total Security Events

🛡️ Security Monitoring Workflow
~~~
Security Testing
       ↓
Ubuntu Log Generation
       ↓
Splunk Universal Forwarder
       ↓
TCP 9997
       ↓
Splunk Enterprise
       ↓
SPL Queries
       ↓
Security Analysis
       ↓
SIEM Dashboard
~~~


🧪 Testing & Results

The environment was tested using controlled security activity.

The project successfully demonstrated:

*SSH authentication monitoring
*Apache web activity monitoring
*Firewall IP blocking
*Firewall event logging
*Centralized log collection
*SPL-based security analysis
*SIEM dashboard visualization



⚠️ Disclaimer

~~~
This project was developed in an isolated virtual laboratory environment for educational and cybersecurity learning purposes.

No unauthorized systems or networks were targeted.
~~~

