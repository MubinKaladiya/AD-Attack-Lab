# Phase 2 – Domain Structure & Intentional Misconfiguration

### Objective
Create a realistic Active Directory environment by adding users, service accounts, groups, and a domain-joined workstation in order to simulate common enterprise weaknesses exploited during internal attacks.


### Organizational Unit Design
Created Organizational Units (OUs) to separate objects logically:
- Employees – normal domain users
- IT – administrative groups
- ServiceAccounts – non-interactive service identities

This mirrors how real enterprises structure Active Directory.


### Domain Users
Created low-privileged domain users:
- john
- maria

These users were assigned weak but policy-compliant passwords to simulate common password reuse issues found in corporate environments.

These accounts represent typical employee identities and will later serve as initial access points.


### Service Account Configuration
Created a service account:
- Username: svc-backup
- Password: weak but policy-compliant
- Password never expires: enabled
- User cannot change password: enabled

This reflects a common enterprise misconfiguration where service accounts are poorly managed and rarely rotated.


### Excessive Privileges (Intentional Misconfiguration)
Created an administrative group:
- IT-Admins

Added the service account (svc-backup) as a member of this group.

This represents a critical security flaw, as service accounts should not possess administrative privileges. Such misconfigurations are frequently abused during Kerberoasting and privilege escalation attacks.


### Domain-Joined Workstation
Joined a Windows 10 Pro workstation to the domain:
- Domain: corp.local

The workstation was configured with:
- Static IP address
- DNS pointing to the Domain Controller

This machine simulates a real employee endpoint and will later be used for credential access and lateral movement.


### Issues Faced & Troubleshooting
- The Windows 10 machine initially received an APIPA (169.254.x.x) address due to the absence of a DHCP server on the internal network.
- This prevented communication with the Domain Controller.
- The issue was resolved by manually assigning a static IP and configuring DNS to point to the DC.


### Key Learnings
- Active Directory environments heavily depend on DNS and correct network configuration.
- Weak service account management introduces high-risk attack paths.
- Small configuration mistakes can lead to full domain compromise.


### Why This Phase Matters
This phase establishes realistic weaknesses that attackers commonly exploit, including weak credentials, overprivileged service accounts, and trusted domain-joined workstations.
These conditions enable attacks such as password spraying, Kerberoasting, lateral movement, and privilege escalation.