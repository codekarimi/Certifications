# 🏢 Administer Active Directory Domain Services

> Microsoft Learn course completion showing I can deploy and manage AD DS domain controllers, administer users, groups, and OUs, enforce Group Policy and password policies, and harden Active Directory security.

![Provider](https://img.shields.io/badge/Provider-Microsoft%20Learn-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Level](https://img.shields.io/badge/Level-Intermediate-blue?style=for-the-badge)
![Product](https://img.shields.io/badge/Product-Active%20Directory-0A7E8C?style=for-the-badge)
![Date](https://img.shields.io/badge/Issued-September%202026-informational?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Earned-success?style=for-the-badge)

<!-- TODO: replace with the real image path in your repo -->
![Certificate](./images/administer-active-directory-domain-services.png)

---

## 📋 Certificate Details

| Field | Value |
|-------|-------|
| **Certificate Name** | Administer Active Directory Domain Services (learning path **AZ-1008**) |
| **Issuing Organization** | Microsoft (Microsoft Learn) |
| **Issue Date** | September 18, 2026 |
| **Credential ID** | E85BDBD59834B3F7 |
| **Certificate Type** | Course Completion (Learning Path, 5 modules) |
| **Validity** | No expiration listed on the completion credential |
| **Verification** | [Verify on Microsoft Learn](https://learn.microsoft.com/api/credentials/share/en-us/cliffordkarimi/E85BDBD59834B3F7?sharingId=74F8402F2ED5F3F) |
| **My Context** | IT Support |

> **📝 Transparency note:** This certificate is for **completing the AZ-1008 learning path**. It is **not** the separate [APL-1008 Applied Skills credential](https://learn.microsoft.com/en-us/credentials/applied-skills/administer-active-directory-domain-services/), which requires passing a timed, interactive assessment lab. The learning path is designed to prepare you for that assessment.

---

## 📚 What I Learned

The learning path has **five modules**: four instructional modules plus a **guided project** lab. The instructional modules are 🧠 **theory** (reading, knowledge checks, and short exercises). The guided project is 🛠️ **hands-on**, using two Windows Server 2022 Evaluation VMs in a virtualized environment.

**Prerequisites listed by Microsoft:** working knowledge of Windows Server and core networking technologies.

<!-- Trim the hands-on bullets to what you personally practiced. -->

### Module 1 — Deploy and Manage AD DS Domain Controllers

I learned how Active Directory is structured (forests, domains, sites) and how domain controllers fit into that topology. The module walked through deploying a DC, migrating one between sites, and managing the operations masters (FSMO roles).

**🧠 Key Concepts**
- What AD DS is: a directory service providing centralized authentication, authorization, and management
- Logical structure: forests, domains, and trusts
- Physical structure: sites, subnets, and how site mapping affects replication and client DC selection
- Domain controller roles, including the global catalog
- The five FSMO roles: Schema Master, Domain Naming Master, PDC Emulator, RID Master, Infrastructure Master
- Difference between **transferring** and **seizing** an operations master role
- Prerequisites for promoting a server: static IP, DNS, and the `AD-Domain-Services` role

**🛠️ Hands-on Skills Gained**
- I can install the AD DS role and promote a Windows Server to a domain controller
- I can create an AD site, map it to a subnet, and move a DC into it
- I can identify which server holds each FSMO role and transfer a role to another DC
- I can verify DC health and replication after changes

**Tools/Technologies:** Server Manager, Active Directory Sites and Services, PowerShell (`ActiveDirectory` module), `netdom`, `dcdiag`, `repadmin`

```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -DomainName "corp.contoso.com" -Credential (Get-Credential)

New-ADReplicationSite -Name "Nairobi"
New-ADReplicationSubnet -Name "10.20.0.0/24" -Site "Nairobi"
Move-ADDirectoryServer -Identity "DC02" -Site "Nairobi"

netdom query fsmo
Move-ADDirectoryServerOperationMasterRole -Identity "DC02" -OperationMasterRole PDCEmulator
```

---

### Module 2 — Create and Manage Active Directory Objects

This module covered day-to-day directory administration: organizing objects into OUs and creating users, groups, and computer accounts. It also covered bulk operations and recovering deleted objects.

**🧠 Key Concepts**
- Core objects: users, groups, computers, and organizational units (OUs)
- OU design for delegation and Group Policy targeting, versus containers such as `CN=Users`
- Group types (security vs. distribution) and scopes (domain local, global, universal)
- Privileged groups (e.g., Domain Admins) and why membership should be minimal
- Account lifecycle: create, disable, reset password, and offboard
- Bulk management of accounts using CSV import and PowerShell
- The AD Recycle Bin: enabling it and restoring deleted objects with attributes intact

**🛠️ Hands-on Skills Gained**
- I can build an OU structure and create users and groups, including adding members to privileged groups and to the **Protected Users** group
- I can bulk-create or modify user accounts from a CSV file
- I can find and manage disabled accounts and reset passwords (including forcing change at next logon)
- I can recover an accidentally deleted user or OU from the Recycle Bin

**Tools/Technologies:** Active Directory Users and Computers (ADUC), Active Directory Administrative Center (ADAC), PowerShell

```powershell
New-ADOrganizationalUnit -Name "Nairobi-Staff" -Path "DC=corp,DC=contoso,DC=com"
New-ADUser -Name "Jane Doe" -SamAccountName jdoe -Path "OU=Nairobi-Staff,DC=corp,DC=contoso,DC=com" `
  -AccountPassword (Read-Host -AsSecureString) -Enabled $true -ChangePasswordAtLogon $true

Import-Csv .\newhires.csv | ForEach-Object { New-ADUser -Name $_.Name -SamAccountName $_.Sam -Enabled $false }

Search-ADAccount -AccountDisabled -UsersOnly | Select Name, SamAccountName
Set-ADAccountPassword -Identity jdoe -Reset

Enable-ADOptionalFeature 'Recycle Bin Feature' -Scope ForestOrConfigurationSet -Target corp.contoso.com
Get-ADObject -Filter 'isDeleted -eq $true' -IncludeDeletedObjects | Restore-ADObject
```

---

### Module 3 — Create and Configure Group Policy Objects

This module focused on using Group Policy to centrally manage settings and enforce security, including domain-wide and fine-grained password policies.

**🧠 Key Concepts**
- What a GPO is, and the split between Computer Configuration and User Configuration
- GPO scope: linking to sites, domains, and OUs
- Processing order (LSDOU) and inheritance, including **Enforced** and **Block Inheritance**
- Security filtering to target GPOs at specific users or groups
- Domain-based GPOs stored in SYSVOL and replicated to all DCs
- The domain password policy: length, complexity, history, age, and account lockout
- **Fine-grained password policies (PSOs)** that apply stricter rules to specific users or groups
- Precedence when multiple PSOs apply to the same account

**🛠️ Hands-on Skills Gained**
- I can create a GPO, link it to an OU, and confirm which settings apply
- I can configure the domain password and lockout policy
- I can create a fine-grained password policy and apply it to a group such as IT admins
- I can troubleshoot policy application with `gpupdate` and `gpresult`

**Tools/Technologies:** Group Policy Management Console (GPMC), Group Policy Management Editor, ADAC (PSO management), PowerShell `GroupPolicy` module

```powershell
New-GPO -Name "Workstation-Baseline" | New-GPLink -Target "OU=Nairobi-Staff,DC=corp,DC=contoso,DC=com"

Get-ADDefaultDomainPasswordPolicy

New-ADFineGrainedPasswordPolicy -Name "Admins-PSO" -Precedence 10 -MinPasswordLength 14 `
  -ComplexityEnabled $true -LockoutThreshold 5 -LockoutDuration "00:30:00" -LockoutObservationWindow "00:30:00"
Add-ADFineGrainedPasswordPolicySubject -Identity "Admins-PSO" -Subjects "IT-Admins"
Get-ADUserResultantPasswordPolicy -Identity jdoe

gpupdate /force
gpresult /r
```

---

### Module 4 — Manage Security in Active Directory

This module covered protecting the directory itself: controlling who can do what, hardening authentication, and finding risky accounts.

**🧠 Key Concepts**
- User account rights and logon restrictions (allow/deny logon rights) to limit where accounts can sign in
- Delegation of control: granting scoped permissions (e.g., reset passwords on one OU) instead of adding people to Domain Admins
- Principle of least privilege and separation of admin and standard accounts
- The **Protected Users** group: no NTLM, no DES/RC4 for Kerberos, no cached credentials, and shorter TGT lifetime
- **Windows Defender Credential Guard**: isolating secrets using virtualization-based security
- Blocking NTLM authentication to reduce credential relay and pass-the-hash exposure
- Locating problematic accounts: inactive, disabled, and passwords set to never expire

**🛠️ Hands-on Skills Gained**
- I can delegate specific tasks to a helpdesk group at OU level
- I can add sensitive accounts to Protected Users and understand the impact on legacy apps
- I can find stale, inactive, and never-expiring accounts for cleanup
- I can describe how Credential Guard and NTLM restrictions reduce credential theft risk

**Tools/Technologies:** Delegation of Control Wizard, Protected Users group, Credential Guard, Group Policy (NTLM restriction settings), PowerShell

```powershell
Add-ADGroupMember -Identity "Protected Users" -Members jdoe
Get-ADGroupMember "Domain Admins" | Select Name, SamAccountName

Search-ADAccount -AccountInactive -TimeSpan 90.00:00:00 -UsersOnly | Select Name, LastLogonDate
Search-ADAccount -PasswordNeverExpires -UsersOnly | Select Name
```

---

### Module 5 — Guided Project: Administer Active Directory Domain Services 🛠️

The capstone lab. Following step-by-step instructions, I built an AD DS environment end to end on two Windows Server 2022 Evaluation VMs and worked through the four skilling areas that the Applied Skills assessment also uses.

**🛠️ Hands-on Skills Gained (project objectives)**
- **Configure domain controller operations:** deploy a DC, transfer a FSMO role, create a site and map it to a subnet, and move DCs between sites
- **Configure user management operations:** create OUs, users, and groups; perform bulk account changes; manage disabled users; reset passwords; recover items from the Recycle Bin
- **Manage password policies:** configure the domain policy and a fine-grained policy
- **Configure security settings:** delegate permissions, use Protected Users, and identify risky accounts

**Tools/Technologies:** Windows Server 2022 (Evaluation), Windows 10/11 host with virtualization, Server Manager, ADUC/ADAC, GPMC, PowerShell

---

## 🎯 Skills Acquired

### Technical Skills
**AD DS Deployment & Topology**
- [x] Install AD DS and promote domain controllers
- [x] Configure sites and subnets; move DCs between sites
- [x] Identify, transfer, and manage FSMO roles

**Identity & Object Management**
- [x] Design and manage OUs, users, groups, and computers
- [x] Perform bulk account operations with PowerShell and CSV
- [x] Manage disabled accounts, password resets, and Recycle Bin recovery

**Group Policy & Password Policy**
- [x] Create, link, and scope GPOs; understand inheritance and precedence
- [x] Configure domain and fine-grained password policies
- [x] Troubleshoot policy application with `gpupdate` and `gpresult`

**Security Hardening**
- [x] Delegate permissions using least privilege
- [x] Apply Protected Users, and describe Credential Guard and NTLM blocking
- [x] Audit for inactive and risky accounts

### Soft Skills
- [x] Following structured, step-by-step technical procedures
- [x] Thinking in terms of least privilege and blast radius
- [x] Documenting changes and verifying results after each step

---

## 🧪 Practical Applications

How I can apply this in IT Support and on my path toward Cloud Networking:

| Scenario | How this certificate helps |
|----------|---------------------------|
| **Locked-out or expired accounts** | Diagnose lockouts, reset passwords, and check whether a fine-grained policy applies to the user |
| **New hire / leaver processes** | Create accounts in the right OU and groups, then disable and clean up on departure |
| **"Policy isn't applying" tickets** | Check OU linking, inheritance, security filtering, and `gpresult` output |
| **Accidental deletion** | Restore users or OUs from the AD Recycle Bin without rebuilding them |
| **Access requests** | Recommend group-based access and scoped delegation rather than broad admin rights |
| **Security clean-ups** | Report on stale, disabled, and never-expiring accounts for review |
| **Hybrid identity and cloud** | Understand the on-prem directory that syncs to Microsoft Entra ID, which underpins cloud access and Azure networking permissions |
| **DNS/site issues** | Recognize how AD sites, subnets, and DNS affect where clients authenticate, which matters in multi-site and cloud-connected networks |

---

## 🔗 Related Certifications & Next Steps

**Prerequisites**
- Windows Server experience and core networking knowledge (IP addressing, DNS, DHCP)

**Recommended Next Steps**

| Priority | Credential | Why |
|----------|-----------|-----|
| 1 | **APL-1008: Administer Active Directory Domain Services** (Applied Skills) | Validates these skills in a timed, interactive lab; this learning path is its preparation |
| 2 | **AZ-900: Azure Fundamentals** | Cloud baseline if not already covered |
| 3 | **AZ-104: Azure Administrator Associate** | Core Azure administration, including identity, VNets, and hybrid connectivity |
| 4 | **SC-300: Identity and Access Administrator** | Extends AD skills into Microsoft Entra ID and hybrid identity |
| 5 | **AZ-700: Azure Network Engineer Associate** | Directly targets my Cloud Networking goal (VNets, DNS, VPN, ExpressRoute) |

**How this connects to my goal:** Most enterprise cloud networks still depend on Active Directory for authentication and DNS. Understanding sites, DCs, replication, and Group Policy helps me design and troubleshoot hybrid connectivity, such as VPN-connected domain controllers or cloud VMs joined to an on-premises domain.

---

## 📖 Study Resources

- [Learning path: Administer Active Directory Domain Services (AZ-1008)](https://learn.microsoft.com/en-us/training/paths/administer-active-directory-domain-services/)
  - [Deploy and manage AD DS domain controllers](https://learn.microsoft.com/en-us/training/modules/deploy-manage-active-directory-domain-services-domain-controllers/)
  - [Create and manage Active Directory objects](https://learn.microsoft.com/en-us/training/modules/create-manage-active-directory-objects/)
  - [Create and configure Group Policy Objects](https://learn.microsoft.com/en-us/training/modules/create-configure-group-policy-objects-active-directory/)
  - [Manage security in Active Directory](https://learn.microsoft.com/en-us/training/modules/manage-security-active-directory/)
  - [Guided project](https://learn.microsoft.com/en-us/training/modules/guided-project-administer-active-directory-domain-services/)
- [APL-1008 Applied Skills credential page](https://learn.microsoft.com/en-us/credentials/applied-skills/administer-active-directory-domain-services/)
- [APL-1008 assessment study guide](https://learn.microsoft.com/en-us/credentials/applied-skills/resources/study-guides/apl-1008)
- [ActiveDirectory PowerShell module reference](https://learn.microsoft.com/en-us/powershell/module/activedirectory/)
- [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/) for Windows Server evaluation ISOs to build a home lab

**Tip for the assessment lab:** it is an interactive, recorded lab, and Microsoft's page notes a 72-hour wait before you can relaunch it. Practice the PowerShell tasks above in a home lab first.

---

<sub>📅 README generated: September 19, 2026 · Part of my [`certificates`](../) repository</sub>
