# 🛡️ SOC Lab: Deployment & Log Visibility Validation

**Date:** February 7, 2026  
**Objective:** Finalize lab setup using VirtualBox, Windows 10, and Splunk Enterprise to verify Windows Security logging.

---

## 💻 Environment Specifications
* **Host OS:** Windows
* **Virtualization:** Oracle VirtualBox
* **Guest OS:** Windows 10
* **SIEM:** Splunk Enterprise (local installation)

---

## 🛠️ Implementation & Tasks Completed
* Deployed Windows 10 virtual machine in VirtualBox.
* Installed VirtualBox Guest Additions (`VBoxWindowsAdditions.exe`).
* Installed Splunk Enterprise and verified web access at `http://localhost:8000`.
* Opened Event Viewer to inspect Security authentication events.

---

## 🖼️ Evidence & Validation

### 1. VirtualBox & OS Deployment
Successfully booted the Windows 10 instance and verified the desktop environment.

<img src="projects/screenshots/day-01/windows10.png">

### 2. Event Viewer - Security Logs
Confirmed that the system is successfully generating and capturing security telemetry.

<img src="projects/screenshots/day-01/Eventviewer_4625__List.png" width="800" alt="Event Viewer List">

### 3. Deep Dive: Event ID 4625 (Logon Failure)
Captured specific "Audit Failure" logs showing Status `0xc000006d` and SubStatus `0xc0000380`.

| General View | Event Data (Technical) |
| :---: | :---: |
| <img src="projects/screenshots/day-01/Event4625_General.png" width="800"> | <img src="projects/screenshots/day-01/Event4625_Eventdata.png" width="800"> |

---

## 🚀 Next Steps
* Analyze specific Windows authentication events.
* Configure Splunk to ingest Windows Security logs.
* Install Sysmon for advanced process-level telemetry.
