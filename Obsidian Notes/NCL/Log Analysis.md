### SIEM: Security Information and Event Management

- A tool that collects data from various endpoints/network devices across the network, stores them at a centralized place and performs correlation on them.

#### Network Visibility
- each network component can have one or more log sources generating different logs. we can divide our network log sources into two logical parts:
##### Host-Centric Log Sources
- these are log sources that capture events that occurred within or related to the host. Some examples are Windows Event logs, Sysmon, Osquery, etc.
- examples of host-centric logs are:
	- a user accessing a file
	- a user attempting to authenticate
	- a process execution activity
	- a process adding/editing/deleting a registry key or value
	- PowerShell execution
##### Network-Centric Log Sources
- these are generated when the hosts communicate with each other or access the internet to visit a website. some network-based protocols are SSH, VPN, HTTP/s, FTP, etc.
- examples of such events are:
	- SSH connection
	- a file being accessed via FTP
	- web traffic
	- a user accessing company's resources through VPN
	- network file sharing activity

- Having a SIEM solution in place takes logs from various sources in real-time and provides the ability to correlate between events, search through logs, investigate incidents, and respond promptly.
- Key features provided by SIEM:
	- real-time log ingestion
	- alerting against abnormal activites
	- 24/7 monitoring and visibility
	- protection against the latest threats through early detection
	- data insights and visualization
	- ability to investigate past incidents


#### Log Sources and Log Ingestion

- every device generates some kind of log whenever an activity is performed on it, like a user visiting a website, connecting to SSH, logging into his workstation, etc.

##### Windows Machine
- Windows records every event that can be viewed through the Event Viewer utility. It assigns a unique ID to each type of log activity, making it easy for the analyst to examine and keep track of. These can be viewed in the Event Viewer application

##### Linux Workstation
- Linux OS stores all the related logs, such as events, errors, warnings, etc. They are then ingested into SIEM for continious monitoring. 
- Common locations where Linux store logs are:
	- /var/log/httpd : Contains HTTP Request  / Response and error logs.
	- /var/log/cron   : Events related to cron jobs are stored in this location.
	- /var/log/auth.log and /var/log/secure : Stores authentication related logs.
	- /var/log/kern : This file stores kernel related events.
- Example of a cron log:
```
May 28 13:04:20 ebr crond[2843]: /usr/sbin/crond 4.4 dillon's cron daemon, started with loglevel notice
May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-hourly)  
May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-daily)  
May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-weekly)  
May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-monthly)  
Jun 13 07:46:22 ebr crond[3592]: unable to exec /usr/sbin/sendmail: cron output for user root job sys-daily to /dev/null
```

##### Web Server
- It is important to keep track of all the requests/responses coming in and out of the webserver for any potential web attack attempt. In Linux, common locations to write all apache related logs are:
	- /var/log/apache or /var/log/httpd
- Example of Apache Logs:
```
192.168.21.200 - - [21/March/2022:10:17:10 -0300] "GET /cgi-bin/try/ HTTP/1.0" 200 3395
127.0.0.1 - - [21/March/2022:10:22:04 -0300] "GET / HTTP/1.0" 200 2216
```

##### Log Ingestion
- each SIEM solution has its own way of ingesting the logs
- some common ways are below:
	- Agent / Forwarder: these provide a lightweight tool called an agent (forawrder by Splunk) that gets installed in the endpoint and is configured to capture all the important logs and send them to the SIEM server.
	- Syslog: a widely used protocol to collect data from various systems like web servers, databases, etc, are sent real-time data to the centralized detsination
	- Manual Upload: some solutions like Splunk, ELK, etc allow users to ingest office data for quick analysis and once the data is ingested, it is normalized and made available for analysis.
	- Port-Forwarding: SIEM solutions can also be configured to listen on a certain port, and then the endpoints forward the data to the SIEM instance on the listening port

#### Why SIEM?
- SIEM is used to provide correlation on the collected data to detect threats. Once a threat is detected, or a certain threshold is crossed, an alert is raised. This alert enables the analysts to take suitable actions based on the investigation.

##### Capabilities:
- SIEM is one major componet of a Security Operations Center (SOC) ecosystem. It starts by collecting logs and examining if any event/flow has matched the condition set in the rule or crossed a certain threshold.
- Common capabilities are:
	- Correlation between events from different log sources.
	- Provide visibility on both Host-centric and Network-centric activities.
	- Allow analysts to investigate the latest threats and timely responses.
	- Hunt for threats that are not detected by the rules in place.

##### SOC Analyst Responsibilities:
- SOC Analysts utilize SIEM solutions in order to have better visibility of what is happening within the network.
- Some responsibilities are:
	- Monitoring and Investigating.
	- Identifying False positives.
	- Tuning Rules which are causing the noise or False positives.
	- Reporting and Compliance.
	- Identifying blind spots in the network visibility and covering them.

#### Analysing Logs and Alerts

##### Dashboard
- Dashboards are the most important componets of SIEM. The summary of the analyses is presnsted in the form of actionable insights with the help of multiple dahsboards. 
- Each SIEM solution comes with some defualt dashboards and provides an option for custom Dashboard creation. 
- Information found in a dashboard are:
	- alert highlights
	- system notifications
	- health alert
	- list of failed login attempts
	- events ingested count
	- rules triggered
	- top domains visited
- Example of a defualt dashboard:
![[Screenshot 2023-03-24 at 12.44.41 PM.png]]

##### Correlation Rules
- Correlation rules play an important role in the timely detection of threats. They are pretty much logial expressions set to be triggered. 
- A few examples:
	-  If a User gets 5 failed Login Attempts in 10 seconds - Raise an alert for `Multiple Failed Login Attempts`
	-   If login is successful after multiple failed login attempts - Raise an alert for `Successful Login After multiple Login Attempts`
	-   A rule is set to alert every time a user plugs in a USB (Useful if USB is restricted as per the company policy)
	-   If outbound traffic is > 25 MB - Raise an alert to potential Data exfiltration Attempt (Usually, it depends on the company policy)

- Use case 1:
	- Adversaries tend to remove logs during the post-exploitation phase to remove their tracks. A unique Event ID 104 is logged every time a user tries to remove or clear event logs. 
		- If the Log source is WinEventLog **AND** EventID is **104** - Trigger an alert `Event Log Cleared`
- Use case 2:
	- Adversaries use commands like whoami after the exploitation/privelge esclation phase. The following fields will be helpful to include in the rule
		- Log source: Identify the log source capturing the event logs  
		-  Event ID: which Event ID is associated with Process Execution activity? In this case, event id 4688 will be helpful.  
		-  NewProcessName: which process name will be helpful to include in the rule?
	- Rule: If Log Source is WinEventLog **AND** EventCode is **4688,** and NewProcessName contains **whoami,** then Trigger an ALERT `WHOAMI command Execution DETECTED`