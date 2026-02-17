# 🛡️ SOC Detection Lab – Windows Authentication Analysis (Splunk)

Hands-on lab focused on Windows Security log ingestion and failed authentication monitoring using Splunk.

---

## 🔧 Lab Environment

- SIEM: Splunk Enterprise  
- Virtualization: Oracle VirtualBox  
- Endpoint: Windows 10 Pro  
- Log Source: Windows Security Event Logs  

---

## ✅ Work Completed

### 1️⃣ Splunk Installation & Validation

- Installed Splunk Enterprise
- Verified web interface access
- Confirmed indexing functionality
- Validated search capability

---

### 2️⃣ Windows Security Log Monitoring

Analyzed the following Event IDs:

- 4624 – Successful Logon  
- 4625 – Failed Logon  
- 4672 – Special Privileges Assigned  

Confirmed logs were searchable and fields were properly extracted.

---

### 3️⃣ Failed Login Analysis (Event ID 4625)

Performed manual login failure testing on Windows endpoint.

#### SPL Query Used

```spl
index=main EventCode=4625
| stats count by TargetUserName, Source_Network_Address
| sort - count
```

Identified:
- Accounts with repeated failed logon attempts
- Source IP generating authentication failures

---

### 4️⃣ Basic Threshold Detection Rule

```spl
index=main EventCode=4625
| stats count by TargetUserName, Source_Network_Address
| where count > 5
```

Created a basic rule to flag excessive failed login attempts.

---

## 🧠 Skills Demonstrated

- Splunk setup & configuration  
- Windows log ingestion validation  
- Event ID analysis  
- SPL query creation  
- Basic detection logic development  

---

This lab was conducted in an isolated environment for educational and detection engineering practice.
