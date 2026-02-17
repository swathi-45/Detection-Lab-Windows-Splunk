# 🛡️ Splunk Lab – Windows Authentication Analysis

**Environment:** Splunk Enterprise | Windows 10 (VirtualBox)  
**Logs Monitored:** Event ID 4624, 4625, 4672  

## Work Done
- Installed and configured Splunk  
- Verified Windows Security log ingestion  
- Analyzed failed login attempts (4625)  
- Created basic threshold detection  

## SPL

```spl
index=main EventCode=4625
| stats count by TargetUserName, Source_Network_Address
| where count > 5
```

Identified repeated failed login attempts and associated source IP.
