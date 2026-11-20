The `Detection & Analysis` stage involves all aspects of detecting an incident, such as utilizing sensors, logs, and trained personnel.

It is highly recommended to create levels of detection by logically categorizing our network as follows:
- Detection at the network perimeter (using firewalls, internet-facing network intrusion detection/prevention systems, demilitarized zone, etc.).
- Detection at the internal network level (using local firewalls, host intrusion detection/prevention systems, etc.).
- Detection at the endpoint level (using antivirus systems, endpoint detection & response systems, etc.).
- Detection at the application level (using application logs, service logs, etc.).
# Initial Investigation
- When a security incident is detected, conduct initial investigation and establish context before assembling the team

**Collect  as much information as possible at this stage about the following:**
- Date/Time when the incident was reported. Additionally, who detected the incident and/or who reported it?
- How was the incident detected?
- What was the incident? Phishing? System unavailability? etc.
- Assemble a list of impacted systems (if relevant).
- Document who has accessed the impacted systems and what actions have been taken. Make a note of whether this is an ongoing incident or if the suspicious activity has been stopped.
- Physical location, operating systems, IP addresses and hostnames, system owner, system's purpose, current state of the system.
- List of IP addresses, if malware is involved, time and date of detection, type of malware, systems impacted, export of malicious files with forensic information on them (such as hashes, copies of the files, etc.).
# Incident Severity & Extent Questions
When handling a security incident, try to answer the following questions to get an idea of the incidents severity and extent:
- What is the exploitation impact?
- What are the exploitation requirements?
- Can any business-critical systems be affected by the incident?
- Are there any suggested remediation steps?
- How many systems have been impacted?
- Is the exploit being used in the wild?
- Does the exploit have any worm-like capabilities?
# Incident Confidentiality & Communication
- All information on incidents should be kept on a need-to-know basis unless applicable laws or a management decision instructs us otherwise
# The Investigation
The investigation starts based on the initially gathered information that contains what we know about the incident so far.

With this information start the 3-step cyclic process:
- Creation and usage of indicators of compromise (IOCs).
- Identification of new leads and impacted systems.
- Data collection and analysis from the new leads and impacted systems.
![[Pasted image 20260405234037.png]]
## Initial Investigation Data
- Investigation should be based on valid leads
- The incident handling team should constantly bring up new leads
- Narrowing an investigation down to a specific activity often results in limited findings, premature conclusions and incomplete understanding of the overall impact
## Creation & Usage of IOCs
- An indicator of compromise (IOC) is a sign that an incident has occured
- IOCs are documented in a structured manner, which represents the artifacts of the compromise
- Example IOCs:
	- IP addresses
	- hash values of files
	- file names
## Identification of New Leads & Impacted Systems
- After searching for IOCs, new hits that reveal other systems with the same sign of compromise are expected
- These hits may not be directly associated with the incident
- We need to identify and eliminate false positives
## Data Collection and Analysis from the New Leads and Impacted Systems
- **Collect** and **Preserve** the state of the identified systems that include our IOCs
- Further analyse systems
- Live response - Collect predefined set of data from a system that is still running to find out what happened to a system
- Shutting down a system is not an easy decision when preserving valuable information since much of the artifacts will live in RAM memory
- keep track of **chain of custody** to ensure data is court-admissible