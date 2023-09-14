#### Linux:
"WULAI":
	- Weed
		- Removing/disabling unnecessary applications/services/processes/etc.
	- Update
		- Strategically update system componets
	- Log
		- Log important system info, changes, ownership, etc.
	- Access Control
		- Strict and effective access control measures
	- Isolate
		- Segment parts of your network

- Have a checklist per service/system/network/etc
- passwd is how to change the password for the user (normally do this as soon as you get on a competition box)
- checking bash history shows every command ran on the system before you got on. The command to do this is `cat .bash_history`
- check crontab for tasks scheduled in the system, or check /etc/cron for daily,hourly,monthy,etc.
- This command is `sudo crontab -l` or `cd /etc/cron` or you can list the tasks by doing `crontab -e` 
- running `sudo netstat -tunlp` to see all running services and what port they are on
- run the  command `ps` to see all the processes running on the system
- You can see all of the users on a system by running `cat /etc/passwd` and every user with an ID of over 1000 is an actaul user on the system
- You can scan for malicious files and remove them with `sudo clamscan --infected --remove` 
- `sudo apt install linus` to install linus which is what you can use to identify any vulnerable spots in the system. In order to run linus you do `sudo linus audit system`

#### Windows:
