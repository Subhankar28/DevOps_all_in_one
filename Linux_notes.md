Linux file system hierarchy: 

1. / (Root Directory) 
• The topmost directory in Linux. 
• Everything in the Linux file system is stored under /. 
• Mounted file systems and devices are all accessible from this single directory. 

2. /bin (Binaries) 
• Contains essential binary executables (commands) needed by all users, including system 
administrators. 
• Commonly used commands like ls, cp, mv, rm, cat, echo, mkdir, and rmdir are stored here. 
• These binaries are required for system recovery and are available in single-user mode. 

3. /boot (Boot Loader Files) 
• Stores boot-related files required to start Linux. 
• Contains the Linux kernel (vmlinuz), initial RAM disk (initrd or initramfs), bootloader 
configuration files (like grub.cfg for GRUB). 
• Example files: 
o /boot/vmlinuz – The compressed Linux kernel. 
o /boot/initrd.img – Initial RAM disk image used during boot. 

4. /dev (Device Files) 
• Contains special device files representing hardware and virtual devices. 
• Examples: 
o /dev/sda – First hard disk. 
o /dev/tty – Terminal devices. 
o /dev/null – Discard data. 
o /dev/random – Generate random numbers. 
• These files allow interaction with devices as if they were regular files. 

5. /etc (Configuration Files) 
• Stores system-wide configuration files and shell scripts used during system boot. 
• Examples: 
o /etc/passwd – User account details. 
o /etc/shadow – Encrypted passwords. 
o /etc/fstab – File system mount points. 
o /etc/network/interfaces – Network configuration. 

6. /home (User Home Directories) 
• Contains personal directories for each user. 
• Example: 
o /home/vishal/ – Home directory for user "vishal". 
• Each user has their own configuration files, documents, downloads, and settings in this 
directory. 

7. /lib (System Libraries) 
• Contains shared libraries required by binaries in /bin and /sbin. 
• Includes kernel modules (/lib/modules/). 
• Libraries are similar to Windows .DLL files. 
• Examples: 
o /lib/libc.so.6 – Standard C library. 
o /lib/modules/ – Kernel modules. 

8. /sys (System Information) 
• Exposes kernel and hardware information. 
• Similar to /proc, but more structured. 
• Examples: 
o /sys/class/net/ – Network interfaces. 
o /sys/block/ – Block devices (disks). 

9. /tmp (Temporary Files) 
• Stores temporary files created by applications and users. 
• Data is deleted on system reboot. 
• Example: 
o /tmp/session.log – Temporary session log file. 

10. /usr (User System Resources) 
• Contains user-installed software, libraries, and documentation. 
• Divided into subdirectories: 
o /usr/bin/ – Non-essential command binaries (nano, vim, git). 
o /usr/sbin/ – Non-essential system administration binaries. 
o /usr/lib/ – Shared libraries. 
o /usr/share/ – Documentation, icons, themes. 

11. /var (Variable Data) 
• Stores variable data such as logs, mail, and print queues. 
• Examples: 
o /var/log/ – System logs (syslog, auth.log). 
o /var/mail/ – Email storage. 
o /var/spool/ – Print jobs, cron jobs. 

12. /run (Runtime Data) 
• Stores volatile runtime data since the system booted. 
• Replaces older directories like /var/run/ and /var/lock/. 
• Examples: 
o /run/utmp – Active user sessions. 
o /run/systemd/ – Systemd runtime information. 


Linux file Permissions: 
Each file and directory in Linux have permissions associated with three categories: 
1. Owner (User) – The person who created the file. 
2. Group – A collection of users with shared permissions. 
3. Others – Everyone else who has access to the system. 
Linux uses three types of permissions: 
• Read (r) – Allows reading a file’s contents or listing a directory. 
• Write (w) – Allows modifying or deleting a file, or adding/removing files in a directory. 
• Execute (x) – Allows executing a file (script/program) or accessing a directory. 

# When you run the ls -l command, you see file permissions in the following format: -rwxr-xr-- 1 user group 1234 Aug 20 10:00 myfile.sh 

- File type (- for file, d for directory, l for link)
rwx -> Owner (User) permissions 
r-x -> Group permissions 
r-- -> Others permissions 

rwx   rw-     r-x
user  Group   Other

r=4
w=2
x=1

# So, 777 means = read,write,execute permission is given.

# Linux Shell Command Components: 

1. Arguments 
• Arguments are values passed to a command to specify what it should operate on. 
• Example:  
# cp file1.txt /home/user/ 
o cp is the command. 
o file1.txt is the first argument (source file). 
o /home/user/ is the second argument (destination directory). 

2. Options (Flags) 
• Options modify the behaviour of a command. 
• Example:  
# ls -l --human-readable 
o -l enables long format listing. 
o --human-readable makes file sizes easier to read. 

3. Pipelines (|) 
• Pipes allow the output of one command to be used as the input for another. 
• Example:  
# ls -l | grep "test" 

4. Redirections (>, >>, <) 
• Redirects standard input/output to or from files. 
• Examples:  
# ls > output.txt  # Overwrites 
# ls >> output.txt # Appends 
# sort < file.txt  # Reads from a file 

5. Environment Variables 
• Variables that store data used by the shell and scripts. 
• Example:  
# echo $HOME 

6. Command Substitution ($(), ````) 
• Uses the output of a command as an argument for another. 
• Example:  
# echo "Today is $(date)" 

7. Background Execution (&) 
• Runs commands in the background. 
• Example:  
# sleep 10 & 

8. Job Control (fg, bg, jobs) 
• Manages running jobs. 
• Examples:  
# sleep 100 & 
# jobs 
# fg %1 
# bg %1 

9. Brace Expansion ({}) 
• Generates multiple strings or sequences. 
• Examples:  
# mkdir {dir1,dir2,dir3} 
# echo {1..5} 

10. Wildcard Characters (*, ?, []) 
• Pattern matching in filenames. 
• Examples:  
# ls *.txt 
# ls file?.txt 
# ls file[1-3].txt 

11. Quoting (", ', \) 
• Prevents interpretation of special characters. 
• Examples:  
# echo 'Hello $USER'   
# Prints literally 
echo "Hello $USER"  # Expands variable 
echo "Hello \"World\"" 

12. Shebang (#!) 
• Specifies the interpreter for scripts. 
• Example (myscript.sh):  
#!/bin/bash 
echo "This is a Bash script" 

13. Control Operators (&&, ||, ;) 
• Used for command sequencing. 
• && executes the second command only if the first succeeds. 
• || executes the second command only if the first fails. 
• ; executes commands sequentially, regardless of success or failure. 
• Examples:  
# mkdir test && cd test  # Creates and navigates to test if successful 
# mkdir test || echo "Failed"  # Prints message if mkdir fails 
# echo "Hello"; ls   
# Executes both commands 

14. Process Substitution (<(), >()) 
• Treats the output of a command as a file. 
• Useful for comparing outputs without creating temporary files. 
• Example: Compares the file listings of two directories. 
# diff <(ls /dir1) <(ls /dir2) 

15. Tilde Expansion (~) 
• Represents the home directory. 
• Example:  
# cd ~  # Navigates to the home directory 

16. Arithmetic Expansion ($(( ))) 
• Performs arithmetic calculations inside shell scripts. 
• Example:  
# echo $((5 + 3)) # Outputs 8 

17. Aliases 
• Shortcuts for longer commands. 
• Example:  
# alias ll="ls -la" 
# ll  # Runs 'ls -la' 

18. Functions 
• Define reusable command sequences. 
• Functions allow writing custom commands inside scripts or interactive shells. 
• Example:  
# myfunc() { 
# echo "Hello, $1" 
# } 
# myfunc Vishal # Prints 'Hello, Vishal' 

# Shell Scripting: 

1. echo 
The echo command is used to display a line of text or a variable value on the terminal. It is 
commonly used in shell scripts to provide output messages to users. 
Syntax: 
echo [OPTIONS] [STRING] 
Common Options: 
# • -n : Do not output the trailing newline. 
# • -e : Enable interpretation of backslash escapes. 

Example: 
# echo "Hello, World!" 
# echo -n "Hello, No New Line" 
# echo -e "Line1\nLine2" 

2. read 
The read command is used to take user input from the terminal. It waits for the user to enter input 
and stores it in a variable. 
Syntax: 
read [OPTIONS] [VARIABLE] 
Common Options: 
# • -p : Prompt the user with a message. 
# • -s : Silent mode (useful for password input). 
Example: 
# read -p "Enter your name: " name 
# echo "Hello, $name" 

3. if Statement 
The if statement is used to execute a block of commands conditionally. It is useful for decision
making in scripts. 
Syntax: 
if [ condition ]; then 
commands 
elif [ condition ]; then 
commands 
else 
commands 
fi 
Example: 
# num=10 
# if [ $num -gt 5 ]; then 
# echo "Number is greater than 5" 
# else 
# echo "Number is 5 or less" 
# fi 

4. for Loop 
The for loop is used to iterate over a sequence of values. It simplifies repetitive tasks. 
Syntax: 
for var in list; do 
commands 
done 
Example: 
# for i in 1 2 3 4 5; do 
# echo "Iteration: $i" 
# done 

5. while Loop: The while loop repeatedly executes a block of commands as long as a condition is 
true. 
Syntax: 
while [ condition ]; do 
commands 
done 
Example: 
# count=1 
# while [ $count -le 5 ]; do 
# echo "Count: $count" 
# count=$((count + 1)) 
# done 

6. case Statement: The case statement is used for pattern matching and is an alternative to 
multiple if-elif conditions. 
Syntax: 
case variable in 
pattern1) 
commands ;; 
pattern2) 
commands ;; 
*) 
default commands ;; 
esac 
Example: 
# read -p "Enter a letter: " letter 
# case $letter in 
# a) echo "You entered A" ;; 
# b) echo "You entered B" ;; 
# *) echo "Unknown letter" ;; 
# esac 

7. function in Shell Script: Functions in shell scripting allow you to define reusable blocks of code. 
Syntax: 
function_name() { 
commands 
} 
Example: 
# hello() { 
# echo "Hello, World!" 
# } 
# 

