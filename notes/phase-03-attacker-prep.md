# Phase 3 – Attacker Machine Preparation & Initial Enumeration

### Objective
Prepare the attacker machine (Kali Linux) for internal network enumeration and validate visibility of Active Directory services before launching credential-based attacks.


### Attacker Network Configuration

Kali was connected to the same Internal Network as the Domain Controller and Windows 10 client.

Since the internal network does not provide DHCP, Kali initially received no IPv4 address.

A static IP was manually assigned:

- IP: 192.168.100.30
- Subnet: 255.255.255.0
- DNS: 192.168.100.10 (Domain Controller)

This restored connectivity to the internal AD environment.


### Connectivity Validation

Verified network reachability:

- Successful ping to Domain Controller
- DNS resolution of corp.local
- Confirmed internal routing was functioning

This confirmed that the attacker had network-level access to the domain infrastructure.


### Service Enumeration (Unauthenticated)

Performed Nmap scan against Domain Controller:

Identified key AD services:
- 53/tcp – DNS
- 88/tcp – Kerberos
- 389/tcp – LDAP
- 445/tcp – SMB
- 135/tcp – RPC

These services confirm a standard Active Directory environment.


### SMB Null Session Check

Tested anonymous SMB access using smbclient.

Observed that:
- SMB1 was disabled (secure configuration)
- Anonymous share enumeration was limited

This indicates that while the DC is reachable, it does not allow excessive anonymous access.


### Key Learnings

- Active Directory environments rely heavily on DNS and service discoverability.
- Internal network access is sufficient to begin domain enumeration.
- Even without credentials, attackers can fingerprint AD infrastructure.
- SMB and LDAP exposure are critical to internal AD attack chains.


### Why This Phase Matters

This phase simulates an attacker who has gained internal network access but does not yet possess domain credentials.

It validates:
- Service exposure
- Network segmentation
- Attack surface visibility

This reconnaissance stage is foundational before launching credential-based attacks such as password spraying or Kerberoasting.