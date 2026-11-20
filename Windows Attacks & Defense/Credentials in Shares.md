Having unencrypted credentials exposed in network shares are a very common misconfiguration in AD.

Usually found in:
- scripts
- configuration files
- excel sheets
- word docs
- text files
# Attack
1. Identify what shares exist in a domain, there are many tools for this such as PowerViews Invoke-ShareFinder
	1. `Invoke-ShareFinder -domain eagle.local -ExcludeStandard -CheckShareAccess`
2. Find files
	1. Automated tools exist for this such as [SauronEye](https://github.com/vivami/SauronEye) but you can also do it manually using `findstr`
		1. `findstr /m /s /i "pass" *.bat`
		2. `findstr /m /s /i "pw" *.config`
	2. Check .bat, .cmd, .ini, .config
	
Note: Running `findstr` with the same arguments is recently picked up by Windows Defender as suspicious behavior
# Prevention
LOCK DOWN THE SHARES
Cant do much more than that, its more user error than anything
# Detection
- Understand and analyze users behavior is the best detection technique for abusing discovered credentials in shares
- Successful logon with an event ID `4624`/`4625`/`4768`
![[Pasted image 20260716161532.png]]
- Discover one-to-many connections, for example when `Invoke-ShareFinder` scans every domain to obtain a list of its network shares.
# Honeypot
- User in AD environment with some privileges and a wrong password