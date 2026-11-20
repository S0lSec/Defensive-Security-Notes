# Tips
1. Target relevant data
2. Using target searches are much more efficient. e.g using `uniwaldo.local` or `ComputerName="*uniwaldo.local*"` instead of `*uniwaldo.local*`
3. Sorting by count can help spot abnormalities, an activity occurring frequently is more "normal" 
# Path
1. If this is a unknown environment start by listing source types.
	1. `index="main" | stats count by sourcetype`
2. Select a source type for this example we will be using Windows Event Logs Sysmon
	1. `index="main" sourcetype="WinEventLog:Sysmon`
3. Check event codes for activity that could be malicious, such as `sysmon event 1`: process creation or `sysmon event 10`: process access
	1. `index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | stats count by ParentImage, Image`
4. If we still have a lot of results we can filter for more problematic processes/systems
	1. `index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 (Image="*cmd.exe" OR Image="*powershell.exe") | stats count by ParentImage, Image`