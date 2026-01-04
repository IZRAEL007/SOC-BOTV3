# BOTSv3 SOC Investigation – Day 1
**COMP5002 – Security Operations and Incident Response with Splunk**

---

## Day 1 Focus: Environment Setup and Scope Definition

### Objectives
- Deploy Splunk Enterprise on Ubuntu
- Ingest and validate the BOTSv3 dataset
- Define investigation scope and assumptions

### Dataset Overview
Boss of the SOC Dataset Version 3 (BOTSv3) is a simulated enterprise intrusion dataset created by Splunk to train SOC analysts through realistic attack scenarios.

### Scope
- Single analyst investigation
- Dataset indexed as `index=botsv3`
- Email, cloud, endpoint, Windows, and Linux telemetry

### Assumptions
- Splunk default timezone
- Dataset integrity matches official release

### Validation SPL
```spl
index=botsv3 | stats count by sourcetype
```

### Outcome
Successful ingestion and validation of BOTSv3 data. Key sourcetypes confirmed and baseline visibility established.

---

**Next Phase:** Tier 1 SOC triage and initial access investigation.
