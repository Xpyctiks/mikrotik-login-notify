# mikrotik-login-notify
Bash script which parses .log files with collected from ROS devices log data. Sends notifications about log-in and log-out to device. Can send alert by trigger word.

Set-up log collection from your Mikrotik devices.For example using Debian machine with Rsyslog daemon, configured to accept external log messages to UDP 514.
Now, place all your log files in one folder. After first launch the script will generate .conf file where you need to put correct values of Telegram API token and
telegram ChatID. Plus, configure log files folder.

After launch, the script getting into the log folder, looking for all .log files and starts parse them.Main keywords to look for are: "logged in", "logged out",
"failed login" and one trigger-keyword "ALERT" which can be added to any firewall filter log rule and will trigger this script to send notifiy if being detected in logs.

To use script, just add it to cron:
* * * * * /<path>/mikrotik-login-notify > /dev/null 2>&1
