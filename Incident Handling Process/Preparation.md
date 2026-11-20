# Preparation Stage
The preparation stage has two separate objectives:
- Establishment of incident handling capability within the organization
- Protect against and prevent IT security incidents by implementing appropriate protective measures
## Preparation Prerequisites
During the preparation stage we need to ensure that we have:
- Skilled incident handling team members
- A trained workforce
- Clear policies and documentation
- Tools
## Clear Policies & Documentation
Some of the written policies and documentation should contain an up-to-date version of the following information:
- Contact information and roles of the incident handling team members.
- Contact information for the legal and compliance department, management team, IT support, communications and media relations department, law enforcement, internet service providers, facility management, and external incident response team.
- Incident response policy, plan, and procedures.
- Incident information sharing policy and procedures.
- Baselines of systems and networks, out of a golden image and a clean state environment.
- Network diagrams.
- Organization-wide asset management database.
- User accounts with excessive privileges that can be used on-demand by the team when necessary (also for business-critical systems, which are handled with the skills needed to administer that specific system). These user accounts are normally enabled when an incident is confirmed during the initial investigation and then disabled once it is over. A mandatory password reset is also performed when disabling the users.
- Ability to acquire hardware, software, or an external resource without a complete procurement process (urgent purchase of up to a certain amount). The last thing you need during an incident is to wait for weeks for the approval of a $500 tool.
- Forensic/Investigative cheat sheets.

## Tools (Software & Hardware)
- An additional laptop or a forensic workstation for each incident handling team member to preserve disk images and log files, perform data analysis, and investigate without any restrictions (we know malware will be tested here, so tools such as antivirus should be disabled). These devices should be handled appropriately and not in a way that introduces risks to the organization.
- Digital forensic image acquisition and analysis tools.
- Memory capture and analysis tools.
- Live response capture and analysis tools.
- Log analysis tools.
- Network capture and analysis tools.
- Network cables and switches.
- Write blockers.
- Hard drives for forensic imaging.
- Power cables.
- Screwdrivers, tweezers, and other relevant tools to repair or disassemble hardware devices if needed.
- Indicator of Compromise (IOC) creator and the ability to search for IOCs across the organization.
- Chain of custody forms.
- Encryption software.
- Ticket tracking system.
- Secure facility for storage and investigation.
- Incident handling system independent of your organization's infrastructure.

Many of the tools mentions above will be part of a **jump bag** - always ready with the necessary tools to be picked up and taken immediately. 

## DMARC
DMAR is an email protection mechanism against phishing built on top of the already existing SPF (Sender Policy Framework) and DKIM (DomainKeys Identified Mail).

SPF - Email authentication method
DKIM - Adds digital signatures to emails

DMARC rejects emails that pretend to originate from our organisation.

## Endpoint Hardening ( & EDR)
Endpoints are the entry points of most attacks. Some highly important actions to note and do something about are:
- Disable LLMNR/NetBIOS.
- Implement LAPS and remove administrative privileges from regular users.
- Disable or configure PowerShell in "ConstrainedLanguage" mode.
- Enable Attack Surface Reduction (ASR) rules if using Microsoft Defender.
- Implement whitelisting. We know this is nearly impossible to implement. Consider at least blocking execution from user-writable folders (Downloads, Desktop, AppData, etc.). These are the locations where exploits and malicious payloads will initially find themselves. Remember to also block script types such as .hta, .vbs, .cmd, .bat, .js, and similar. We need to pay attention to [LOLBin](https://lolbas-project.github.io) files while implementing whitelisting. Do not overlook them; they are really used in the wild as initial access to bypass whitelisting.
- Utilize host-based firewalls. As a bare minimum, block workstation-to-workstation communication and block outbound traffic to LOLBins.
- Deploy an EDR product. At this point in time, [AMSI](https://learn.microsoft.com/en-us/windows/win32/amsi/how-amsi-helps) provides great visibility into obfuscated scripts for antimalware products to inspect the content before it gets executed. It is highly recommended that we only choose products that integrate with AMSI.

## Network Protection
- Business-critical systems must be isolated
- Connections should be allowed only as required
- Internal resources should not face the internet directly (unless placed in a DMZ)
- Consider IPS/IDS systems
- Ensure only approved devices can access the network
- 802.1x can be utilized to reduce the risk of BYOD
- If you are a cloud-only compay using Conditional Access Policies can achieve similar protection as the last two points

## Privilege Identity Management/MFA/Passwords
- Teach employees to use passphrases
- Use MFA on all applications and devices

## Vulnerability Scanning
- Perform continuous vulnerability scans
- Remediate at least the High and Critical vulnerabilities
- If patches can not be applied segment the systems that are vulnerable

## User Awareness Training
- Train users to recognize and report suspicious behavior

## Active Directory Security Assessment
- Crucial for the security posture of the environment
- Conduct your own reviews (or hire a third party) to check for misconfigurations or exposed vulnerabilities

## Purple Team Exercises
- A security assessment by a read team that either continuously or eventually informs the blue team about their actions, findings, any visibility or security shortcomings
- Such exercises will help in identifying vulnerabilities in an organisation while testing the blue teams defensive capability