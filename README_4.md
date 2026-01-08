# BOTSv3 SOC Investigation – Day 4
**COMP5002 – Security Operations and Incident Response with Splunk**

---

## Day 4 Focus: Tier 3 SOC Analysis and Reporting

### Q7. Process ID listening on leet port
```
14356
```

### Q8. MD5 hash of network scanning binary
```
586EF56F4D8963DD546163AC31C865D7
```

### SOC Interpretation
- Listener on port 1337 indicates potential backdoor
- Hash-based containment enables EDR and network blocking

---

## SOC Reflection

### SOC Tiers
- Tier 1: Triage and alert validation
- Tier 2: Deep investigation and scoping
- Tier 3: Threat hunting and detection engineering

### Incident Handling Lifecycle
- Prevention, Detection, Response, Recovery

---

## Conclusion

This investigation demonstrates a complete attack lifecycle across cloud, email, endpoint, and network telemetry. Findings reinforce the importance of cross-source correlation and structured SOC workflows.

---

## References
1. Splunk Inc., Boss of the SOC Dataset Version 3 – https://github.com/splunk/botsv3
2. Rosana F. S., Splunk 3 Task 6 Walkthrough – Medium, 2025

---

**Project Complete**
