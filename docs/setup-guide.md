# Setup Guide

This guide walks through building the corp.local Active Directory lab in VirtualBox.

## Prerequisites

- VirtualBox installed on the host
- Windows Server 2024 ISO
- Windows 10 Pro ISO
- At least 8 GB RAM available on the host

## 1. Create the VirtualBox Network

1. Open VirtualBox.
2. Create an Internal Network named `LABNET`.
3. Ensure both VMs use this internal network.

## 2. Create the SERVER1 VM

- Name: `SERVER1`
- OS: Windows Server 2024
- RAM: 4 GB
- CPU: 2 vCPUs
- Storage: 40 GB
- Network Adapter: Internal Network `LABNET`

Install Windows Server 2024 and set a strong local Administrator password.

## 3. Configure Static IP on SERVER1

Set the following:

- IP Address: `192.168.20.50`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.20.1`
- Preferred DNS: `192.168.20.50`

## 4. Install AD DS and DNS

1. Open Server Manager.
2. Add Roles and Features.
3. Install:
   - Active Directory Domain Services
   - DNS Server
4. Promote the server to a domain controller.
5. Create a new forest with domain name `corp.local`.

Reboot when prompted.

## 5. Create the CLIENT1 VM

- Name: `CLIENT1`
- OS: Windows 10 Pro
- RAM: 4 GB
- CPU: 2 vCPUs
- Storage: 50 GB
- Network Adapter: Internal Network `LABNET`

Install Windows 10 Pro.

## 6. Configure Static IP on CLIENT1

Set the following:

- IP Address: `192.168.20.110`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.20.1`
- Preferred DNS: `192.168.20.50`

## 7. Join CLIENT1 to the Domain

1. Open System Properties.
2. Join the computer to `corp.local`.
3. Authenticate with domain admin credentials.
4. Reboot when prompted.

## 8. Create OUs, Users, and Groups

Create the following in Active Directory Users and Computers:

- OU: `north`
- Groups: `employees`, `managers`
- Users: `emp01`, `mgr01`

Assign users to their respective groups.

## 9. Configure File Shares on SERVER1

1. Create folders:
   - `C:\FILES\Employees`
   - `C:\FILES\Managers`
2. Share as:
   - `\\SERVER1\Employees`
   - `\\SERVER1\Managers`
3. Share and NTFS permissions:
   - `employees` group has Full Control to Employees share
   - `managers` group has Full Control to Managers share

## 10. Validate Functionality

- Ping between CLIENT1 and SERVER1
- Resolve `corp.local` using DNS
- Log in with domain accounts
- Test access to shares
- Verify access is denied for incorrect group
