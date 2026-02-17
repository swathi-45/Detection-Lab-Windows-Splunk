# 🏗️ Lab Deployment & Log Visibility Validation
**Date:** February 7, 2026  

**Objective:** Finalize the lab setup using VirtualBox, Windows 10, and Splunk Enterprise. Verify Windows Security logging and capture evidence.

---

## 💻 Environment Specifications

- **Host OS:** Windows  
- **Virtualization:** Oracle VirtualBox  
- **Guest OS:** Windows 10  
- **SIEM:** Splunk Enterprise (local installation)  
- **Purpose:** Windows log analysis for SOC skill development  

---

## 🛠️ Implementation & Tasks Completed

1. Deployed Windows 10 virtual machine in VirtualBox  
2. Installed VirtualBox Guest Additions (`VBoxWindowsAdditions.exe`)  
3. Installed Splunk Enterprise and verified web access at `http://localhost:8000`  
4. Opened Event Viewer → Windows Logs → Security to inspect authentication events  

---

## 📊 Results & Validation

- System booted successfully  
- Splunk Web interface accessible  
- Windows Security logs confirmed  
- Verified authentication events including:
  - Event ID 4624 (Logon)
  - Event ID 4672 (Special Logon)

---

## 🖼️ Evidence

### VirtualBox – VM Running
![VM Running](../screenshots/day-01/day1_vbox_vm_running.png)

### Splunk Web Interface
![Splunk Dashboard](../screenshots/day-01/day1_splunk_dashboard.png)

### Event Viewer – Security Logs
![Event Viewer Security Log](../screenshots/day-01/day1_eventviewer_security.png)

---

## 🚀 Next Steps

- Analyze specific Windows authentication events  
- Configure Splunk to ingest Windows Security logs  
- Install Sysmon for advanced process-level telemetry  

---

[⬅️ Back to Main Portfolio](../README.md)
