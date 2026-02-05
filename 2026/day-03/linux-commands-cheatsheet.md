Process Management commands: -

ps :
    displays info about the programs currently running on your computer

ps aux :
    displays detailed list of currently running programs

pidof :
    displays process id of currently running process

pgrep :
    used to search process by name and it returns the process id

top:
    displays details of running process and programs also provides the info about how much resources are bring used currently

htop :
    same as top command but lets you view the details vertically and horizontally

kill PID :
    kills the process with <PID>

lsof:
    lists all open files on the system

lsof -u root:
    lists all open files on the system by root user

nohup :
    runs a programs in background even if shells is killed

systemctl :
    Linux uses system as service manager and systemctl is remote control of systemd.
    ex :- systemctl start nginx : turns on the service
    systemctl stop nginx : turns off the service

nice :
    sets the priority level of program
    ex:- nice -n 10 script.sh :runs script.sh at lower priority

renice :
    changes the priority of already running program
    ex: renice -n 5 1234 : changes priority of PID 1234 to 5



File system commands: -


 *  :
 	compares and matches with any number of characters , returns the lists with matching filenames in current working directory

ls * :
    lists all the files and directories in the directory

ls -l :
 	lists all the files and directories with all user permissions , date \& time of modification

ls -a :
 	list all the hidden file and folders

ls -t:
 	list all the files and directories sorted on the basis of recent date/time modification

*.txt :
 	lists all the files having .txt extension in the directory

? :
    matches any single character
    ex: ls file?.txt would match file1.txt , fileA.txt , file\_.txt but not file10.txt(it has 2 characters after "file")

cd :
    to change the directory

cd ..
    navigates back to parent directory

pwd :
    returns the path of present working directory

mkdir A :
    makes a new directory named A inside current directory

mv A B :
    moves a file from path A to path B
    ex : mv ./folder1/file.txt ./folder2

cp A B :
    copies a file from path A to path B
    ex : cp ./folder1/file.txt ./folder2

cp -r A B:
    recursively copies all files of A (copies whole A directory) to B

rm X :
    removes file X permanently

rm -r X :
    removes X directory permanently and its content

rm -f X :
    removes X file forcibly without prompting confirmation

rm -rf X :
    removes X directory and its content forcibly without prompting confirmation

touch x :
    creates an empty file x or updates the access and modification times of X

cat x :
    view content of file x

cat-b x :
    displays line number of x with content

wc x :
 	displays word count of x

head x :
    displays first 10 lines of x

head -n 4 x:
    displays first 4 lines of x

tail x :
    displays last 10 lines of x

tail -n+1 x:
    displays entire content of x with header of file name

tail -f x :
    displays last 10 lines of x and track changes appended to them




Networking troubleshooting : -

ifconfig :
	Displays all network interfaces with ip addresses

ifconfig -a :
	Displayes all network interfaces with ip addresses even if any one is down 

ip a : 
	another way of displaying all network interfaces with ip addresses

netstat :
	prints open sockets of network connections , routing tables , interface statistics 

netstat -a :
	show both listening and non listening sockets 

netstat -l :
	 shows only listening sockets 

ping host :
	sends ICMP echo request to host which may be a symbolic name , domain name or IP address

whois domain :
	displays domain information 

dig domain :
	displays DNS information for domain 

host domain :
	displays DNS IP address for domain 

wget LINK :
	download from location link 

curl LINK :
	displays HTML source of link

