```Bash
ubuntu@ip-172-31-32-244:~$ touch log_rotate.sh
ubuntu@ip-172-31-32-244:~$ chmod +x log_rotate.sh
ubuntu@ip-172-31-32-244:~$ vim log_rotate.sh

ubuntu@ip-172-31-32-244:~$ ./log_rotate.sh
./log_rotate.sh: line 5: $1: unbound variable
ubuntu@ip-172-31-32-244:~$ ./log_rotate.sh /var/log
error : directory does not exist!
ubuntu@ip-172-31-32-244:~$ vim log_rotate.sh
ubuntu@ip-172-31-32-244:~$ ./log_rotate.sh /var/log
Processing logs in /var/log ...
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/amazon’: Permission denied
ubuntu@ip-172-31-32-244:~$ sudo ./log_rotate.sh /var/log
Processing logs in /var/log ...
compressed file: 4
Deleted Old archives: 20
ubuntu@ip-172-31-32-244:~$ touch server_backup.sh
ubuntu@ip-172-31-32-244:~$ chmod +x server_backup.sh
ubuntu@ip-172-31-32-244:~$ vim server_backup.sh
ubuntu@ip-172-31-32-244:~$ ./server_backup.sh
./server_backup.sh: line 5: $1: unbound variable
ubuntu@ip-172-31-32-244:~$ ./server_backup.sh /home/ubuntu /home/ubuntu/backups
tar: Removing leading `/' from member names
Backup created successfully
File: /home/ubuntu/backups/backup-2026-05-02.tar.gz
12K     /home/ubuntu/backups/backup-2026-05-02.tar.gz
ubuntu@ip-172-31-32-244:~$ crontab -l
no crontab for ubuntu
ubuntu@ip-172-31-32-244:~$ 0 2 * * * /path/to/log_rotate.sh /var/log/myapp
0: command not found
ubuntu@ip-172-31-32-244:~$ crontab -e
no crontab for ubuntu - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny
  4. /bin/ed

Choose 1-4 [1]: 2
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ crontab -l
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#

# m h  dom mon dow   command

0 2 * * * /home/ubuntu/log_rotate.sh /var/log/myapp
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ touch maintenance.sh
ubuntu@ip-172-31-32-244:~$ chmod +x maintenance.sh
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ ./maintenance.sh
./maintenance.sh: line 8: /var/log/maintenance.log: Permission denied
ubuntu@ip-172-31-32-244:~$ sudo ./maintenance.sh
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ ./maintenance.sh
./maintenance.sh: line 8: /var/log/maintenance.log: Permission denied
ubuntu@ip-172-31-32-244:~$ sudo ./maintenance.sh
ubuntu@ip-172-31-32-244:~$ * * * * * /bin/bash /home/ubuntu/maintenance.sh >> /home/ubuntu/test.log 2>&1
ubuntu@ip-172-31-32-244:~$ cat /home/ubuntu/test.log
Command 'backups' not found, did you mean:
  command 'backupy' from snap backupy (1.10.1)
  command 'backupz' from snap backupz (0.0.5)
  command 'backup' from deb openafs-client (1.8.10-2.1ubuntu3.4)
See 'snap info <snapname>' for additional versions.
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ cat /home/ubuntu/test.log
Command 'backups' not found, did you mean:
  command 'backupy' from snap backupy (1.10.1)
  command 'backupz' from snap backupz (0.0.5)
  command 'backup' from deb openafs-client (1.8.10-2.1ubuntu3.4)
See 'snap info <snapname>' for additional versions.
ubuntu@ip-172-31-32-244:~$ cat /home/ubuntu/test.log
Command 'backups' not found, did you mean:
  command 'backupy' from snap backupy (1.10.1)
  command 'backupz' from snap backupz (0.0.5)
  command 'backup' from deb openafs-client (1.8.10-2.1ubuntu3.4)
See 'snap info <snapname>' for additional versions.
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ crontab -e
crontab: installing new crontab
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ cat /home/ubuntu/test.log
Command 'backups' not found, did you mean:
  command 'backupy' from snap backupy (1.10.1)
  command 'backupz' from snap backupz (0.0.5)
  command 'backup' from deb openafs-client (1.8.10-2.1ubuntu3.4)
See 'snap info <snapname>' for additional versions.
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ sudo ./maintenance.sh
ubuntu@ip-172-31-32-244:~$ cat ~/maintenance.log
cat: /home/ubuntu/maintenance.log: No such file or directory
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ ./maintenance.sh
ubuntu@ip-172-31-32-244:~$ cat ~/maintenance.log
2026-05-02 21:03:02 : Maintenance started
2026-05-02 21:03:02 : Starting log rotation
Error: Directory does not exist ❌
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ ./maintenance.sh
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ ./maintenance.sh
ubuntu@ip-172-31-32-244:~$ cat ~/maintenance.log
2026-05-02 21:03:02 : Maintenance started
2026-05-02 21:03:02 : Starting log rotation
Error: Directory does not exist ❌
2026-05-02 21:04:32 : Maintenance started
2026-05-02 21:04:32 : Starting log rotation
Processing logs in /var/log ...
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/amazon’: Permission denied
2026-05-02 21:04:40 : Maintenance started
2026-05-02 21:04:40 : Starting log rotation
Processing logs in /var/log ...
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/amazon’: Permission denied
ubuntu@ip-172-31-32-244:~$ vim maintenance.sh
ubuntu@ip-172-31-32-244:~$ vim log_rotate.sh
ubuntu@ip-172-31-32-244:~$ ./maintenance.sh
Processing logs in /var/log ...
ubuntu@ip-172-31-32-244:~$ cat ~/maintenance.log
2026-05-02 21:03:02 : Maintenance started
2026-05-02 21:03:02 : Starting log rotation
Error: Directory does not exist ❌
2026-05-02 21:04:32 : Maintenance started
2026-05-02 21:04:32 : Starting log rotation
Processing logs in /var/log ...
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/amazon’: Permission denied
2026-05-02 21:04:40 : Maintenance started
2026-05-02 21:04:40 : Starting log rotation
Processing logs in /var/log ...
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/amazon’: Permission denied
2026-05-02 21:07:22 : Maintenance started
2026-05-02 21:07:22 : Starting log rotation
2026-05-02 21:07:22 : Log rotation failed
2026-05-02 21:07:22 : Starting backup
tar: Removing leading `/' from member names
Backup created successfully
File: /home/ubuntu/backup/backup-2026-05-02.tar.gz
28K     /home/ubuntu/backup/backup-2026-05-02.tar.gz
2026-05-02 21:07:22 : Completed backup
2026-05-02 21:07:22 : Maintenance completed
ubuntu@ip-172-31-32-244:~$
```
