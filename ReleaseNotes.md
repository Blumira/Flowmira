# Release Notes

## 2.0
* Now with better formatting!
* Got rid of all references to unsupported operating system versions. Now works on standard versions of Windows Server 2016 and 2019
* Separated out Core and Supplementary logging into three separate priorities.
	* Core Logs - Every OS has these, the most used and important of all windows event channels
	* Priority 1 - The higher fidelity and important log channels. Less configuration issues with mass roll out.
	* Priority 2 - Lower fidelity and medium importance depending on OS and environment. Disabled by default.
* More well defined and formatted tasks per sectiom

## 1.5
* Added Print Spooler Logs - CVE-2021-1675
## 1.4
* Added Directory Service Logs
## 1.3
* Isolated "Core" event route
* Added "Supplemental" and "Windows Defender" specific routes
* Comment changes - removed some verbiage
## 1.2
* Added Azure AD Password Protection support
* Isolated 15001/15007 errors specific to 2k12/2k16/2k19 and added related "Potential Tasks" and notes
* Added DEBUG LogLevel option
## 1.1
* Added Sysmon Support
* Updated Query list for Windows Event Logs
## 1.0
* Added IIS Support - Event Viewer default to On, polling non-existent is non-impacting to hosts
* Added FW Support 
* Improved time handling to force UTC time on host
