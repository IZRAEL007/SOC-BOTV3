# BOTSv3 SOC Investigation – Day 3
**COMP5002 – Security Operations and Incident Response with Splunk**

---

## Day 3 Focus: Tier 2 SOC Analysis – Endpoint Compromise

### Q3. Executable embedded in malware
```
HxTsr.exe
```

### Q4. Password for Linux user created by root
```
ilovedavidverve
```

### Q5. User created after Windows endpoint compromise
```
svcvnc
```

### Q6. Groups assigned to compromised user
```
administrators,user
```

### SOC Interpretation
- Office-spawned executables confirm malicious macro execution
- Account creation and group assignment demonstrate privilege escalation
- Root-level Linux activity confirms full compromise

---

**Next Phase:** Tier 3 threat hunting and final reporting.
