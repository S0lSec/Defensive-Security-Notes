Example: `calc.exe` spawning `cmd.exe` in a normal Windows environment

**To view parent-child relationships within Windows use**:
- Process Hacker
# Showcase
Using the [psgetsystem project](https://github.com/decoder-it/psgetsystem) run these commands:
- `powershell -ep bypass`
- `Import-Module .\psgetsys.ps1`
- `[MyProcess]::CreateProcessFromParent([Parent PID], "C:\Windows\System32\cmd.exe")`