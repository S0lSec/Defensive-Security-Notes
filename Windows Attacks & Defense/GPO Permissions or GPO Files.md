Group Policy Objects are used apply settings to devices connected to a domain. This attack is a simple GPO edit or file replacement.
# Prevention
- Lock down the GPO permissions to be modified by a group of users only or by a specific account
- Never deploy files stored in network locations
# Detection
If Directory Service Changes auditing is enabled then event ID `5136` will be generated.
![[Pasted image 20260716151225.png]]
# Honeypot
Having a misconfigured GPO in an environment for threat agents to abuse can be a good detection, however its only wise to implement such a method if the organization is proactive in responding to high/critical vulnerabilities.

If decided to implement a honeypot using a misconfigured GPO consider:
- GPO is linked to non-critical servers only
- Continuous automation is a place for monitoring modifications of GPO
- The GPO should be automatically unlinked from all locations if a modification is detected

Consider the following script to demonstrate how PowerShell can automate this. In our case, the honeypot GPO is identified by a GUID value, and the action desired is to disable the account(s) associated with this change. The reason for potentially multiple accounts is that we will execute the script every 15 minutes as a scheduled task. So, if numerous compromised users were used to modify the GPO in this time frame, we will disable them all instantly. The script has a commented-out section that can be used for sending an email as an alert, but for a PoC, we will display the output on the command line:

```
# Define filter for the last 15 minutes
$TimeSpan = (Get-Date) - (New-TimeSpan -Minutes 15)

# Search for event ID 5136 (GPO modified) in the past 15 minutes $Logs = Get-WinEvent -FilterHashtable @{LogName='Security';id=5136;StartTime=$TimeSpan} -ErrorAction SilentlyContinue |`
Where-Object {$_.Properties[8].Value -match "CN={73C66DBB-81DA-44D8-BDEF-20BA2C27056D},CN=POLICIES,CN=SYSTEM,DC=EAGLE,DC=LOCAL"}

if($Logs){
	$emailBody = "Honeypot GPO '73C66DBB-81DA-44D8-BDEF-20BA2C27056D' was modified`r`n" 
	$disabledUsers = @()
	ForEach($log in $logs){
		If(((Get-ADUser -identity $log.Properties[3].Value).Enabled -eq $true) -and ($log.Properties[3].Value -notin $disabledUsers)){
		    Disable-ADAccount -Identity $log.Properties[3].Value
		    $emailBody = $emailBody + "Disabled user " + $log.Properties[3].Value + "`r`n"
		    $disabledUsers += $log.Properties[3].Value
		}
	}
	# Send an alert via email - complete the command below
	# Send-MailMessage
	$emailBody
}
```
