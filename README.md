# Enterprise-IT-Support-Identity-Management-Simulation
# Objective:
Designed and deployed a simulated enterprise Helpdesk environment integrating Atlassian Jira Service Management (ITSM) with a local Windows Server Active Directory (AD) infrastructure. The project focuses on resolving simulated end-user tickets, managing Identity and Access Management (IAM), enforcing Role-Based Access Control (RBAC), and automating bulk user provisioning via PowerShell.
# Tools & Technologies Used:
- Ticketing & ITSM: Jira Service Management (Cloud)
- Infrastructure: Windows Server (Core), Active Directory Domain Services (AD DS)
- Administration: Remote Server Administration Tools (RSAT), Active Directory Users and Computers (ADUC)
- Automation: PowerShell, CSV Data Parsing
- Security & Compliance: NTFS File Permissions, ITIL Standard Operating Procedures (SOPs)
# Phase 1: Helpdesk Configuration & Ticket Lifecycle
- Jira ITSM Setup: Configured a centralized Service Desk portal for end-users to submit Service Requests and Incidents.
- SLA Management: Defined response and resolution Service Level Agreements (SLAs) to mirror corporate Helpdesk environments.
- Ticket Resolution Workflow: Established a strict documentation process where all Active Directory administrative actions were recorded as "Internal Notes" on Jira tickets for audit compliance.

# Phase 2: Identity & Access Management (User Lifecycle)
- Account Lockouts & Password Resets: Resolved simulated incidents by locating locked accounts in ADUC, verifying identity, unlocking accounts, and enforcing "User must change password at next logon" policies.
- Secure Employee Offboarding: Executed a compliance-driven termination SOP.
- Action: Disabled the AD account, randomized the password to prevent unauthorized access, stripped all Security Group memberships, and quarantined the user object to a dedicated "Disabled Users" Organizational Unit (OU).
- Audit: Mirrored the termination in Jira by suspending the user's SaaS access.

# Phase 3: Role-Based Access Control (RBAC) & File Security
- NTFS vs. Share Permissions: Configured a secure share.
- Security Groups: Created an AD Security Group (Marketing) and applied the Principle of Least Privilege.
- Execution: Granted "Full Control" at the Share level, but restricted NTFS Security permissions to "Read & Execute" strictly for the Security Group. Resolved user access tickets by managing group memberships rather than individual user permissions.

# Phase 4: PowerShell Automation (Bulk Onboarding)
- The Challenge: Automate the provisioning of multiple new hires based on an HR-provided .csv or .txt file.
- The Solution: Authored and executed a PowerShell script utilizing the New-ADUser cmdlet to parse the data file and sequentially generate user objects.

The Result: Automatically populated user attributes (Name, SamAccountName, Title, Department), placed them in the correct OU, and assigned a standardized, secure temporary password with forced reset upon first login.
