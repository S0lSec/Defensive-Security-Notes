`SYSVOL` is a network share on all DCs, containing logon scripts, gp data, etc.
This attack essentially takes advantage that this share is available to anyone and attempts to decrypt the credentials used for authentication.
# Attack
- Use **Get-GPPPassword** function from `PowerSploit` which automatically parses all XML files in the Policies folder in `SYSVOL`
```
PS C:\Users\bob\Downloads> Import-Module .\Get-GPPPassword.ps1
PS C:\Users\bob\Downloads> Get-GPPPassword
```
# Prevention
- Assess the environment to ensure no credentials are stored in `SYSVOL`
- Microsoft released a patch (`KB2962486`) in **2014** to prevent caching credentials in GPP
# Detection
- Accessing the XML file containing the credentials should be a red flag if we are auditing the file. No one should be touching this file
- If auditing the file is enabled any access will generate Event ID `4663`
- Logon attempts of the user whose credentials are exposed is another way of detecting the abuse of this attack. Should generate `4624`,`4625` or `4768`
# Honeypot
Use a smi-privileged user with a wrong password. The password should be old and ensure that the last password is older than when the GPP XML file was last modified.

Configure an alert that if any successful or failed logon attempts occur with this service account.

Since the provided password is wrong, we expect failed logon attempts. Three IDs can indicate this:
- `4625`
- `4771`
- `4776`