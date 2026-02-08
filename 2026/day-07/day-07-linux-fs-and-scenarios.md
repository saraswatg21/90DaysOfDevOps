## Commands Practiced & explanation

## Core directories

```bash
ls -l /
```
displays detailed info about the number of files & folder present in root folder with user permissions accross files and folder. dev , boot , etc , bin -> usr/bin are few folders that are returned after the command 

```bash
ls -l /home
```
displays total number as 4 and folder named `ubuntu` inside it 
`drwxr-x--- 6 ubuntu ubuntu 4096 Feb  8 13:49 ubuntu`

```bash
 ls -l /root
```
displays user has not permission to access it 
`ls: cannot open directory '/root': Permission denied`

```bash
ls -l /etc
```
displays total number as 928 with detailed info about user permission for files and folders present in it .

```bash
ls -l /var/log
```
displays total number as 2784 with detailed info about user permission for logs files present in it .

```bash
ls -l /tmp
```
displays total number as 28 with detailed info about user permission for folders present in it .

## Additional Directories

```bash
ls -l /bin
```
displays  detailed info about user permission for binary present in it.
`lrwxrwxrwx 1 root root 7 Apr 22  2024 /bin -> usr/bin`


```bash
ls -l /usr/bin
```
displays total number as 121196 with detailed info about user binaries present in linux .

```bash
ls -l /opt
```
displays total number as 0 because there is no file and folder present in it.


## Part-1: Hands-On Task

```bash
 du -sh /var/log/* 2>/dev/null |sort -h | tail -5
```
finds the largest log file in /var/log

```bash
cat /etc/hostname
```
displays output of config file in /etc

```bash
ls -la ~
```
displays total number as 44 with detailed info about user permission for files present in home directory.

### Part 2: Scenario-Based Practice

**Scenario 1: Service Not Starting**

```
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.
```

Step 1: `systemctl status myapp`
**Why: Checks whether the service is running, failed, or inactive and shows recent errors.**

Step 2: `journalctl -u myapp -n 50`
**Why: Reads the last 50 log entries to understand why the service failed.**

Step 3: `systemctl is-enabled myapp`
**Why: Verifies whether the service is enabled to start automatically on boot.**

Step 4: `systemctl list-dependencies myapp`
**Why: Checks if required dependent services are missing or failed.**

---

**Scenario 2: High CPU Usage** 

```
Your manager reports that the application server is slow.
You SSH into the server.
What commands would you run to identify which process is using high CPU?
```

Step 1: `top`
**Why: Shows live CPU usage and highlights processes consuming the most CPU.**

Step 2: `ps aux --sort=-%cpu | head -10`
**Why: Lists the top CPU-consuming processes in descending order.**

Step 3: `ps -p <PID> -o pid,ppid,cmd,%cpu,%mem`
**Why: Inspects the specific process using high CPU to understand what it is.**


---

**Scenario 3: Finding Service Logs** 

```
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?
```

Step 1: `systemctl status docker`
**Why: Confirms the service state and shows a short log summary.**

Step 2: `journalctl -u docker -n 50`
**Why: Displays the last 50 log entries for the docker service.**

Step 3: `journalctl -u docker -f`
**Why: Follows docker logs in real time to observe live activity or errors.**


---

**Scenario 4: File Permissions Issue** 
```
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

What commands would you use to fix this?
```

Step 1: `ls -l /home/user/backup.sh`
**Why: Checks current permissions and confirms missing execute (x) bit.**

Step 2: `chmod +x /home/user/backup.sh`
**Why: Adds execute permission so the script can run.**

Step 3: `ls -l /home/user/backup.sh`
**Why: Verifies that execute permission was applied successfully.**

Step 4: `./backup.sh`
**Why: Runs the script to confirm the issue is fixed.**


