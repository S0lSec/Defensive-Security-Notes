# Sysmon
(System Monitor)
- Provides detailed information about process creation, network connection, changes to file creation time
- Logs information that may not appear in Security Event Logs
- Sysmon event IDs: [link](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- Uses a XML-based configuration file, allowing you to include/exclude events based on data ([example1](https://github.com/SwiftOnSecurity/sysmon-config) [example2](https://github.com/olafhartong/sysmon-modular))
## Installation
1. Download from official Microsoft documentation ([link](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon))
2. `C:\Tools\Sysmon> sysmon.exe -i -accepteula -h md5,sha256,imphash -l -n`
## Use a custom Sysmon configuration
`C:\Tools\Sysmon> sysmon.exe -c filename.xml`
## For Linux
https://github.com/microsoft/SysmonForLinux
