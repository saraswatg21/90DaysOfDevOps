Core components of Linux 

A:- Application(system applications)
S:- Shell(bash ....for user commands)
K:- Kernel( heart/core of Linux ...manages hardware, processes , memory)
H:- Hardware :- physical components which controls OS(RAM ,CPU ,disk)

user space :- it is the memory where applications , daemons and drivers execute(runs)
kernel space :- it is the restricted memory are where cpre of operating system runs 

init/system :- Both are responsible for booting the system and managing the processes , running as the first process with PID 1 


How processes are created and managed?

processes are created through fork() and exec() and are managed by kernel's scheduler and user space commands 

fork(): a system call which creates a copy of parent process resulting in a new and separate child process which inherits parents memory space
exec():- child process then uses this system call to load a new executable program into its memory space.

What systemd does and why it matters

systemd is responsible for booting the system and managing the processes , running as the first process with PID 1

it matters because it reduces boot time through parallelization and it also provides automatic service restart if service crashes


What is Linux ------- Linux is an open source operating system developed by Linux Torwalds in 1991
Why Linux ---- 90% of apps are running on Linux 
How to learn ----- AWS 

_______________________________________________________________
"Everything in Linux is either a file or a directory(folder)"
"Everything starts with a process"
_______________________________________________________________

bin :-binaries--> cd (shell command) -> c program -> 01010

cd , ls :-built in commands which  helps to navigate in shell
man:- is a command used to read the manual

ls:-list the directory
cd:- change directory
pwd:- present working directory
mkdir:- make directory
cat:- read the file
man:- read the manual of any command 
cp:- copy the file/folder
mv:- move the file/ folder
rm:- remove the file/folder
mv <old name> <new name>:- rename the file/folder
df: disk free 
free :-check system memory (RAM) usage
copy:- cp <source> <destination> 



we cannot create any file/folder in bin/sbin.....but can create in home directory
