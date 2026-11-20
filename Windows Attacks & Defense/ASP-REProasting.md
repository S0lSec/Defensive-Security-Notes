# Attack
## How Kerberos works
1. User requests a Ticket Granting Ticket (TGT) from the DCs Kerberos service
2. The DC sends back data encrypted using a key derived from the users password
3. The user can decrypt it because they know their password
The process proves the user knows their password without sending it over the network.
## How the attack works
Accounts in AD have the **Do not require Keberos pre-authentication** setting enabled. If this setting is disabled anyone can request an Authenticated Service Response for the account.
The DC returns data encrypted with a key derived from the users password, allowing for it to be guessed.
# Prevention
- Use strong passwords
- Require kerberos pre-auth
# Detection
- Event with ID `4768` is generated signaling that a Kerberos Authentication tick was generated
- Events with ID are generated often so try to use location to track the device
- Focus on Pre-Authentication Type fields as well
# Honeypot
- Creating a fake user account
- Dont make it the only account with kerberos pre-authentication not required