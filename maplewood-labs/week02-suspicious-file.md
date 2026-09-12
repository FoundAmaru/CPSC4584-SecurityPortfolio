# Week 2: Suspicious File on a Nurse's Workstation
**Course:** CPSC 4584 | Special Topics in Information Security
**Date:** September 7, 2026
**Analyst:** [Rodney Evans]
**Incident ID:** INC-2026-0907-001

---

## Incident Summary

[An unexpected executable file named patient_notes.txt was created at 3:14 AM within the home directory of clinical workstation MHS C3 NRS 07 during non clinical hours.
Because the assigned nurse denies creating the file and no automated processes were active,
the event suggests unauthorized access and requires evidence collection.]

---

## Key Findings

**Permission Finding:** [The permission string informed me that, despite having a text file extension, the file has execution functions]

**File Type Finding:** [The file command revealed the file was actually an ELF executable and not a text file]

**Timestamp Finding:** [The file was modified outside of working hours with the change time matching this information]

**Strings Finding:** [The string revealed witin the file was an external URL, hiddent tmp path, and a curl command for downloads]

---

## Terminal Commands Used

| Command | Purpose |
|---------|---------|
| pwd && ls -la | [Used to determine where the file is and any potential other suspsicious files] |
| file [filename] | [Used to verify whether the file was the text file it claimed to be which it was not. The file was an ELF executable] |
| stat [filename] | [Used to provide time based metadata to determine when the file was changed. Confirmed the change happened during the suspicious activity time] |
| strings [filename] | [The readable strings within the file are revealed with this command showcasing that it was an external URL,had hidden tmp files, and a curl command] |
| find . -mtime -1 -type f | [Time based search which narrowed down changes to files within the last day showcasing the tmp files which were modified.] |

---

## Escalation Recommendation

[Due to the evidence gathered, I would escalate the situation to the next level. The strongest pieces of evidence for my escalation 
would be the external URL, hidden tmp files, and curl command found using the strings command.
Still, the question of how the unauthorized user was able to get the nurse's account requires Tier 2 investigation.]

---
*CPSC 4584 | Governors State University | Fall 2026*
    
