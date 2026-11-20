1. Pick a call stack to yield data from
	1. `index="main" CallTrace="*UNKNOWN*" | stats count by EventCode`
2. Group data based on variables, e.g. SourceImage
	1. `index="main" CallTrace="*UNKNOWN*" | stats count by SourceImage`
3. If needed filter for necessary events, e.g a process accessing itself
	1. `index="main" CallTrace="*UNKNOWN*" | where SourceImage!=TargetImage | stats count by SourceImage`