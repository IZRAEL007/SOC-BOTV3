# BOTSv3 SOC Investigation – Day 2
**COMP5002 – Security Operations and Incident Response with Splunk**

---

## Day 2 Focus: Tier 1 SOC Analysis – Initial Access

### Q1. UserAgent used to upload malicious OneDrive link
```
Mozilla/5.0 (X11; U; Linux i686; ko-KP; rv: 19.1br) Gecko/20130508 Fedora/1.9.1-2.5.rs3.0 NaenaraBrowser/3.5b4
```

### Q2. Macro-enabled attachment identified as malware
```
Frothly-Brewery-Financial-Planning-FY2019-Draft.xlsm
```

### SOC Interpretation
- Anomalous UserAgent indicates suspicious cloud activity
- Macro-enabled Office documents remain a common initial access vector

### Evidence
- SPL queries and screenshots stored under `/evidence/splunk_queries` and `/evidence/screenshots`

---

**Next Phase:** Tier 2 endpoint investigation and privilege escalation analysis.
