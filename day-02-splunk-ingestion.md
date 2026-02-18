# 🛡️ SOC Lab: Splunk Ingestion & Failed Logon Analysis

**Date:** February 13, 2026  
**Objective:** Configure Splunk to monitor Windows Security logs and utilize Search Processing Language (SPL) to analyze Event ID 4625 (Failed Logon).

---

## 💻 Environment Details
* **Host OS:** Windows 
* **Virtualization:** Oracle VirtualBox 
* **Guest OS:** Windows 10 
* **SIEM:** Splunk Enterprise 
* **Log Source:** `WinEventLog:Security`

---

## 🛠️ Implementation & Tasks Completed
* **Configured Local Data Inputs:** Mapped the Windows Security event channel for ingestion via `Settings` → `Data Inputs`.
* **Verified Indexing:** Confirmed Windows Security events are being successfully indexed in the `main` index.
* **SPL Search Optimization:** Isolated Event ID 4625 to identify account names and specific failure reasons.
* **Technical Analysis:** Interpreted Windows hexadecimal sub-status codes to categorize authentication failures.

---

## 🖼️ Evidence & Validation

### 1. Data Input Configuration
Successfully added the Windows Security log channel as a data input source in the Splunk web interface.

<img src="https://github.com/swathi-45/Detection-Lab-Windows-Splunk/blob/33c267a562b954558d141a0f63e5bc4a5fa1cc4b/day2_input_setup.png" width="400" alt="Splunk Data Input Setup">

### 2. Successful SPL Search (Event ID 4625)
Utilized SPL to filter and table specific fields, allowing for rapid analysis of failed logon attempts.

**Query:**
`index="main" source="WinEventLog:Security" EventCode=4625 | table _time, TargetUserName, Status, Sub_Status`

<img src="https://github.com/swathi-45/Detection-Lab-Windows-Splunk/blob/33c267a562b954558d141a0f63e5bc4a5fa1cc4b/day2_splunk_4625_search.png" width="400" alt="Splunk SPL Search Results">

### 3. Detailed Event Breakdown
Expanded the raw event details within Splunk to inspect metadata and verify specific failure codes.

<img src="https://github.com/swathi-45/Detection-Lab-Windows-Splunk/blob/33c267a562b954558d141a0f63e5bc4a5fa1cc4b/day2_event_deatails.png" width="400" alt="Splunk Event Breakdown">

---

## 🔍 Technical Deep Dive: Decoding Sub-Status
I analyzed raw events to locate the Sub-Status field, which provides the forensic reason for the logon failure. This is critical for distinguishing between user error and malicious activity.

| Sub Status Code | Meaning |
| :--- | :--- |
| **0xc000006a** | The username is correct, but the password is incorrect. |
| **0xc0000064** | The specified user account does not exist (Potential Username Enumeration). |

---

## 🚀 Next Steps
* Install **Sysmon** (System Monitor) for advanced process-level visibility.
* Create a Splunk dashboard to track failed logon trends over time.
* Configure an alert for high-frequency failed logons (Brute Force Detection).
