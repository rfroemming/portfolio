# Technical Projects Portfolio
## Enterprise Infrastructure, Cloud Architecture, & Process Automation

Regis Froemming  

---

## 🎯 Summary
As an IT Support and Infrastructure Specialist, my approach to technology centers on three core principles: **eliminating operational waste through automation**, **hardening security perimeters via zero-trust baselines**, and **architecting seamless cloud migrations** that ensure business continuity. 
This portfolio details real-world, enterprise-level projects designed and executed to modernize infrastructure and solve complex operational bottlenecks. Rather than just managing systems, I focus on engineering proactive solutions that reduce support ticket volumes and scale efficiently with organizational growth.

### Core Areas of Expertise Demonstrated in this Portfolio:
* **Workflow Automation:** Building smart, cloud-based workflows (using tools like Power Automate and SharePoint) that connect different business apps and eliminate hours of repetitive manual data entry.
* **User & Identity Migrations:** Moving user profiles and data seamlessly during company mergers, linking local corporate accounts safely to cloud systems, and ensuring employees don't lose their desktop settings or data.
* **Cloud Identity & Device Management:** Setting up and managing company devices remotely using Microsoft Intune and moving physical computers fully into cloud-managed environments (Microsoft Entra ID).
* **Network & Wireless Optimization:** Fixing deep-rooted network lag and connectivity issues, updating corporate firewall security rules, and fine-tuning multi-floor office Wi-Fi networks for maximum speed and stability.

---

## 📂 Table of Contents
1. [Case Study 1: Automated Backup Monitoring & Incident Response Portal](#1-technical-project-case-study-automated-backup-monitoring--incident-response-portal)
2. [Case Study 2: Domain Merger & Hybrid Identity Migration](#2-technical-project-case-study-domain-merger--hybrid-identity-migration)
3. [Case Study 3: Legacy AD to Microsoft Entra ID Cloud Endpoint Transformation](#3-technical-project-case-study-legacy-ad-to-microsoft-entra-id-cloud-endpoint-transformation)
4. [Case Study 4: Multi-Floor Enterprise Wireless Network Optimization & Advanced Remediation](#4-technical-project-case-study-multi-floor-enterprise-wireless-network-optimization--advanced-remediation)

---

## 1. Automated Backup Monitoring & Incident Response Portal

### Project Overview
* **Project Title:** Cloud-Driven Automation & Centralized Backup Monitoring System
* **Role:** Tier 1, CSC - Customer Service Consultant
* **Environment:** Microsoft Power Automate, Microsoft Lists / SharePoint, Zendesk API Integration, Exchange Online (Shared Mailboxes)
* **Scope:** Designing and deploying an automated workflow to replace a multi-hour manual verification process, centralizing multi-region backup alerts, and stream-lining incident
ticket creation.

### The Challenge (Situation)
The technical support team was responsible for executing daily manual compliance verifications on data backup integrity across three distinct geographical regions. Hardware and cloud endpoints were configured to broadcast individual email status notifications directly to a central shared mailbox, resulting in techs manually parsing through hundreds of alerts daily.
The legacy process required an average of 3 aggregate hours of tech work per day to manually cross-reference alerts against an Excel spreadsheet. When a backup failure was discovered, a technician had to manually extract the error logs, navigate to Zendesk, open a support ticket, paste the logs, and then manually write the ticket ID back into the spreadsheet tracking list. This
process was highly inefficient, repetitive, and prone to human error.

### Core Technical Toolkit
* **Data Layout & UI:** Microsoft Lists / SharePoint Online
* **Workflow Orchestration:** Power Automate (Cloud Flows)
* **Ticketing & Communications:** Zendesk API Email Integration, Exchange Online
* **Resource Scheduling:** Office 365 Outlook Calendar Automation

### Step-by-Step Execution (Action)

#### Phase 1: Conceptual Design & Database Staging
1. **Centralized Schema Architecture:** Developed a unified data repository within Microsoft Lists to replace fragmented legacy trackers. Structured columns to categorize clients, backup software types (e.g., Veeam, Datto, Cloudberry), execution schedules, operational health statuses, and dynamic fields for ticketing system mapping.
2. **Technician Allocation Automation:** Configured an automated morning routine that polls team calendars to dynamically identify scheduled support shifts and systematically assign daily regional inspection oversight to specific available technicians.

#### Phase 2: Power Automate Scripting & Log Parsing
1. **Mailbox Ingestion Flow:** Built a background automation trigger within Power Automate to scan the inbound shared backup mailbox every morning.
2. **String Parsing Logic:** Configured parsing parameters to extract plain-text contents from hundreds of incoming device alerts, automatically mapping device names and execution statuses (e.g., Success, Warning, Failed) straight into corresponding database records.
3. **UI Centralization:** Consolidated all individual email data into a single, real-time, easy-to-read dashboard, eliminating the need for technicians to hunt through raw mailbox folders.

#### Phase 3: Automated Incident Management Loop
1. **Toggle-Triggered Ticket Generation:** Integrated custom interactive elements directly inside the Microsoft List interface. Enforced a logic flow where if a backup fails, a technician simply flips a "Create a Ticket" toggle switch.
2. **API Payload Execution:** Programmed a secondary Power Automate flow that listens for that toggle update. It compiles the exact error payload, extracting the faulty device details and structural body text from the original log email, and shoots an automated API email directly to the Zendesk processing endpoint.
3. **Dynamic Webhook Confirmation:** Configured the automated loop to listen for Zendesk's creation receipt. The moment Zendesk logs the ticket, the flow writes the exact numeric incident ticket ID right back into the active database record automatically, facilitating immediate follow-up capabilities for the team.

### Project Results (Impact)
* **90%+ Reduction in Operational Waste:** Dropped the manual verification requirement from 3 hours per day of engineering time down to a brief, automated dashboard review, saving roughly 750 hours of technical labor annually.
* **Drastic Acceleration in MTTR (Mean Time to Resolution):** Reduced ticket generation timelines from minutes of manual copy-pasting down to a single-click toggle, allowing high-priority backup failures to hit remediation pipelines instantly.
* **Elimination of Human Error:** Standardized data entry by ensuring no failed backup jobs are accidentally skipped or missed in full email folders, safeguarding client business continuity and strict SLA compliance.

---
## 2. Domain Merger & Hybrid Identity Migration

### Project Overview
* **Project Title:** Cross-Domain Identity Migration & Hybrid Microsoft 365 Integration
* **Role:* Tier 2 / Infrastructure Support Specialist
* **Environment:** Active Directory Domain Services (AD DS), Azure AD Connect, Microsoft 365, ForensiT Transwiz, Duo Security, Group Policy (GPO)
* **Scope:** Migrating corporate identities, local workstation profiles, and remote desktop user profiles from a legacy acquired domain to a centralized parent domain, while preserving cloud-hosted email access and data integrity.

### The Challenge (Situation)
Following an organizational merger, users and assets on a legacy source domain needed to be consolidated into a centralized parent domain. The primary technical challenges were:
1. **Identity Matching:** Moving users to the new domain without destroying or duplicating their existing Microsoft 365 cloud mailboxes and licenses.
2. **Profile Continuity:** Ensuring users did not lose local data, browser settings, or application configurations on their local workstations and Remote Desktop Services (RDS) environments.
3. **Security Baseline Preservation:** Maintaining Multi-Factor Authentication (MFA) via Duo (Complete Identity Security & MFA Solutions) and re-establishing BitLocker drive encryption under the new domain structure.

### Core Technical Toolkit
* **Directory Synchronization:** Azure AD Connect (Start-ADSyncSyncCycle)
* **Cloud Identity Management:** PowerShell MSOnline Module (Connect-MsolService, Set-MsolUser)
* **Profile Migration Utilities:** ForensiT Transwiz Deployment Wizard
* **Security & Authentication:** Duo Security Console, Windows BitLocker Drive Encryption

### Step-by-Step Execution (Action)
#### Phase 1: Hybrid Cloud Identity Hard-Matching
To prevent cloud mailbox duplication, a manual cryptographic hard-match was executed to bridge the new on-premises Active Directory accounts with existing Microsoft 365 objects.
1. **Cloud Disconnection:** Isolated the source user objects from Azure AD Connect sync to temporarily convert them to cloud-only objects, ensuring the accounts remained intact for restoration.
2. **ImmutableID Injection:** Created the corresponding new user objects in the target domain. Used PowerShell to extract the new on-premises GUID, converted it to a Base64 string, and mapped it directly to the cloud user's ImmutableId attribute:
   ```
    $ADUser = "TargetNewUser"
    $365User = "user@company.com"
    $guid = (Get-ADUser $ADUser).Objectguid
    $immutableID = [system.convert]::ToBase64String($guid.tobytearray())
    Set-MsolUser -UserPrincipalName $365User -ImmutableId $immutableID
   ```
4. **Directory Re-Synchronization:** Forced sequential delta sync cycles via Azure AD Connect to finalize the hard-match, seamlessly binding the new local AD account to the existing cloud mailbox.

#### Phase 2: Remote Desktop (RDS) & Local Profile Migration
To minimize post-migration ticket volumes, user desktop environments were programmatically migrated to prevent data loss.
1. **RDS Server Profiles** Utilized ForensiT Transwiz on production remote desktop servers to compress and back up user profiles to temporary local storage. Restored the data by targeting the new domain and user accounts, leveraging profile merging capabilities while intentionally holding the RDS host on its original domain until the final infrastructure cutover.
2. **Endpoint Machine Migration:** Deployed Transwiz to local workstations to back up user profiles. Executed the built-in domain join functionality within the wizard to simultaneously bind the physical workstation to the new target domain and map the restored profile to the new domain credentials.

#### Phase 3: Network Environment & Security Posture Finalization
1. **Group Policy & Drive Mapping:** Provisioned migrated users into target security groups (e.g., login script and drive-mapping groups) to automate network resource delivery.
2. **Legacy Resource Cleanup:** Flushed stale environment mappings on client machines using `net use * /delete` and migrated legacy user shares to the centralized file server infrastructure.
3. **MFA & Compliance Realignment:** Re-synchronized and provisioned user hardware tokens/mobile devices within the Duo Security console. Decrypted legacy volumes and cycled BitLocker drive encryption to escrow fresh recovery keys into the new target domain's Active Directory Organizational Units (OUs).

### Project Results (Impact)
* **Zero Cloud Data Loss:** Successfully migrated enterprise mailboxes and cloud identities without a single instance of data loss or account duplication.
* **Seamless User Experience:** Maintained a familiar desktop environment for end-users across both physical workstations and virtualized RDS hosts, resulting in an exceptionally low post-migration support queue.
* **Maintained Compliance Baseline:** Ensured that MFA protections and BitLocker drive encryption standards remained continuously enforced throughout the domain transition lifecycle.

---
## 3. Legacy AD to Microsoft Entra ID Cloud Endpoint Transformation
### Project Overview
* **Project Title:** Legacy Active Directory to Microsoft Entra ID Cloud Endpoint Transformation
* **Role:** Tier 2 / Infrastructure & Support Specialist
* **Environment:** Microsoft Entra ID, Microsoft Intune (MDM), ForensiT Profwiz, Windows 10/11, PowerShell, Endpoint Security
* **Scope:** Decommissioning legacy on-premises domain dependencies and migrating 60+ physical corporate endpoints into a modern, cloud-native identity framework managed entirely via MDM profiles.

### The Challenge (Situation)
The organization sought to modernize its device management strategy by eliminating reliance on an aging on-premises domain infrastructure. Endpoints needed to be transitioned to a cloud-native workplace framework using Microsoft Entra ID and Intune. The core operational challenge was executing this migration seamlessly on live production machines, preserving local user profiles, data, and application states, while engineering a comprehensive suite of cloud-delivered app deployments, configuration policies, and zero-trust compliance baselines to replace legacy Group Policies (GPOs).

### Core Technical Toolkit
* **Cloud Identity & MDM:** Microsoft Entra ID Admin Center, Microsoft Intune
* **Authentication Systems:** Temporary Access Passwords (TAP), Multi-Factor Authentication (MFA) bypass protocols
* **Profile Migration Utilities:** ForensiT User Profile Wizard (Profwiz)
* **Endpoint Architecture Modules:** Intune Win32 App Packaging, Device Configuration Profiles, Device Compliance Policies

### Step-by-Step Execution (Action)
#### Phase 1: Pre-Migration Data Scoping & Identity Provisioning
To minimize the impact of moving from a local domain account to a cloud identity, exhaustive pre-flight configurations were run on each endpoint.
1. **Cloud Group Staging:** Pre-staged targeted user accounts into dedicated Intune deployment groups within the cloud console to automate downstream policy assignments.
2. **State Protection:** Confirmed that cloud-backup sync engines (OneDrive) were fully operational, capturing the user's Desktop, Documents, and Pictures folders. Manually exported local browser components (Chrome bookmarks) and secured credential-manager tokens (1Password extension keys).
3. **Authentication Bypass Staging:** Generated time-limited, 60-minute Temporary Access Passwords (TAP) for users within the Entra ID portal. This allowed technical enrollment to proceed efficiently without requiring the user's explicit interactive MFA prompts during device configuration.

#### Phase 2: Domain Disconnection and Cloud Entra ID Joining
1. **On-Premises Severance:** Logged into endpoints via an isolated local administrator account and completely disconnected the machine from the legacy on-premises Active Directory network.
2. **Cloud Identity Binding:** Following a system reboot, navigated to the modern workplace enrollment terminal and selected _Join this device to Azure Active Directory_. Bound the hardware directly to the user's cloud corporate identity using the pre-staged TAP token.
3. **Resolution of Provisioning Blockers:** Remediated enrollment anomalies (such as MDM Error Code 8018000a, indicating a device pre-existing enrollment conflict) by running targeted cleanup scripts via PowerShell to purge stale hardware registrations.
4. **Profile Realignment:** Leveraged the ForensiT User Profile Wizard to programmatically map and merge the legacy local domain user profile path directly into the newly generated cloud-native Entra ID user space, preserving all app settings, backgrounds, and personalizations.

#### Phase 3: Intune Policy Infrastructure & App Deployment
To establish parity with (and exceed) legacy on-premises structures, an enterprise-grade ecosystem of device configurations, compliance filters, and applications was built out from scratch in Microsoft Intune:
* **App Lifecycle & Deployment Management:** Packaged and targeted core software configurations to silently install upon Entra enrollment. This included foundational productivity tools (Microsoft 365 Apps for Enterprise, Microsoft Teams, Outlook Classic, Adobe Acrobat Reader DC), secure connectivity agents (WatchGuard Agent, WatchGuard Mobile VPN with SSL), device administration helpers (Company Portal), hardware utilities (Dymo Label Software), and print infrastructure objects (Ricoh Downstairs and Upstairs network printers).
* **Device Configuration Profiles:** Engineered and applied automated workspace settings, including _Silently Sign In OneDrive_ , _Enable Auto Update for Google Chrome_ , _Google
Chrome SSO_ , _Default homepage_ , _Bookmarks_ , and _Teams auto start_.
* **Security & Least Privilege Hardening:** Enforced Attack Surface Reduction ( ASR - Secure Score ) and baseline firewalls. To correct the default Entra behavior that grants local admin rights to the enrolling user, deployed the Remove users from local administrators group policy via an Account Protection profile to strictly maintain a least-privilege stance. Blocked manual MDM detachment via the Block Unenrollment mechanism.
* **Device Compliance Baselines:** Designed conditional access safety nets across platforms. Constructed the BitLocker policy to mandate full-volume drive encryption on Windows endpoints, the Minimun OS Version rule to block unpatched devices from accessing cloud repositories, and targeted mobile guardrails ( Compliance policy for Android and Compliance for iOS ).

### Project Results (Impact)
* **Successful Cloud Transformation:** Transitioned 60+ legacy network-bound physical workstations into fully autonomous, cloud-managed modern workplace devices with zero data loss.
* **Automated Zero-Touch Provisioning Baseline:** Verified that new hardware assets could now be spun up directly out-of-the-box using purely Entra ID login credentials, cutting historical technician hands-on configuration times drastically.
* **Enforced Least Privilege & Hardened Compliance:** Closed major security vulnerabilities by enforcing localized non-admin privileges globally, mandating BitLocker encryption escrow, and automating application delivery via Intune.

---
## 4. Multi-Floor Enterprise Wireless Network Optimization & Advanced Remediation
### Project Overview
* **Project Title:** High-Density Enterprise Wireless Infrastructure Stabilization & Layer 2/Re-Engineering
* **Role:** Tier 2 / Infrastructure & Support Specialist
* **Environment:** UniFi Wireless Architecture, HPE Legacy Switching, Enterprise Firewalls, Windows Server (DHCP/DNS), Advanced RF Diagnostic Suites
* **Scope:** Performing root-cause analysis and full-scale technical remediation of a chronic, multi-month wireless performance degradation affecting an enterprise multi-floor campus network.

### The Challenge (Situation)
An enterprise client was experiencing systemic, long-term wireless network unreliability, high latency, packet loss, and severe throughput drops. Multiple previous technicians had attempted to remediate the environment over several months without success. The infrastructure suffered from undocumented structural flaws across the wireless spectrum, underlying Layer 2 segmentation issues, and firewall routing ambiguities that severely degraded the user experience for both staff and guests.

### Core Technical Toolkit
* **Wireless Management:** UniFi Network Controller Infrastructure
* **Hardware Layer:** UniFi U6-Lite Access Points, HPE 1950 & 1820 Managed Switches
* **Protocols & RF Control:** 802.11r (Fast Roaming), Minimum Data Rate Tuning, Co-Channel Interference Mitigation
* **Network Core Services:** Windows Server DHCP, Layer 3 Firewall Routing, VLAN Segmentation

### Root-Cause Analysis & Engineering Remediation (Action)
The stabilization project was broken down into four distinct structural phases to isolate and repair legacy misconfigurations.

#### Phase 1: Layer 3 Routing & Firewall Remediation
* **VPN Address Overlap Resolution:** Discovered a critical architectural conflict where a Branch-to-Office Site-to-Site VPN advertised an address space that directly overlapped with the local internal network. This created routing ambiguity and asymmetric traffic loops. Completely re-engineered the firewall policies and disabled the conflicting overlapping advertisements to instantly stabilize internal network behavior.
* **Network Traffic Segmentation:** Identified a flat wireless network design where corporate staff traffic was combined on the same virtual network as legacy machinery and internal systems. Engineered a dedicated wireless VLAN (192.168.3.0/24), provisioned a fresh DHCP scope on the core domain controller, and established isolated firewall rules to enforce strict security zoning and traffic visibility.

#### Phase 2: RF Spectrum & Channel Optimization
* **Airtime Contention Remediation:** Diagnosed that legacy 2.4 GHz client devices and modern 5 GHz devices were bundled on the same SSIDs, triggering high airtime contention and dropping transmission rates for all users. Disabled the 2.4 GHz radio band entirely on Primary Staff and Guest SSIDs. Created an isolated, dedicated legacy SSID mapped to targeted access points to house older 2.4 GHz hardware safely away from production traffic.
* **Channel Width & Overlap Tuning:** Discovered access points mistakenly operating on wide 80 MHz channel widths in a high-density, multi-floor environment. This consumed scarce contiguous channels, causing massive co-channel interference and cross-floor airtime congestion. Scaled down channel footprints, implemented a meticulous channel reuse plan, and manually dialed down transmit power levels to LOW on all managed APs to completely eliminate overlapping RF boundaries and fix "sticky client" behavior.

#### Phase 3: Advanced High-Capacity & Roaming Adjustments
* **Enforcing Roaming Thresholds:** Implemented strict roaming optimization policies, setting a minimum 5 GHz RSSI roaming threshold of -65 dBm. This programmatically forces mobile endpoints to roam gracefully to a closer access point before packet retries and latency spike.
* **Airtime Fairness Tuning:** Enabled advanced high-capacity tuning. Raised the Minimum Data Rate threshold on the 5 GHz band to 12 Mbps / 24 Mbps and enforced a Multicast and Broadcast Blocker. This purged low-rate management frames from clogging wireless cells, freeing up massive blocks of raw airtime.

#### Phase 4: Infrastructure Auditing & Device Adoption
* **Orphaned Access Point Recovery:** Discovered multiple rogue/orphaned UniFi access points across all floors that were actively broadcasting corporate SSIDs but had completely lost their trust relationship with the central UniFi controller. Because they were unmanaged, they could not receive central channel distribution adjustments or firmware updates. Initiated physical audits, traced internal legacy HPE switches (HPE 1950 / 1820), and prepared a physical adoption workflow using remote PoE reset injectors to reclaim central management authority.

### Project Results (Impact)
* **Resolved a Multi-Month Network Crisis:** Successfully diagnosed and permanently resolved a chronic infrastructure failure that had eluded multiple engineering groups for months.
* **Drastic Performance Amplification:** Eliminated packet drops, reduced latency, and normalized deterministic throughput across all floors by purging co-channel interference and optimizing airtime utilization.
* **Hardened Security & Zero-Trust Posture:** Moved the entire corporate wireless footprint from a risky, flat broadcast domain into a highly segmented, firewall-audited VLAN structure.
This is a offline tool, your data stays locally and is not send to any server!
Feedback & Bug Reports
