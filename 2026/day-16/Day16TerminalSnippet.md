```Bash
ubuntu@ip-172-31-32-244:~$ ./hello.sh
./hello.sh: line 2: Hello: command not found
./hello.sh: line 3: Myself: command not found
ubuntu@ip-172-31-32-244:~$ vim hello.sh
ubuntu@ip-172-31-32-244:~$ sed -i '1d' hello.sh
ubuntu@ip-172-31-32-244:~$ vim hello.sh
ubuntu@ip-172-31-32-244:~$ ./hello.sh
./hello.sh: line 1: Hello: command not found
./hello.sh: line 2: Myself: command not found
ubuntu@ip-172-31-32-244:~$ vim hello.sh
ubuntu@ip-172-31-32-244:~$ ./hello.sh
Hello devops Engineers
Myself Govind saraswat
ubuntu@ip-172-31-32-244:~$ touch variable.sh
ubuntu@ip-172-31-32-244:~$ vim variable.sh
ubuntu@ip-172-31-32-244:~$ ./variable.sh
-bash: ./variable.sh: Permission denied
ubuntu@ip-172-31-32-244:~$ chmod +x variable.sh
ubuntu@ip-172-31-32-244:~$ ./variable.sh
 Hello , My name is Name and I am a Devops Engineer
ubuntu@ip-172-31-32-244:~$ vim variable.sh
ubuntu@ip-172-31-32-244:~$ ./variable.sh
./variable.sh: line 2: Name: command not found
./variable.sh: line 3: Role: command not found
 Hello , My name is  and I am a
ubuntu@ip-172-31-32-244:~$ vim variable.sh
ubuntu@ip-172-31-32-244:~$ ./variable.sh
./variable.sh: line 2: Name: command not found
./variable.sh: line 3: Role: command not found
 Hello , My name is  and I am a
ubuntu@ip-172-31-32-244:~$ vim variable.sh
ubuntu@ip-172-31-32-244:~$ ./variable.sh
 Hello , My name is Govind Saraswat and I am a Devops Engineer
ubuntu@ip-172-31-32-244:~$ vim variable.sh
ubuntu@ip-172-31-32-244:~$ ./variable.sh
Enter your Name:
Govind Saraswat
Enter your Role:
Devops Engineer
Hello , My name is Govind Saraswat and I am a Devops Engineer
ubuntu@ip-172-31-32-244:~$
Broadcast message from root@ip-172-31-32-244 (Fri 2026-05-01 17:06:52 UTC):

The system will power off now!

Connection to ec2-13-53-212-18.eu-north-1.compute.amazonaws.com closed by remote host.
Connection to ec2-13-53-212-18.eu-north-1.compute.amazonaws.com closed.
PS C:\Users\saras\downloads> ssh -i "2501key.pem" ubuntu@ec2-16-170-235-141.eu-north-1.compute.amazonaws.com
The authenticity of host 'ec2-16-170-235-141.eu-north-1.compute.amazonaws.com (16.170.235.141)' can't be established.
ED25519 key fingerprint is SHA256:LzJ0K+2yPW8w5YHOcd7FqGUtw6MMPMLUOSp0b31Q30U.
This host key is known by the following other names/addresses:
    C:\Users\saras/.ssh/known_hosts:26: ec2-13-51-169-85.eu-north-1.compute.amazonaws.com
    C:\Users\saras/.ssh/known_hosts:29: 13.51.169.85
    C:\Users\saras/.ssh/known_hosts:30: ec2-16-171-36-101.eu-north-1.compute.amazonaws.com
    C:\Users\saras/.ssh/known_hosts:31: ec2-13-60-83-25.eu-north-1.compute.amazonaws.com
    C:\Users\saras/.ssh/known_hosts:32: ec2-13-62-100-112.eu-north-1.compute.amazonaws.com
    C:\Users\saras/.ssh/known_hosts:33: ec2-16-170-225-32.eu-north-1.compute.amazonaws.com
    C:\Users\saras/.ssh/known_hosts:34: ec2-16-170-241-156.eu-north-1.compute.amazonaws.com
    C:\Users\saras/.ssh/known_hosts:35: ec2-13-53-212-18.eu-north-1.compute.amazonaws.com
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'ec2-16-170-235-141.eu-north-1.compute.amazonaws.com' (ED25519) to the list of known hosts.
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.14.0-1018-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Fri May  1 18:23:09 UTC 2026

  System load:  0.0               Temperature:           -273.1 C
  Usage of /:   37.6% of 6.71GB   Processes:             127
  Memory usage: 29%               Users logged in:       0
  Swap usage:   0%                IPv4 address for ens5: 172.31.32.244


Expanded Security Maintenance for Applications is not enabled.

5 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

1 additional security update can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


Last login: Fri May  1 16:18:51 2026 from 223.228.89.170
ubuntu@ip-172-31-32-244:~$ checknumber.sh
checknumber.sh: command not found
ubuntu@ip-172-31-32-244:~$ touch checknumber.sh
ubuntu@ip-172-31-32-244:~$ vim checknumber.sh

ubuntu@ip-172-31-32-244:~$ chmod +x checknumber.sh
ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
-1
./checknumber.sh: line 11: syntax error: unexpected end of file
ubuntu@ip-172-31-32-244:~$ vim checknumber.sh

ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
2
./checknumber.sh: line 13: syntax error: unexpected end of file
ubuntu@ip-172-31-32-244:~$ vim checknumber.sh

ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
-2
 -2 is Negative
ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
23
 23 is Positive
ubuntu@ip-172-31-32-244:~$ vim checknumber.sh

ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
2
./checknumber.sh: line 7: syntax error near unexpected token `elif'
./checknumber.sh: line 7: `elif [ $Number -lt 0]'
ubuntu@ip-172-31-32-244:~$ vim checknumber.sh
"checknumber.sh" 11L, 239B written
ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
2
 2 is Positive
ubuntu@ip-172-31-32-244:~$ -23
-23: command not found
ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
-23
./checknumber.sh: line 7: [: missing `]'
 -23 is Zero
ubuntu@ip-172-31-32-244:~$ vim checknumber.sh
ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
-23
 -23 is Negative
ubuntu@ip-172-31-32-244:~$ ./checknumber.sh
 enter your number to check if it is positive or negative:
0
 0 is Zero
ubuntu@ip-172-31-32-244:~$ touch find_file.sh
ubuntu@ip-172-31-32-244:~$ vim find_file.sh
ubuntu@ip-172-31-32-244:~$  0L, 0B written
ubuntu@ip-172-31-32-244:~$ vim find_file.sh
ubuntu@ip-172-31-32-244:~$ chmod +x find_file.sh
ubuntu@ip-172-31-32-244:~$ ./find_file.sh
enter the filename:
hello.sh
file exists
ubuntu@ip-172-31-32-244:~$ ./find_file.sh
enter the filename:
scipt.sh
file does not exists
ubuntu@ip-172-31-32-244:~$ ./find_file.sh
enter the filename:
script.sh
file exists
ubuntu@ip-172-31-32-244:~$ touch service_check.sh
ubuntu@ip-172-31-32-244:~$ vim service_check.sh

ubuntu@ip-172-31-32-244:~$ chmod +x service_check.sh
ubuntu@ip-172-31-32-244:~$ ./service_check.sh
Available services are nginx , sshd
enter the service you want to check :
nginx
./service_check.sh: line 7: syntax error in conditional expression
./service_check.sh: line 8: syntax error near `you'
./service_check.sh: line 8: `   echo "Do you want to check the status of $service? (y/n) :"'
ubuntu@ip-172-31-32-244:~$ vim service_check.sh

ubuntu@ip-172-31-32-244:~$ vim service_check.sh
ubuntu@ip-172-31-32-244:~$  26L, 566B written
ubuntu@ip-172-31-32-244:~$ ./service_check.sh
Available services are nginx , sshd
enter the service you want to check :
nginx
invalid service requested
ubuntu@ip-172-31-32-244:~$ ./service_check.sh
Available services are nginx , sshd
enter the service you want to check :
^[[A^[[A^[^C
ubuntu@ip-172-31-32-244:~$ vim service_check.sh
"service_check.sh" 26L, 565B written
ubuntu@ip-172-31-32-244:~$ vim service_check.sh

ubuntu@ip-172-31-32-244:~$ ./service_check.sh
Available services are nginx , sshd
enter the service you want to check :
nginx
Do you want to check the status of nginx? (y/n) :
y
service is running
ubuntu@ip-172-31-32-244:~$ ./service_check.sh
Available services are nginx , sshd
enter the service you want to check :
ssh
invalid service requested
ubuntu@ip-172-31-32-244:~$ exit
logout
Connection to ec2-16-170-235-141.eu-north-1.compute.amazonaws.com closed.
```
