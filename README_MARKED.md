# BOTSv3 SOC Investigation Report
**COMP5002 – Security Operations, Incident Response and Splunk**

---

## 1. Introduction

This repository contains an individual Security Operations Center (SOC) investigation conducted using **Boss of the SOC Dataset Version 3 (BOTSv3)** within **Splunk Enterprise**. BOTSv3 is a publicly available Capture The Flag style dataset developed by Splunk to simulate a realistic enterprise security incident at a fictitious brewing company named *Frothly* [1].

The primary objective of this investigation is to apply SOC methodologies, Splunk Search Processing Language (SPL), and incident response principles to identify, analyze, and document attacker activity across the cyber kill chain. The scope of this work focuses on answering the **300-level BOTSv3 guided questions**, supported by evidence and SOC contextual analysis.

**Scope**
- Single analyst investigation
- Splunk Enterprise deployed on Ubuntu
- BOTSv3 data ingested into `index=botsv3`
- Email, cloud, endpoint, Windows, and Linux telemetry

**Assumptions**
- All timestamps use Splunk default timezone
- Dataset integrity matches the official BOTSv3 release
- Findings are constrained strictly to dataset evidence

---

## 2. SOC Roles and Incident Handling Reflection

### SOC Tier Responsibilities
- **Tier 1 SOC Analyst:** Alert triage, identification of suspicious artifacts, basic SPL pivots
- **Tier 2 SOC Analyst:** Timeline reconstruction, attack scoping, correlation across data sources
- **Tier 3 SOC Analyst:** Threat hunting, detection engineering, control and visibility improvements

### Incident Handling Lifecycle
- **Prevention:** Macro controls, least privilege, application allow listing
- **Detection:** Correlation of O365, SMTP, Sysmon, Windows Security, and osquery logs
- **Response:** Account isolation, indicator blocking, credential resets
- **Recovery:** Post-incident monitoring, detection tuning, documentation

This exercise highlights how cross-domain telemetry correlation is critical for effective SOC operations.

---

## 3. Installation and Data Preparation

### Environment
- Ubuntu Linux Virtual Machine
- Splunk Enterprise
- BOTSv3 Dataset

### Installation Summary
1. Provision Ubuntu VM with sufficient CPU, RAM, and disk
2. Install Splunk Enterprise
3. Clone and ingest BOTSv3 dataset following official instructions [1]
4. Validate ingestion:
   ```spl
   index=botsv3 | stats count by sourcetype
   ```

### Validation
Key sourcetypes confirmed include:
- `ms:o365:management`
- `stream:smtp`
- `WinEventLog:Security`
- `XmlWinEventLog:Microsoft-Windows-Sysmon/Operational`
- `osquery:results`

Screenshots and validation outputs are stored under `/evidence/screenshots`.

---

## 4. Guided Questions – 300 Level Analysis

### Q1. UserAgent used to upload malicious OneDrive link
**Answer**
```
Mozilla/5.0 (X11; U; Linux i686; ko-KP; rv: 19.1br) Gecko/20130508 Fedora/1.9.1-2.5.rs3.0 NaenaraBrowser/3.5b4
```

**SOC Relevance:** Rare and anomalous UserAgent strings in cloud storage activity are strong indicators of compromise.

---

### Q2. Macro-enabled attachment identified as malware
**Answer**
```
Frothly-Brewery-Financial-Planning-FY2019-Draft.xlsm
```

**SOC Relevance:** Macro-enabled Office documents remain a common initial access vector.

---

### Q3. Executable embedded in the malware
**Answer**
```
HxTsr.exe
```

**SOC Relevance:** Office applications spawning uncommon executables is a high-confidence malicious behavior.

---

### Q4. Password for Linux user created by root
**Answer**
```
ilovedavidverve
```

**SOC Relevance:** Root-level account creation indicates full system compromise.

---

### Q5. User created after Windows endpoint compromise
**Answer**
```
svcvnc
```

**SOC Relevance:** Unauthorized account creation is a strong persistence indicator.

---

### Q6. Groups assigned to the compromised user
**Answer**
```
administrators,user
```

**SOC Relevance:** Assignment to privileged groups confirms escalation of privileges.

---

### Q7. Process ID listening on a leet port
**Answer**
```
14356
```

**SOC Relevance:** Listener on port 1337 commonly indicates backdoor or C2 activity.

---

### Q8. MD5 hash of the network scanning binary
**Answer**
```
586EF56F4D8963DD546163AC31C865D7
```

**SOC Relevance:** Hash-based blocking and EDR containment actions can be applied.

---

## 5. Conclusion

This investigation demonstrates a complete attack lifecycle from initial access via malicious email and cloud uploads through endpoint compromise, privilege escalation, and internal network discovery. The BOTSv3 exercise reinforces the importance of SOC visibility across heterogeneous log sources and the value of SPL-driven correlation for incident response.

Future improvements include detection engineering for rare UserAgents, enhanced macro defenses, and behavioral monitoring for account creation and network scanning activity.

---

## 6. Repository Structure

```
.
├── README.md
├── evidence/
│   ├── screenshots/
│   └── splunk_queries/
├── presentation/
│   ├── slides.pdf
│   └── video_link.txt
└── references/
```

---

## 7. Presentation and Continuous Improvement

A recorded presentation (maximum 10 minutes) accompanies this repository and:
- Summarizes investigation findings
- Demonstrates key Splunk queries
- Reflects on SOC operations and incident response lessons

GitHub commit history demonstrates continuous development over a minimum four-week period.

---

## References (IEEE Style)

[1] Splunk Inc., “Boss of the SOC Dataset Version 3,” GitHub Repository. [Online]. Available: https://github.com/splunk/botsv3  
[2] R. F. S. Rosana, “Splunk 3 Task 6: TryHackMe Walkthrough – Security Operations and AWS Incident Response with Splunk,” Medium, May 2025. [Online]. Available: https://medium.com/@RosanaFS/splunk-3-task-6-tryhackme-walkthrough-security-operations-aws-incident-response-with-splunk-4ab8b4afa7f4  

---

## Author

**Israel**  
IT and Security Operations  
COMP5002
