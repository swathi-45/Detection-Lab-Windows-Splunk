# 🛡️ SOC Analyst Portfolio – Detection Engineering Lab

**Author:** Your Name  
**Focus:** Detection Engineering, Authentication Monitoring, and SIEM Operations using Splunk.

---

## 🏗️ Lab Architecture

This lab simulates attacker behavior against a monitored Windows endpoint to develop and validate detection logic.

```
[ Kali Linux ]  --->  [ Windows 10 Endpoint ]  --->  [ Splunk Enterprise ]
   (Attacker)           (Security Logs)             (Search & Alerting)
```

---

## 🛠️ Technical Environment

| Component | Technology |
|------------|------------|
| SIEM | Splunk Enterprise |
| Endpoint | Windows 10 Pro |
| Telemetry | Windows Security Logs |
| Virtualization | Oracle VirtualBox |
| Attack Simulation | Kali Linux |

---

# 📁 Security Projects & Case Studies

Each project includes:
- Log source validation
- Attack simulation
- SPL query development
- Detection rule creation
- False positive considerations

---

## 1️⃣ Lab Deployment & Log Validation

### Objective
Establish end-to-end telemetry flow from Windows endpoint to Splunk.

### Actions Performed
- Deployed Windows 10 virtual machine
- Installed Splunk Enterprise
- Configured log ingestion
- Verified Event ID visibility (4624, 4625, 4672)

### Outcome
Confirmed reliable data pipeline and searchable authentication logs.

📄 Documentation: `./projects/day-1-lab-setup.md`

---

## 2️⃣ Windows Authentication Analysis – Brute Force Detection

### Objective
Detect repeated failed authentication attempts (MITRE ATT&CK T1110 – Brute Force).

### Log Source
Windows Security Log (Event ID 4625)

---

### 🔎 Detection Query (Threshold-Based)

```spl
index=main EventCode=4625
| stats count by TargetUserName, Source_Network_Address
| where count > 10
```

### Purpose
Identify accounts experiencing excessive failed login attempts from a single source.

---

### 🔎 Improved Time-Based Detection

```spl
index=main EventCode=4625
| bin _time span=2m
| stats count by _time, TargetUserName, Source_Network_Address
| where count > 5
```

### Purpose
Detect rapid authentication failures within a short time window to reduce false positives.

---

### Findings

- Identified repeated failed login attempts
- Determined source IP generating failures
- Differentiated between normal user mistakes and suspicious patterns

📄 Documentation: `./projects/day-2-authentication-analysis.md`

---

## 🧠 Core Skills Demonstrated

- Splunk installation & configuration
- Windows Security log ingestion
- Event ID analysis (4624, 4625, 4672)
- SPL query development
- Threshold-based detection
- Time-window correlation logic
- Basic detection tuning

---

## 🚀 Next Development Areas

- Password spraying detection
- Success-after-failure correlation
- Sysmon process monitoring
- Privilege escalation detection
- Network-based anomaly detection

---

This lab environment is built in isolation for educational and detection engineering practice.
