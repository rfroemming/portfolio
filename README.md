TECHNICAL PROJECT PORTFOLIO










Enterprise Infrastructure, Cloud Architecture, & Process Automation









Prepared by: Regis Froemming
Contact: froemming@gmail.com | (782) 234-3898
Professional Profiles: www.linkedin.com/in/regisfroemming  
Professional Portfolio Summary
As an IT Support and Infrastructure Specialist, my approach to technology centers on three core principles: eliminating operational waste through automation, hardening security perimeters via zero-trust baselines, and architecting seamless cloud migrations that ensure business continuity.
This portfolio details real-world, enterprise-level projects designed and executed to modernize infrastructure and solve complex operational bottlenecks. Rather than just managing systems, I focus on engineering proactive solutions that reduce support ticket volumes and scale efficiently with organization growth.
Core Areas of Expertise Demonstrated in this Portfolio:
Unified Endpoint Management (UEM) & Cloud Identity: Designing, packaging, and deploying Microsoft Intune MDM/MAM architectures and executing native Microsoft Entra ID migrations across desktop and mobile ecosystems (iOS/Android).
Hybrid Identity & Infrastructure Migrations: Managing complex, cross-domain Active Directory object mergers, executing cryptographic cloud-identity hard-matching via Azure AD Connect, and implementing seamless local user profile transitions.
Infrastructure Automation & Process Optimization: Engineering automated, cloud-based workflows utilizing the Microsoft 365 stack (Power Automate, SharePoint Online) and relational APIs to eradicate hours of repetitive manual technical labor.
Advanced Network Diagnostics & Optimization: Troubleshooting and permanently remediating chronic Layer 2/Layer 3 networking failures, re-architecting firewall policies, and performing high-density Radio Frequency (RF) wireless tuning.

Technical Project Case Study: Automated Backup Monitoring & Incident Response Portal
Project Overview
Project Title: Cloud-Driven Automation & Centralized Backup Monitoring System
Role: Tier 1, CSC - Customer Service Consultant
Environment: Microsoft Power Automate, Microsoft Lists / SharePoint, Zendesk API Integration, Exchange Online (Shared Mailboxes)
Scope: Designing and deploying an automated workflow to replace a multi-hour manual verification process, centralizing multi-region backup alerts, and stream-lining incident ticket creation.
The Challenge (Situation)
The technical support team was responsible for executing daily manual compliance verifications on data backup integrity across three distinct geographical regions. Hardware and cloud endpoints were configured to broadcast individual email status notifications directly to a central shared mailbox, resulting in techs manually parsing through hundreds of alerts daily.
The legacy process required an average of 3 aggregate hours of tech work per day to manually cross-reference alerts against an Excel spreadsheet. When a backup failure was discovered, a technician had to manually extract the error logs, navigate to Zendesk, open a support ticket, paste the logs, and then manually write the ticket ID back into the spreadsheet tracking list. This process was highly inefficient, repetitive, and prone to human error.
Core Technical Toolkit
Data Layout & UI: Microsoft Lists / SharePoint Online
Workflow Orchestration: Power Automate (Cloud Flows)
Ticketing & Communications: Zendesk API Email Integration, Exchange Online
Resource Scheduling: Office 365 Outlook Calendar Automation
Step-by-Step Execution (Action)
Phase 1: Conceptual Design & Database Staging
Centralized Schema Architecture: Developed a unified data repository within Microsoft Lists to replace fragmented legacy trackers. Structured columns to categorize clients, backup software types (e.g., Veeam, Datto, Cloudberry), execution schedules, operational health statuses, and dynamic fields for ticketing system mapping.
Technician Allocation Automation: Configured an automated morning routine that polls team calendars to dynamically identify scheduled support shifts and systematically assign daily regional inspection oversight to specific available technicians.
Phase 2: Power Automate Scripting & Log Parsing
Mailbox Ingestion Flow: Built a background automation trigger within Power Automate to scan the inbound shared backup mailbox every morning.
String Parsing Logic: Configured parsing parameters to extract plain-text contents from hundreds of incoming device alerts, automatically mapping device names and execution statuses (e.g., Success, Warning, Failed) straight into corresponding database records.
UI Centralization: Consolidated all individual email data into a single, real-time, easy-to-read dashboard, eliminating the need for technicians to hunt through raw mailbox folders.
Phase 3: Automated Incident Management Loop
Toggle-Triggered Ticket Generation: Integrated custom interactive elements directly inside the Microsoft List interface. Enforced a logic flow where if a backup fails, a technician simply flips a "Create a Ticket" toggle switch.
API Payload Execution: Programmed a secondary Power Automate flow that listens for that toggle update. It compiles the exact error payload—extracting the faulty device details and structural body text from the original log email—and shoots an automated API email directly to the Zendesk processing endpoint.
Dynamic Webhook Confirmation: Configured the automated loop to listen for Zendesk's creation receipt. The moment Zendesk logs the ticket, the flow writes the exact numeric incident ticket ID right back into the active database record automatically, facilitating immediate follow-up capabilities for the team.
Project Results (Impact)
90%+ Reduction in Operational Waste: Dropped the manual verification requirement from 3 hours per day of engineering time down to a brief, automated dashboard review, saving roughly 750 hours of technical labor annually.
Drastic Acceleration in MTTR (Mean Time to Resolution): Reduced ticket generation timelines from minutes of manual copy-pasting down to a single-click toggle, allowing high-priority backup failures to hit remediation pipelines instantly.
Elimination of Human Error: Standardized data entry by ensuring no failed backup jobs are accidentally skipped or missed in full email folders, safeguarding client business continuity and strict SLA compliance.

2. Technical Project Case Study: Domain Merger & Hybrid Identity Migration
Project Overview
Project Title: Cross-Domain Identity Migration & Hybrid Microsoft 365 Integration
Role: Tier 2 / Infrastructure Support Specialist
Environment: Active Directory Domain Services (AD DS), Azure AD Connect, Microsoft 365 (MSOnline), ForensiT Transwiz, Duo Security, Group Policy (GPO)
Scope: Migrating corporate identities, local workstation profiles, and remote desktop user profiles from a legacy acquired domain to a centralized parent firm domain, while preserving cloud-hosted email access and data integrity.
The Challenge (Situation)
Following an organizational merger, users and assets on a legacy source domain needed to be consolidated into a centralized parent firm domain. The primary technical challenges were:
Identity Matching: Moving users to the new domain without destroying or duplicating their existing Microsoft 365 cloud mailboxes and licenses.
Profile Continuity: Ensuring users did not lose local data, browser settings, or application configurations on their local workstations and Remote Desktop Services (RDS) environments.
Security Baseline Preservation: Maintaining Multi-Factor Authentication (MFA) via Duo and re-establishing BitLocker drive encryption under the new domain structure.
Core Technical Toolkit
Directory Synchronization: Azure AD Connect (Start-ADSyncSyncCycle)
Cloud Identity Management: PowerShell MSOnline Module (Connect-MsolService, Set-MsolUser)
Profile Migration Utilities: ForensiT Transwiz Deployment Wizard
Security & Authentication: Duo Security Console, Windows BitLocker Drive Encryption
Step-by-Step Execution (Action)
Phase 1: Hybrid Cloud Identity Hard-Matching
To prevent cloud mailbox duplication, a manual cryptographic hard-match was executed to bridge the new on-premises Active Directory accounts with existing Microsoft 365 objects.
Cloud Disconnection: Isolated the source user objects from Azure AD Connect sync to temporarily convert them to cloud-only objects, ensuring the accounts remained intact for restoration.
ImmutableID Injection: Created the corresponding new user objects in the target firm domain. Used PowerShell to extract the new on-premises GUID, converted it to a Base64 string, and mapped it directly to the cloud user's ImmutableId attribute:
	$ADUser = "TargetNewUser"
$365User = "user@company.com"
$guid = (Get-ADUser $ADUser).Objectguid
$immutableID = [system.convert]::ToBase64String($guid.tobytearray())
Set-MsolUser -UserPrincipalName $365User -ImmutableId $immutableID
Directory Re-Synchronization: Forced sequential delta sync cycles via Azure AD Connect to finalize the hard-match, seamlessly binding the new local AD account to the existing cloud mailbox.

Phase 2: Remote Desktop (RDS) & Local Profile Migration
To minimize post-migration ticket volumes, user desktop environments were programmatically migrated to prevent data loss.

RDS Server Profiles Utilized ForensiT Transwiz on production remote desktop servers to compress and back up user profiles to temporary local storage. Restored the data by targeting the new domain and user accounts, leveraging profile merging capabilities while intentionally holding the RDS host on its original domain until the final infrastructure cutover.
Endpoint Machine Migration: Deployed Transwiz to local workstations to back up user profiles. Executed the built-in domain join functionality within the wizard to simultaneously bind the physical workstation to the new target domain and map the restored profile to the new domain credentials.
Phase 3: Network Environment & Security Posture Finalization
Group Policy & Drive Mapping: Provisioned migrated users into target security groups (e.g., login script and drive-mapping groups) to automate network resource delivery.
Legacy Resource Cleanup: Flushed stale environment mappings on client machines using `net use * /delete` and migrated legacy user shares to the centralized file server infrastructure.
MFA & Compliance Realignment: Re-synchronized and provisioned user hardware tokens/mobile devices within the Duo Security console. Decrypted legacy volumes and cycled BitLocker drive encryption to escrow fresh recovery keys into the new target domain's Active Directory Organizational Units (OUs).
Project Results (Impact)
Zero Cloud Data Loss: Successfully migrated enterprise mailboxes and cloud identities without a single instance of data loss or account duplication.
Seamless User Experience: Maintained a familiar desktop environment for end-users across both physical workstations and virtualized RDS hosts, resulting in an exceptionally low post-migration support queue.
Maintained Compliance Baseline: Ensured that MFA protections and BitLocker drive encryption standards remained continuously enforced throughout the domain transition lifecycle.



3. Technical Project Case Study: Legacy AD to Microsoft Entra ID Cloud Endpoint & Mobile Management (MDM) Transformation
Project Overview
Project Title: Enterprise Legacy Infrastructure Modernization & Unified Endpoint Management (UEM) Rollout
Role: Tier 2 -  Support Specialist
Environment: Microsoft Entra ID, Microsoft Intune (MDM/MAM), Android Enterprise, Apple iOS User Enrollment, ForensiT Profwiz, PowerShell, Endpoint Security
Scope: Decommissioning legacy on-premises domain dependencies, migrating 60+ physical corporate endpoints, and establishing a secure, cross-platform Mobile Device Management framework for corporate and BYOD mobile devices.
The Challenge (Situation)
The organization sought to eliminate reliance on aging on-premises domain infrastructure and modernize its absolute security perimeter. The primary challenges were twofold:
Workstation Transition: Moving 60+ production workstations seamlessly to Microsoft Entra ID and Intune, replacing legacy Group Policies (GPOs) with cloud configuration policies while preserving existing localized user profiles and app data.
Unmanaged Mobile Risk: Safeguarding enterprise data accessed via employee mobile devices (iOS and Android). Without an active MDM system, the company faced threats regarding unprotected data access, potential data leaks via copy/paste actions to personal applications, and the inability to securely wipe corporate repositories from lost or stolen devices.
Core Technical Toolkit
Cloud Identity & MDM: Microsoft Entra ID Admin Center, Microsoft Intune
Authentication & Access: Temporary Access Passwords (TAP), Conditional Access Frameworks
Mobile Frameworks: Android Enterprise (Work Profiles), Apple iOS User-Driven Enrollment via Company Portal
Profile Migration Utilities: ForensiT User Profile Wizard (Profwiz)
Step-by-Step Execution (Action)
Phase 1: Workstation Migration & Cloud Identity Binding
Cloud Group & TAP Staging: Pre-staged targeted user accounts into dedicated Intune groups and generated time-limited, 60-minute Temporary Access Passwords (TAP) to facilitate efficient enrollment without interrupting users with interactive MFA prompts.
On-Premises Severance & Entra Join: Logged into endpoints via an isolated local administrator account, disconnected machines from the legacy on-premises Active Directory network, and executed an explicit Microsoft Entra ID Join.
Profile Realignment: Leveraged the ForensiT User Profile Wizard to programmatically map and merge the legacy local domain user profile path directly into the newly generated cloud-native Entra ID user space, preserving all user personalization and web credentials.
Phase 2: Building the Intune Policy & Application Architecture
To establish parity with legacy on-premises structures, an enterprise-grade ecosystem of device configurations, compliance filters, and application bundles was engineered:
App Lifecycle & Deployment Management: Packaged and targeted core software configurations to silently install upon enrollment, including foundational productivity utilities (Microsoft 365 Apps, Teams, Outlook, Adobe Reader), network security agents (WatchGuard Agent, Mobile VPN with SSL), and network printer objects.
Configuration & Security Hardening: Pushed device profiles enforcing Single Sign-On (SSO), automated OneDrive syncing, and browser baseline optimizations. To enforce strict zero-trust parameters, deployed an Account Protection policy via an Intune profile to programmatically strip standard corporate users from the local Administrators group.
Device Compliance Baselines: Constructed rigid compliance metrics mandating full-volume BitLocker drive encryption, minimum OS patch version rules, and targeted guardrails to automatically isolate non-compliant hardware from reaching corporate data stores.
Phase 3: Implementing Secure Cross-Platform Mobile Management (MDM)
To manage mobile data containers without violating employee personal privacy, designed and documented a user-driven onboarding structure tailored to each platform's architectural requirements:
iOS Enrollment Strategy (iOS 13.0+): Implemented a User-Driven Enrollment workflow through the Microsoft Intune Company Portal app. This enforced sandboxed boundaries where corporate data is encrypted, while keeping personal apps, personal Apple IDs, and private data completely isolated and invisible to IT administration.
Android Enterprise Architecture (Android 8.0+): Standardized on the Android Enterprise Work Profile deployment model. Upon enrollment, the system automatically creates a securely separated, encrypted workspace partition on the OS (indicated by the briefcase icon), separating personal applications from business communication channels.
Data Leakage Prevention (MAM Controls): Engineered data protection boundaries that globally block copy/paste functionality between corporate-managed secure apps (such as Outlook, Teams, and SharePoint) and personal apps. Enabled Selective Wipe functionalities, allowing the instantaneous, remote destruction of corporate data strings from lost, stolen, or decommissioned mobile devices without impacting personal storage.
Standard Operating Procedure (SOP) Creation: Authored a clear, visual, step-by-step end-user onboarding manual detailing the Company Portal configuration flow. This minimized support tickets by guiding users through the work profile configuration, required workspace application downloads, and device health verifications.
Project Results (Impact)
Unified Endpoint Architecture Success: Successfully consolidated 60+ physical workstations and a cross-platform fleet of mobile devices into a single, centralized pane of glass within Microsoft Intune.
Hardened Data Protection (MAM/MDM): Eliminated corporate data exposure risks by completely sandboxing business communications on mobile devices, enforcing encryption baselines, and blocking unauthorized data transfers to personal profiles.
Enforced Global Least Privilege & Compliance: Closed historic infrastructure vulnerabilities by establishing strict non-admin privilege standards across all workstations while automating zero-touch app and patch delivery networks.


4. Technical Project Case Study: Multi-Floor Enterprise Wireless Network Optimization & Advanced Remediation
Project Overview
Project Title: High-Density Enterprise Wireless Infrastructure Stabilization & Layer 2/3 Re-Engineering
Role: Lead Network Infrastructure Consultant
Environment: UniFi Wireless Architecture, HPE Legacy Switching, Enterprise Firewalls, Windows Server (DHCP/DNS), Advanced RF Diagnostic Suites
Scope: Performing root-cause analysis and full-scale technical remediation of a chronic, multi-month wireless performance degradation affecting an enterprise multi-floor campus network.
The Challenge (Situation)
An enterprise client was experiencing systemic, long-term wireless network unreliability, high latency, packet loss, and severe throughput drops. Multiple previous technicians had attempted to remediate the environment over several months without success.
The infrastructure suffered from undocumented structural flaws across the wireless spectrum, underlying Layer 2 segmentation issues, and firewall routing ambiguities that severely degraded the user experience for both staff and guests.
Core Technical Toolkit
Wireless Management: UniFi Network Controller Infrastructure
Hardware Layer: UniFi U6-Lite Access Points, HPE 1950 & 1820 Managed Switches
Protocols & RF Control: 802.11r (Fast Roaming), Minimum Data Rate Tuning, Co-Channel Interference Mitigation
Network Core Services: Windows Server DHCP, Layer 3 Firewall Routing, VLAN Segmentation
Root-Cause Analysis & Engineering Remediation (Action)
The stabilization project was broken down into four distinct structural phases to isolate and repair legacy misconfigurations.
Phase 1: Layer 3 Routing & Firewall Remediation
VPN Address Overlap Resolution: Discovered a critical architectural conflict where a Branch-to-Office Site-to-Site VPN advertised an address space that directly overlapped with the local internal network. This created routing ambiguity and asymmetric traffic loops. Completely re-engineered the firewall policies and disabled the conflicting overlapping advertisements to instantly stabilize internal network behavior.
Network Traffic Segmentation: Identified a flat wireless network design where corporate staff traffic was combined on the same virtual network as legacy machinery and internal systems. Engineered a dedicated wireless VLAN (192.168.3.0/24), provisioned a fresh DHCP scope on the core domain controller, and established isolated firewall rules to enforce strict security zoning and traffic visibility.
Phase 2: RF Spectrum & Channel Optimization
Airtime Contention Remediation: Diagnosed that legacy 2.4 GHz client devices and modern 5 GHz devices were bundled on the same SSIDs, triggering high airtime contention and dropping transmission rates for all users. Disabled the 2.4 GHz radio band entirely on Primary Staff and Guest SSIDs. Created an isolated, dedicated legacy SSID mapped to targeted access points to house older 2.4 GHz hardware safely away from production traffic.
Channel Width & Overlap Tuning: Discovered access points mistakenly operating on wide 80 MHz channel widths in a high-density, multi-floor environment. This consumed scarce contiguous channels, causing massive co-channel interference and cross-floor airtime congestion. Scaled down channel footprints, implemented a meticulous channel reuse plan, and manually dialed down transmit power levels to LOW on all managed APs to completely eliminate overlapping RF boundaries and fix "sticky client" behavior.
Phase 3: Advanced High-Capacity & Roaming Adjustments
Enforcing Roaming Thresholds: Implemented strict roaming optimization policies, setting a minimum 5 GHz RSSI roaming threshold of -65 dBm. This programmatically forces mobile endpoints to roam gracefully to a closer access point before packet retries and latency spike.
Airtime Fairness Tuning: Enabled advanced high-capacity tuning. Raised the Minimum Data Rate threshold on the 5 GHz band to 12 Mbps / 24 Mbps and enforced a Multicast and Broadcast Blocker. This purged low-rate management frames from clogging wireless cells, freeing up massive blocks of raw airtime.
Phase 4: Infrastructure Auditing & Device Adoption
Orphaned Access Point Recovery: Discovered multiple rogue/orphaned UniFi access points across all floors that were actively broadcasting corporate SSIDs but had completely lost their trust relationship with the central UniFi controller. Because they were unmanaged, they could not receive central channel distribution adjustments or firmware updates. Initiated physical audits, traced internal legacy HPE switches (HPE 1950 / 1820), and prepared a physical adoption workflow using remote PoE reset injectors to reclaim central management authority.
Project Results (Impact)
Resolved a Multi-Month Network Crisis: Successfully diagnosed and permanently resolved a chronic infrastructure failure that had eluded multiple engineering groups for months.
Drastic Performance Amplification: Eliminated packet drops, reduced latency, and normalized deterministic throughput across all floors by purging co-channel interference and optimizing airtime utilization.
Hardened Security & Zero-Trust Posture: Moved the entire corporate wireless footprint from a risky, flat broadcast domain into a highly segmented, firewall-audited VLAN structure.

