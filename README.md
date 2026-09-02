# 🛡️ Windows Security Monitoring with Splunk

## 📌 Project Overview

This project demonstrates a hands-on SOC Analyst L1 workflow for monitoring and investigating Windows security events using **Splunk Enterprise**.

The lab focuses on authentication activity, failed login attempts, successful logons, source IP analysis, and identifying suspicious patterns that may indicate a brute-force attack.

---

## 🎯 Objectives

* Collect and monitor Windows Security logs in Splunk
* Understand important Windows Security Event IDs
* Detect failed authentication attempts
* Investigate suspicious login activity
* Identify potential brute-force behavior
* Create Splunk searches and alerts
* Build a SOC monitoring dashboard
* Practice the incident investigation process

---

## 🖥️ Lab Environment

| Component                 | Technology                  |
| ------------------------- | --------------------------- |
| SIEM                      | Splunk Enterprise           |
| Endpoint                  | Windows 11                  |
| Operating System for SIEM | Kali Linux                  |
| Log Forwarder             | Splunk Universal Forwarder  |
| Virtualization            | VMware                      |
| Log Source                | Windows Security Event Logs |

---

## 🔎 Windows Event IDs Monitored

| Event ID | Description                                |
| -------- | ------------------------------------------ |
| 4624     | Successful account logon                   |
| 4625     | Failed account logon                       |
| 4634     | Account logoff                             |
| 4648     | Logon attempted using explicit credentials |

The main focus of this project is **Event ID 4625**, which records failed logon attempts.

---

## 🔍 Splunk Investigation

Example search used to identify failed Windows logons:

```spl
index=* EventCode=4625
```

To identify users experiencing failed logons:

```spl
index=* EventCode=4625
| stats count by Account_Name
| sort - count
```

To analyze failed logons by source IP:

```spl
index=* EventCode=4625
| stats count by src_ip
| sort - count
```

To investigate successful logons:

```spl
index=* EventCode=4624
| stats count by Account_Name
| sort - count
```

---

## 🚨 Brute-Force Detection

Repeated failed authentication attempts against an account can be an indicator of a possible brute-force attack.

As a SOC Analyst, I would investigate:

1. Number of failed login attempts
2. Username being targeted
3. Source IP address
4. Time of the attempts
5. Whether successful login occurred after failures
6. Whether the source IP is known or suspicious
7. Whether the activity affects multiple accounts

---

## 📊 SOC Dashboard

The Splunk dashboard created for this project includes:

* Total Security Events
* Failed Logons
* Successful Logons
* Failed Logons by User
* Failed Logons by Source IP
* Authentication activity over time

### Dashboard Screenshot

## Splunk SOC Dashboard

The dashboard provides a centralized view of Windows authentication activity, including successful logons, failed logons, affected users, and source IP addresses.

![SOC L1 Windows Security Monitoring Dashboard](screenshots/04-soc-l1-dashboard.png)

## Investigation Evidence

### Windows Failed Logon Investigation

![Windows Failed Logon Investigation](screenshots/01-failed-logon-investigation.png)

### Brute Force Detection

![Brute Force Detection](screenshots/02-brute-force-detection.png)

### Brute Force Alert

![Potential Brute Force Alert](screenshots/03-brute-force-alert.png)

---

## 🕵️ Investigation Workflow

The investigation follows a basic SOC L1 process:

**Alert → Triage → Log Analysis → Identify Source → Investigate User → Determine Severity → Respond → Document**

For suspicious authentication activity, the analyst should correlate multiple events instead of relying on a single failed login.

---

## 🛡️ SOC Response

Depending on the investigation results, possible response actions include:

* Validate whether the login attempts were legitimate
* Contact the affected user
* Block or investigate a suspicious source IP
* Reset compromised credentials
* Review successful logons following failed attempts
* Escalate confirmed incidents to the appropriate security team
* Document investigation findings

---

## 🧠 MITRE ATT&CK Mapping

Potential technique:

**T1110 – Brute Force**

Sub-technique:

**T1110.001 – Password Guessing**

The mapping depends on the evidence identified during the investigation.

---

## 📚 Key Learnings

Through this project, I practiced:

* Windows Security log analysis
* Splunk search and investigation
* Authentication monitoring
* Failed-login detection
* Basic brute-force detection
* SOC alert triage# 🛡️ Windows Security Monitoring with Splunk

## 📌 Project Overview

This project demonstrates a hands-on SOC Analyst L1 workflow for monitoring and investigating Windows security events using **Splunk Enterprise**.

The lab focuses on authentication activity, failed login attempts, successful logons, source IP analysis, and identifying suspicious patterns that may indicate a brute-force attack.

---

**Sana Sultana**

Aspiring SOC Analyst | Cybersecurity | SIEM | Splunk
