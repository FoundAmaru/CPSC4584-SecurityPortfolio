# Week 3: Unauthorized USB Drive in Radiology
**Course:** CPSC 4584 | Special Topics in Information Security
**Date:** September 14, 2026
**Analyst:** Rodney Evans
**Incident ID:** INC-2026-0914-001

---

## Incident Summary

An unmarked USB drive was discovered plugged into a restricted Radiology suite workstation that accesses PACS and EHR systems. The device was secured in SOC custody,
and the workstation was isolated from the clinical network pending further review.

---

## Chain of Custody

The chain of custody of the drive is important to ensure the integrity of the evidence and prevent tampering that could reduce its reliability if legal action becomes necessary.
It was maintained when the technician brought the drive directly to IT without opening any files or connecting it to another workstation,
allowing IT to log the device and escalate it safely to the SOC.

---

## Key Encoding Finding

**String Found:** Y3VybCAtcyAtbyAvZGV2L251bGw=

**Encoding Type:** Base64

**Decoded Content:** curl -s -o /dev/null

**Significance:** A common command for attackers which when taking into account other evidence is prudent to treat as malicious.

---

## Terminal Commands Used

| Command | Purpose |
|---------|---------|
| echo "..." \| base64 | [Explain what you learned about Base64 representation.] |
| echo "..." \| base64 -d | [Explain what decoding revealed.] |
| xxd .bashrc \| head -6 | [Explain what the hex dump showed.] |
| strings .bashrc \| grep -i "..." | [Explain how pattern filtering narrowed the output.] |

---

## Escalation Recommendation

I would escalate this situation to a SOC senior due to the severe risks involved. The strongest evidence is the discovery of an unauthorized USB drive plugged into restricted workstation,
combined with an encoded Base64 payload executing a silent outbound curl command designed to evade local logging. A key question requiring deeper investigation is
identifying the exact destination endpoint of the curl request.

---
*CPSC 4584 | Governors State University | Fall 2026*
    
