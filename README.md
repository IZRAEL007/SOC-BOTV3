# BOTSv3 SOC Investigation – Splunk Security Operations Analysis

## Overview

This repository documents a full Security Operations Centre (SOC) investigation conducted using the **Splunk Boss of the SOC Dataset Version 3 (BOTSv3)**. The project simulates a realistic enterprise security incident affecting a fictitious organisation and evaluates both the **technical investigation** and the **operational effectiveness of SOC practices**.

The work goes beyond answering guided questions. It critically examines how SOC roles, workflows, and detection strategies support effective incident detection, investigation, response, and organisational learning.

This repository accompanies:
- A written SOC investigation report
- A recorded evidence presentation (maximum 10 minutes)
- Demonstrable continuous improvement over a minimum four-week period

---

## Objectives

The objectives of this project are to:

- Demonstrate deep understanding of SOC structures, roles, and responsibilities  
- Accurately investigate and answer all BOTSv3 guided questions using Splunk SPL  
- Reconstruct an end-to-end attack lifecycle using cross-domain telemetry  
- Critically reflect on SOC incident handling and operational maturity  
- Evidence continuous analytical and documentation improvement using GitHub  

---

## Dataset and Environment

- **Dataset:** Splunk Boss of the SOC Dataset Version 3 (BOTSv3)
- **Platform:** Splunk Enterprise
- **Operating System:** Ubuntu Linux
- **Data Sources Analysed:**
  - Microsoft Office 365 audit logs
  - Enterprise email (SMTP) telemetry
  - Windows Security and Sysmon logs
  - Linux host telemetry via osquery

The environment reflects a modern hybrid enterprise with cloud services, email infrastructure, and heterogeneous endpoints.

---

## SOC Operating Model

This investigation is framed around a **tiered SOC model**:

- **Tier 1:** Signal detection and initial triage  
- **Tier 2:** Correlation, validation, and incident confirmation  
- **Tier 3:** Detection engineering, threat hunting, and lessons learned  

The project emphasises that effective SOC performance depends on **information flow and analytical judgement**, not rigid escalation or alert volume.

---

## Attack Lifecycle Summary

The reconstructed intrusion follows a realistic enterprise attack pattern:

1. Initial access via macro-enabled phishing email  
2. Endpoint execution through Office-spawned executable  
3. Privilege escalation on Windows and Linux systems  
4. Persistence via local account creation and group assignment  
5. Discovery and network activity including scanning and listening services  

No single alert was sufficient to confirm compromise. Confidence emerged through correlation across multiple telemetry sources.

---

## Repository Structure

botsv3-soc-investigation/
│
├── README.md
├── splunk/
│ ├── guided_questions.md
│ ├── spl_queries/
│ └── dashboards/
│
├── soc_reflection/
│ ├── incident_handling.md
│ ├── lessons_learned.md
│
├── screenshots/
├── video/
│ └── presentation_link.md
└── changelog.md

yaml
Copy code

---

## Splunk Analysis

All BOTSv3 guided questions were answered using **Search Processing Language (SPL)** with an emphasis on:

- Early filtering on high-selectivity fields
- Precise sourcetype usage
- Correlation across cloud, email, endpoint, and host telemetry
- Analyst-oriented query design rather than bulk alerting

Representative SPL queries and their analytical rationale are documented in:

splunk/guided_questions.md

yaml
Copy code

---

## SOC Reflection and Lessons Learned

Critical reflection is a core component of this project. Key themes include:

- The risk of alert fatigue without sufficient context  
- The importance of Linux monitoring parity with Windows  
- The value of behavioural and threat-informed detections  
- The necessity of feedback loops from incidents into detection engineering  

These reflections are documented in:

soc_reflection/

yaml
Copy code

---

## Evidence Presentation

A recorded presentation summarising findings, demonstrating Splunk analysis, and reflecting on SOC operations accompanies this repository.

- Duration: ≤ 10 minutes  
- Audience: Security management and SOC leadership  
- Focus: Findings, correlation, lessons learned, and strategic recommendations  

The presentation link and speaker notes are documented in:

video/presentation_link.md

yaml
Copy code

---

## Continuous Improvement Evidence

This repository demonstrates **continuous work over a minimum four-week period**, evidenced through:

- Incremental commits
- Progressive SPL refinement
- Expanded analytical commentary
- Iterative documentation improvements

A summary of changes is maintained in:

changelog.md

yaml
Copy code

Commit messages are descriptive and reflect analytical progress rather than bulk uploads.

---

## Conclusion

This project demonstrates that effective SOC operations rely on the integration of **people, process, and technology**. While Splunk provides powerful analytical capabilities, meaningful security outcomes depend on disciplined investigation, correlation-driven detection, and continuous organisational learning.

The BOTSv3 dataset provides a valuable platform for developing and evidencing these competencies in a realistic and professionally grounded context.

---

## References

- Splunk Inc. – Boss of the SOC Dataset Version 3  
- NIST SP 800-61r2 – Computer Security Incident Handling Guide# SOC-BOTV3
