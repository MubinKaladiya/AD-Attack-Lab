# Phase 4 – Enterprise-Style Initial Access

### Objective
Simulate realistic internal domain compromise using controlled password spraying.

### Target Selection
Created a user list containing only low-privileged accounts.
Avoided privileged and service accounts to prevent detection and disruption.

### Password Strategy
Generated password candidates based on:
- Company naming patterns
- Seasonal trends
- Common corporate defaults

### Tool Selection
Used Kerberos-based spraying (kerbrute) to reduce SMB noise and mimic enterprise red-team techniques.

### Execution
Performed one-password-at-a-time spraying.
Stopped immediately after first successful authentication.

### Result
Discovered valid credentials:
john : Welcome@123

### Credential Validation
Verified authentication via SMB using crackmapexec.

### Security Insight
Weak but policy-compliant passwords remain vulnerable to password spraying attacks.
Initial domain compromise often requires no exploit — only weak credential hygiene.