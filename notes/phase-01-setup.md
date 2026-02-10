### **Objective**
Build an isolated Active Directory lab to simulate a real enterprise environment for offensive security testing.


### **Lab Architecture**
- DC01: Windows Server 2022 (Domain Controller)
- WIN10-CLIENT: Windows 10 Pro (Domain-joined workstation)
- KALI: Kali Linux (Attacker machine)
- Network: VirtualBox Internal Network (isolated)


### **Network Design**
The lab uses an Internal Network to ensure all attack traffic remains isolated from the host and internet. 
This simulates an internal corporate environment where attackers already have network access.


### **Domain Controller Setup**
- Renamed server to DC01 for clarity.
- Assigned a static IP address to prevent DNS and Kerberos issues.
- Installed Active Directory Domain Services role.
- Promoted the server to a Domain Controller.
- Created a new forest and domain: corp.local


### **Authentication & Identity**
After promotion, the local Administrator account became the domain Administrator.
Domain authentication is now handled by Kerberos and LDAP via the Domain Controller.


### **Key Learnings**
- Active Directory is heavily dependent on DNS and static IP configuration.
- Domain Controllers centralize authentication for all domain users.
- Small configuration mistakes can cause major authentication issues.


### **Why This Phase Matters**
This setup phase establishes the authentication infrastructure that will later be abused through attacks such as password spraying, Kerberoasting, and privilege escalation.