- Post-exploitation attacks that attempts to exploit the behavior of Kerberos by obtaining a ticket and performing offline password cracking to open the ticket
- The success of this attacks relies on the strength of the service accounts password
# Performing the Attack
1. Obtain tickets using `Rubeus`
2. Crack passwords using `hashcat` or `John the Ripper`
# Prevention
- Use strong passwords
- Limit the number of accounts with SPNs and disable those not used/needed
- Use Group Managed Service Accounts
# Detection
- When TGS is requested an event log with the ID `4769` is generated
- AD generates event ID `4769` when a user attempts to  connect to a service
# Honeypot
- A honeypot user is a good detection option
- Requirements
	- old user
	- Password must not of been changed recently
	- Must have some privileges
	- Account must have a SPN registered
- Alert if any activity is made