# Active Directory Home Lab – corp.local

This repository documents a complete small-scale Active Directory environment built in VirtualBox.  
The lab simulates a realistic corporate setup including domain services, user and group management, file sharing with permissions, and a domain-joined client machine.

It is designed for hands-on learning, certification preparation, and general homelab experimentation.

---

## Project Overview

- Domain Name: **corp.local**
- Domain Controller: **SERVER1** running Windows Server 2022  
- Client Workstation: **CLIENT1** running Windows 10 Pro  
- Virtual Network: **VirtualBox Internal Network named LABNET**

---

## Network Configuration

| Machine | IP Address     | Subnet Mask   | Default Gateway | Preferred DNS |
|--------|----------------|---------------|----------------|---------------|
| SERVER1 | 192.168.20.50 | 255.255.255.0 | 192.168.20.1   | 192.168.20.50 |
| CLIENT1 | 192.168.20.110 | 255.255.255.0 | 192.168.20.1   | 192.168.20.50 |

---

## Active Directory Design

### Organizational Unit Structure
- **north**

### Security Groups
- **employees**
- **managers**

### Test Accounts
- **emp01** – member of employees  
- **mgr01** – member of managers  

---

## Virtual Machine Specifications

### SERVER1 – Domain Controller
- Operating System: Windows Server 2022  
- RAM: 4 GB  
- CPU: 2 vCPUs  
- Storage: 40 GB  
- Installed Roles:
  - Active Directory Domain Services  
  - DNS Server  

### CLIENT1 – Workstation
- Operating System: Windows 10 Pro  
- RAM: 4 GB  
- CPU: 2 vCPUs  
- Storage: 50 GB  
- Joined to domain: **corp.local**

---

## File Services and Permissions

### Shared Folders on SERVER1

- `C:\FILES\Employees`
- `C:\FILES\Managers`

### Share Permissions

- `\\SERVER1\Employees`
  - Full Control granted only to the **employees** group  

- `\\SERVER1\Managers`
  - Full Control granted only to the **managers** group  

NTFS permissions are configured to match share permissions and enforce proper access control.

---

## Verified Functionality

All major components of the lab were tested successfully:

- Network connectivity using ping  
- DNS resolution of corp.local  
- Successful domain join from CLIENT1  
- Authentication with domain accounts  
- Access to correct file shares  
- Proper denial of access for unauthorized users  

---

## Repository Structure

<pre>
ad-lab-corp/
├── README.md
├── docs/
│   ├── setup-guide.md
│   ├── troubleshooting.md
│   └── ad-structure.md
└── screenshots/
    ├── client1-network-config.png
    ├── server1-network-config.png
    ├── ad-users-and-groups.png
    ├── file-shares-permissions.png
    ├── successful-domain-join.png
    └── access-tests.png
</pre>


## Screenshots

The screenshots folder contains images showing key configuration steps and test results, including:

- Network configuration  
- Active Directory users and groups  
- File share permissions  
- Successful domain join  
- Access verification tests  

---

## Purpose and Learning Outcomes

This lab was built to gain practical experience with:

- Installing and configuring Active Directory Domain Services  
- DNS setup and integration  
- Organizational units, users, and groups  
- Share and NTFS permissions  
- Domain client configuration  
- Basic Windows domain troubleshooting  

---

Feel free to fork this repository, modify it for your own lab, or use it as a reference for learning.

Questions, suggestions, or improvements are always welcome.

---

**Leo Nilsson**  
[LinkedIn](https://www.linkedin.com/in/leonilsson070426/)  
[GitHub](https://github.com/leonilsson07/ad-lab-corp)