# Flowmira
Customized NXLog configuration used to generate data from Windows endpoints that can be leveraged by teams for better insight into host-actions.  Blumira is making the Flowmira configuration for NXLog public for all to simplify the collection effort for all organizations from Windows machines.

## What is NXLog?
NXLog is a multi-platform log shipping tool that helps to easily identify security risks, policy breaches or analyze operational problems in server logs, operation system logs and application logs. In concept NXLog is similar to syslog-ng or Rsyslog but it is not limited to UNIX and syslog only.

## Where can I get NXLog?
You can download the community edition at https://nxlog.co/products/nxlog-community-edition/download.  If you require WEF you should obtain a license for the Commercial version of NXLog.  If you're a Blumira customer you can utilize the Logstash Module to collect WEF logs instead of purchasing a NXLog Commercial license.

# How do I set it up?
* Download and install the newest stable [NXLog Community Edition](https://nxlog.co/products/nxlog-community-edition/download).
* Replace C:\Program Files (x86)\nxlog\conf\nxlog.conf with the Blumira nxlog configuration file found in this repository.  
    * The file must be named nxlog.conf and be at the aforementioned location.  Allowing Windows to rename it to nxlog.conf.1 or renaming the file to flowmira_nxlog.conf will result in a failure of the NXLog service or an uptake of the default configuration.
* Open the configuration file for editing *as an administrator* replace A.B.C.D. with the actual IP address of your log aggregator at line 46. The edited line should look like the following: `define SIEM 10.1.2.3`
* Save the file after making your changes.  
    * You should also review the directions in the file for setting up logging for IIS and Windows Firewall
* Restart the NXLog service either through an administrator prompt in cmd or through the Services application.
    * net stop nxlog && net start nxlog
* Verify at your log aggregator that logs are landing via syslog over 514/TCP/UDP

# I'm not seeing as much as I expected, why's that?
It's possible you need to increase the audit levels of your Windows machines, by default they aren't super verbose.  Take a look at the Blumira [Logmira](https://www.blumira.com/logmira-windows-logging-policies/) - https://github.com/Blumira/Logmira GPO template to quickly resolve any visibility issues.

# I'm seeing way too much data!
You may want to pull back on Windows Filtering events such as 5156, these are very verbose and can be quite massive depending on how your network functions.  To disable these go to your GPO where you have defined these audit policies - or perhaps your Default Domain Controller Policy - and disable Audit Object Access.

`POLICY > POLICIES > WINDOWS SETTINGS > SECURITY SETTINGS > AUDIT POLICY > AUDIT OBJECT ACCESS`
