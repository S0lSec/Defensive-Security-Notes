**(lifecycle -> cyber kill chain)**
- Lifecycle describes how attacks manifest themselves
- Understanding this lifecycle will provides us with insight into how far in the network an attacker is and what they may have access to during the investigation phase of an incident

# Cyber kill chain seven stages
Important to know that some adversaries don't operate linearly and may repeat multiple steps for instance.
![[Pasted image 20260401230302.png]]
## Recon
- Attacker chooses target
- Attacker performs information gathering (active or passive)
![[Pasted image 20260401230440.png]]
## Weaponize
- Malware to be used for initial access is developed and embedded into some type of exploit or deliverable payload
- On a large scale the sole purpose of this stage is to provide remote access
## Delivery
- Payload or exploit is delivered to the victim(s)
- This can be done by phishing, dropping USBs at the business , etc
## Exploitation
- Exploit or delivered payload is triggered
- During this stage the attacker generally attempts to execute code on the target system to gain access or control
## Installation
- The initial stager is executed and is running on the compromised machines
- This can be carried out in multiple ways such as:
	- Droppers
	- Backdoors
	- Rootkits
## Command and Control
- Attacker establishes a remote access capability to the compromised machine
- (It is not uncommon to use a modular initial stager that loads additional scripts on-the-fly)
- Advanced groups will utilize separate tools to ensure that multiple variants of their malware live in a compromised network
## Action
- Objective of the attack