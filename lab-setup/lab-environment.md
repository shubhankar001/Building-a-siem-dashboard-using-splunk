# Lab Environment

## Overview

A virtualized cybersecurity lab was created to generate security events and demonstrate centralized SIEM monitoring using Splunk.

## Virtual Machines

| System | IP Address | Role |
|---|---|---|
| Kali Linux | 192.168.52.128 | Security testing |
| Ubuntu Linux | 192.168.52.137 | Log source / honeypot |
| Windows 11 Pro | 192.168.52.136 | Splunk Enterprise / SIEM |

## Kali Linux

Kali Linux was used to perform controlled security testing against the Ubuntu system.

Activities included:

- SSH authentication testing
- HTTP requests
- Network connectivity testing

## Ubuntu Linux

Ubuntu acted as the primary log-generating system.

Configured components:

- OpenSSH
- Apache2
- vsftpd
- iptables
- Splunk Universal Forwarder

### Log Sources

```text
/var/log/auth.log
/var/log/apache2/access.log
/var/log/apache2/error.log
/var/log/kern.log
```
## Windows 11 Pro

Windows 11 Pro hosted Splunk Enterprise and acted as the centralized SIEM.

The Splunk Universal Forwarder on Ubuntu forwarded logs to Splunk Enterprise using TCP port 9997.

Data Flow
```Kali Linux
     ↓
Ubuntu Linux
     ↓
Splunk Universal Forwarder
     ↓
TCP 9997
     ↓
Splunk Enterprise
     ↓
SPL Analysis
     ↓
SIEM Dashboard
```
## Security Controls

The Ubuntu system included:

-SSH access restrictions\
-iptables IP blocking\
-Firewall logging\
-Centralized security log collection
## Purpose of the Lab

The lab provides an isolated environment for generating, collecting, analyzing, and visualizing security events without affecting production systems.


