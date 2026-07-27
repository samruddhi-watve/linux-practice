# 🐚 Linux Shell Scripting (Part 1)

## Overview

Shell scripting is one of the most important skills for Linux Administrators, Cloud Engineers, DevOps Engineers, and Site Reliability Engineers (SREs). It allows you to automate repetitive tasks, manage servers, monitor systems, and simplify administration.

A shell script is a text file containing Linux commands executed sequentially by the Bash shell.

---

# Learning Objectives

After completing this module, you will be able to:

- Understand Shell Scripting
- Write your first Bash script
- Use variables
- Read user input
- Display output
- Perform arithmetic operations
- Use conditional statements
- Work with comments
- Use command-line arguments

---

# What is Bash?

Bash stands for **Bourne Again Shell**.

It is the default shell on most Linux distributions.

Check current shell

```bash
echo $SHELL
```

Example Output

```
/bin/bash
```

---

# Check Bash Version

```bash
bash --version
```

---

# Create First Script

```bash
nano hello.sh
```

Add

```bash
#!/bin/bash

echo "Hello World"
```

Save

```
CTRL + O

ENTER

CTRL + X
```

---

# Make Script Executable

```bash
chmod +x hello.sh
```

---

# Run Script

```bash
./hello.sh
```

Output

```
Hello World
```

---

# Shebang

Every Bash script should begin with

```bash
#!/bin/bash
```

It tells Linux which interpreter should execute the script.

---

# Comments

Single-line comment

```bash
# This is a comment
```

Example

```bash
#!/bin/bash

# Display welcome message

echo "Welcome"
```

---

# Printing Output

```bash
echo "Linux"
```

```bash
printf "Linux\n"
```

---

# Variables

Create Variable

```bash
name="Samruddhi"
```

Display

```bash
echo $name
```

Output

```
Samruddhi
```

---

# Rules for Variables

✔ No spaces around =

Correct

```bash
city="Pune"
```

Wrong

```bash
city = Pune
```

---

# Multiple Variables

```bash
name="Samruddhi"

course="Linux"

city="Pune"
```

Display

```bash
echo $name

echo $course

echo $city
```

---

# Read User Input

```bash
#!/bin/bash

echo "Enter your name"

read name

echo "Welcome $name"
```

Output

```
Enter your name

Samruddhi

Welcome Samruddhi
```

---

# Read Multiple Values

```bash
read first second
```

---

# Read Password

```bash
read -s password
```

---

# Command Substitution

Store command output

```bash
today=$(date)
```

Display

```bash
echo $today
```

---

# Environment Variables

Display username

```bash
echo $USER
```

Current directory

```bash
echo $PWD
```

Home directory

```bash
echo $HOME
```

Current shell

```bash
echo $SHELL
```

Hostname

```bash
echo $HOSTNAME
```

---

# Arithmetic Operations

```bash
a=10

b=5

echo $((a+b))
```

Addition

```bash
echo $((a+b))
```

Subtraction

```bash
echo $((a-b))
```

Multiplication

```bash
echo $((a*b))
```

Division

```bash
echo $((a/b))
```

Modulus

```bash
echo $((a%b))
```

---

# expr Command

```bash
expr 10 + 5
```

---

# If Statement

```bash
#!/bin/bash

age=20

if [ $age -ge 18 ]
then
echo "Eligible"
fi
```

---

# If Else

```bash
#!/bin/bash

marks=45

if [ $marks -ge 35 ]
then
echo "Pass"
else
echo "Fail"
fi
```

---

# If Else If

```bash
#!/bin/bash

marks=90

if [ $marks -ge 75 ]
then
echo "Distinction"

elif [ $marks -ge 60 ]
then
echo "First Class"

else
echo "Pass"

fi
```

---

# Comparison Operators

| Operator | Meaning |
|----------|----------|
| -eq | Equal |
| -ne | Not Equal |
| -gt | Greater Than |
| -lt | Less Than |
| -ge | Greater or Equal |
| -le | Less or Equal |

Example

```bash
if [ 20 -gt 10 ]
then
echo "True"
fi
```

---

# String Comparison

Equal

```bash
if [ "$name" = "Samruddhi" ]
```

Not Equal

```bash
if [ "$name" != "Admin" ]
```

Empty String

```bash
if [ -z "$name" ]
```

Not Empty

```bash
if [ -n "$name" ]
```

---

# Logical Operators

AND

```bash
&&
```

OR

```bash
||
```

NOT

```bash
!
```

---

# Command Line Arguments

Example Script

```bash
#!/bin/bash

echo $1

echo $2
```

Run

```bash
./demo.sh Linux AWS
```

Output

```
Linux

AWS
```

---

# Special Variables

| Variable | Meaning |
|----------|----------|
| $0 | Script Name |
| $1 | First Argument |
| $2 | Second Argument |
| $# | Number of Arguments |
| $@ | All Arguments |
| $$ | Process ID |
| $? | Exit Status |

Example

```bash
echo $#
```

---

# Exit Status

```bash
echo $?
```

0

means success

Non-zero

means error

---

# Sleep Command

```bash
sleep 5
```

Pauses execution for 5 seconds.

---

# Clear Screen

```bash
clear
```

---

# Exit Script

```bash
exit
```

or

```bash
exit 0
```

---

# Real-world Example 1

Greeting Script

```bash
#!/bin/bash

echo "Enter your name"

read name

echo "Welcome $name"

echo "Today is"

date
```

---

# Real-world Example 2

Calculator

```bash
#!/bin/bash

read -p "Enter First Number: " a

read -p "Enter Second Number: " b

echo "Addition = $((a+b))"

echo "Subtraction = $((a-b))"

echo "Multiplication = $((a*b))"

echo "Division = $((a/b))"
```

---

# Common Errors

Permission denied

Solution

```bash
chmod +x script.sh
```

---

Wrong Interpreter

Check

```bash
#!/bin/bash
```

---

Variable Not Displaying

Use

```bash
echo $name
```

not

```bash
echo name
```

---

# Best Practices

- Always use meaningful variable names.
- Add comments for readability.
- Check user input before processing.
- Keep scripts simple and modular.
- Test scripts before running on production systems.

---

# Interview Questions

### What is Bash?

Bash is a Unix shell and command language used to execute commands and scripts.

---

### What is a shell script?

A text file containing a sequence of Linux commands executed by the shell.

---

### What is the purpose of Shebang?

It specifies which interpreter should execute the script.

---

### How do you make a script executable?

```bash
chmod +x script.sh
```

---

### What does `$?` represent?

The exit status of the last executed command.

---

### Difference between `$*` and `$@`?

Both represent all command-line arguments, but `"$@"` preserves each argument as a separate word, making it safer in scripts.

---

# Practice Tasks

✅ Create your first script

✅ Print your name

✅ Read user input

✅ Perform arithmetic operations

✅ Write an if-else program

✅ Accept command-line arguments

✅ Display environment variables

✅ Check exit status

---

# Summary

In this module, you learned:

- Bash basics
- Shebang
- Variables
- User input
- Environment variables
- Arithmetic
- If/Else conditions
- Comparison operators
- Command-line arguments
- Exit status
- Best practices

  ---

# 🔁 Loops in Bash

Loops allow you to execute a block of code repeatedly until a condition is met.

Types of loops:

- for loop
- while loop
- until loop
- select loop (advanced)

---

# for Loop

Syntax

```bash
for variable in list
do
    commands
done
```

Example

```bash
#!/bin/bash

for i in 1 2 3 4 5
do
    echo $i
done
```

Output

```
1
2
3
4
5
```

---

# for Loop with Range

```bash
for i in {1..10}
do
    echo $i
done
```

---

# for Loop with Step

```bash
for i in {0..20..2}
do
    echo $i
done
```

Output

```
0
2
4
6
8
10
12
14
16
18
20
```

---

# C Style for Loop

```bash
for ((i=1;i<=5;i++))
do
    echo $i
done
```

---

# Loop Through Files

```bash
for file in *.txt
do
    echo $file
done
```

---

# Loop Through Directories

```bash
for dir in */
do
    echo $dir
done
```

---

# while Loop

Runs until the condition becomes false.

Syntax

```bash
while [ condition ]
do
    commands
done
```

Example

```bash
count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count+1))
done
```

---

# Infinite while Loop

```bash
while true
do
    echo "Running..."
done
```

Stop

```
Ctrl + C
```

---

# Reading File Line by Line

```bash
while read line
do
    echo $line
done < file.txt
```

---

# until Loop

Runs until condition becomes true.

```bash
count=1

until [ $count -gt 5 ]
do
    echo $count
    count=$((count+1))
done
```

---

# break Statement

Stops loop immediately.

```bash
for i in {1..10}
do
    if [ $i -eq 5 ]
    then
        break
    fi

    echo $i
done
```

Output

```
1
2
3
4
```

---

# continue Statement

Skips current iteration.

```bash
for i in {1..5}
do
    if [ $i -eq 3 ]
    then
        continue
    fi

    echo $i
done
```

Output

```
1
2
4
5
```

---

# Case Statement

Alternative to multiple if-else conditions.

Syntax

```bash
case variable in
pattern)
commands
;;
esac
```

Example

```bash
read -p "Enter choice: " choice

case $choice in

1)
echo "Linux"
;;

2)
echo "AWS"
;;

3)
echo "Docker"
;;

*)
echo "Invalid Choice"
;;

esac
```

---

# Arrays

Arrays store multiple values.

Create Array

```bash
courses=("Linux" "AWS" "Docker" "Git")
```

Display First Element

```bash
echo ${courses[0]}
```

Display All

```bash
echo ${courses[@]}
```

Display Length

```bash
echo ${#courses[@]}
```

---

# Loop Through Array

```bash
for course in "${courses[@]}"
do
    echo $course
done
```

Output

```
Linux
AWS
Docker
Git
```

---

# Add Array Element

```bash
courses+=("Terraform")
```

---

# Functions

Functions allow reusable code.

Syntax

```bash
function_name(){

commands

}
```

Example

```bash
greet(){

echo "Welcome to Linux"

}

greet
```

---

# Function with Parameters

```bash
greet(){

echo "Welcome $1"

}

greet Samruddhi
```

Output

```
Welcome Samruddhi
```

---

# Return Value

```bash
add(){

result=$(( $1 + $2 ))

echo $result

}

add 10 20
```

---

# Local Variables

```bash
display(){

local name="Linux"

echo $name

}
```

---

# String Length

```bash
name="Samruddhi"

echo ${#name}
```

---

# Convert to Uppercase

```bash
echo ${name^^}
```

---

# Convert to Lowercase

```bash
echo ${name,,}
```

---

# Substring

```bash
echo ${name:0:4}
```

Output

```
Samr
```

---

# Replace String

```bash
echo ${name/Sam/Linux}
```

---

# Check Empty String

```bash
if [ -z "$name" ]
then
echo "Empty"
fi
```

---

# Check Non-empty String

```bash
if [ -n "$name" ]
then
echo "Available"
fi
```

---

# File Tests

Check File Exists

```bash
if [ -f file.txt ]
then
echo "Exists"
fi
```

Directory Exists

```bash
if [ -d Linux ]
then
echo "Directory Found"
fi
```

Readable

```bash
-r
```

Writable

```bash
-w
```

Executable

```bash
-x
```

---

# Practical Example 1

Display Numbers

```bash
#!/bin/bash

for i in {1..20}
do
echo $i
done
```

---

# Practical Example 2

Create Multiple Files

```bash
#!/bin/bash

for i in {1..5}
do
touch file$i.txt
done
```

---

# Practical Example 3

Backup All Log Files

```bash
#!/bin/bash

mkdir backup

cp *.log backup/
```

---

# Practical Example 4

Check Directory Exists

```bash
#!/bin/bash

if [ -d Linux ]
then

echo "Directory Found"

else

mkdir Linux

fi
```

---

# Best Practices

- Keep functions small and reusable.
- Use meaningful variable names.
- Quote variables to avoid word splitting.
- Prefer `$(command)` over backticks.
- Indent code consistently.
- Handle errors explicitly.

---

# Common Errors

### Syntax Error

Cause

Missing `then`, `fi`, `do`, or `done`.

Solution

Verify script structure.

---

### Infinite Loop

Cause

Loop variable never changes.

Solution

Update the loop variable or add a proper exit condition.

---

### Array Index Error

Check array length

```bash
echo ${#array[@]}
```

---

# Interview Questions

### Difference between for and while loop?

- `for` is best when the number of iterations is known.
- `while` is used when the loop depends on a condition.

---

### What is a function?

A reusable block of code that performs a specific task.

---

### What is an array?

A collection of multiple values stored under a single variable name.

---

### What does break do?

Terminates the current loop immediately.

---

### What does continue do?

Skips the current iteration and proceeds to the next one.

---

### Difference between case and if?

- `if` evaluates conditions.
- `case` is cleaner when checking one variable against multiple values.

---

# Hands-on Practice

✅ Print numbers from 1 to 100

✅ Create 10 directories using a loop

✅ Read a file line by line

✅ Create an array of Linux commands

✅ Write a function to calculate the square of a number

✅ Use a case statement to create a simple menu

✅ Check if a file exists before copying it

---

# Summary

In this module, you learned:

- for loops
- while loops
- until loops
- break & continue
- case statements
- arrays
- functions
- string operations
- file tests
- practical automation examples
- interview questions
- Bash scripting best practices

These concepts are widely used in Linux automation, Cloud Support, DevOps pipelines, and day-to-day system administration.
---

# 🚀 Advanced Shell Scripting

## Overview

Advanced shell scripting is used to automate real-world system administration tasks such as backups, log rotation, disk monitoring, user management, health checks, process monitoring, and report generation.

These concepts are commonly used by Linux Administrators, Cloud Engineers, DevOps Engineers, and SREs.

---

# Script Debugging

## Run in Debug Mode

```bash
bash -x script.sh
```

Example

```bash
#!/bin/bash

name="Linux"

echo $name
```

Run

```bash
bash -x script.sh
```

Output

```
+ name=Linux
+ echo Linux
Linux
```

---

# Exit on Error

```bash
set -e
```

Stops the script immediately if any command fails.

Example

```bash
#!/bin/bash

set -e

mkdir backup

cp data.txt backup/

echo "Completed"
```

---

# Undefined Variable Check

```bash
set -u
```

Prevents use of undefined variables.

---

# Trace Every Command

```bash
set -x
```

Disable

```bash
set +x
```

---

# Trap Command

Used to execute cleanup tasks before exiting.

Example

```bash
trap "echo Script Interrupted" INT
```

Press

```
CTRL + C
```

Output

```
Script Interrupted
```

---

# Logging

Store output inside a log file.

```bash
echo "Backup Started" >> backup.log
```

Timestamp

```bash
echo "$(date) Backup Completed" >> backup.log
```

---

# Redirect Output

Overwrite

```bash
command > output.txt
```

Append

```bash
command >> output.txt
```

Redirect Errors

```bash
command 2> error.log
```

Both Output and Errors

```bash
command > output.log 2>&1
```

---

# Reading File

```bash
cat users.txt
```

Read line by line

```bash
while read line
do
echo $line
done < users.txt
```

---

# Count Lines

```bash
wc -l users.txt
```

---

# Search in File

```bash
grep Linux users.txt
```

Ignore Case

```bash
grep -i linux users.txt
```

Count Matches

```bash
grep -c Linux users.txt
```

---

# cut Command

Extract first column

```bash
cut -d ":" -f1 /etc/passwd
```

---

# sort Command

```bash
sort names.txt
```

Reverse

```bash
sort -r names.txt
```

Unique

```bash
sort -u names.txt
```

---

# uniq Command

```bash
uniq names.txt
```

Count

```bash
uniq -c names.txt
```

---

# head Command

```bash
head file.txt
```

First five lines

```bash
head -5 file.txt
```

---

# tail Command

```bash
tail file.txt
```

Live Monitoring

```bash
tail -f /var/log/syslog
```

---

# sed Command

Replace text

```bash
sed 's/Linux/AWS/' file.txt
```

Replace all occurrences

```bash
sed 's/Linux/AWS/g' file.txt
```

---

# awk Command

Print first column

```bash
awk '{print $1}' file.txt
```

Print first and third columns

```bash
awk '{print $1,$3}' file.txt
```

---

# xargs

Delete all txt files

```bash
find . -name "*.txt" | xargs rm
```

---

# Regular Expressions

Starts with A

```bash
grep "^A" file.txt
```

Ends with n

```bash
grep "n$" file.txt
```

Contains digits

```bash
grep "[0-9]" file.txt
```

---

# File Backup Script

```bash
#!/bin/bash

SOURCE=/home/user/Documents

DEST=/home/user/Backup

mkdir -p $DEST

cp -r $SOURCE/* $DEST

echo "Backup Completed"
```

---

# Disk Usage Script

```bash
#!/bin/bash

df -h
```

---

# Memory Usage Script

```bash
#!/bin/bash

free -h
```

---

# CPU Usage Script

```bash
#!/bin/bash

top -bn1 | head -10
```

---

# System Health Check

```bash
#!/bin/bash

echo "Hostname"

hostname

echo

echo "Disk"

df -h

echo

echo "Memory"

free -h

echo

echo "CPU"

lscpu
```

---

# User Creation Script

```bash
#!/bin/bash

read -p "Username: " user

sudo adduser $user

echo "User Created"
```

---

# User Deletion Script

```bash
#!/bin/bash

read -p "Username: " user

sudo userdel -r $user
```

---

# Ping Check Script

```bash
#!/bin/bash

ping -c 2 google.com

if [ $? -eq 0 ]
then

echo "Internet Available"

else

echo "No Internet"

fi
```

---

# Service Status Script

```bash
#!/bin/bash

systemctl status ssh
```

---

# Restart Service Script

```bash
#!/bin/bash

sudo systemctl restart nginx
```

---

# File Exists Script

```bash
#!/bin/bash

if [ -f test.txt ]
then

echo "File Exists"

else

echo "Not Found"

fi
```

---

# Directory Exists Script

```bash
#!/bin/bash

if [ -d Linux ]
then

echo "Directory Exists"

else

mkdir Linux

fi
```

---

# Log Cleanup Script

```bash
#!/bin/bash

find /var/log -name "*.log" -mtime +30 -delete
```

---

# Find Large Files

```bash
find / -size +500M
```

---

# Display Top 10 Processes

```bash
ps -eo pid,comm,%cpu --sort=-%cpu | head
```

---

# Display Top Memory Processes

```bash
ps -eo pid,comm,%mem --sort=-%mem | head
```

---

# Network Check Script

```bash
#!/bin/bash

ping -c 3 8.8.8.8
```

---

# SSH Connection Test

```bash
#!/bin/bash

ssh user@server
```

---

# Compress Backup

```bash
#!/bin/bash

tar -czvf backup.tar.gz Backup/
```

---

# Extract Backup

```bash
tar -xzvf backup.tar.gz
```

---

# Automation Example

Daily Backup

```bash
0 2 * * * /home/user/backup.sh
```

Runs every day at 2 AM.

---

# Best Practices

- Use meaningful variable names.
- Validate user input.
- Check command exit status.
- Log important operations.
- Keep scripts modular.
- Test in a non-production environment.
- Use comments to explain complex logic.

---

# Common Errors

## Permission Denied

Solution

```bash
chmod +x script.sh
```

---

## Command Not Found

Check

```bash
which command
```

Install if missing.

---

## No Such File

Verify path

```bash
pwd

ls
```

---

## Variable Empty

Check

```bash
echo $variable
```

---

# Interview Questions

### What is `set -e`?

Stops script execution when a command fails.

---

### What is `trap`?

Executes a command when the script receives a signal or exits.

---

### Difference between `awk` and `sed`?

- `awk` is mainly used for processing structured text and fields.
- `sed` is mainly used for editing and replacing text.

---

### What is `grep`?

A command used to search for text matching a pattern.

---

### What is output redirection?

Redirecting command output to a file using `>` or `>>`.

---

### Why use logging in scripts?

To record execution details, troubleshoot failures, and maintain audit trails.

---

# Hands-on Practice

✅ Create a backup script

✅ Create a health check script

✅ Monitor disk usage

✅ Monitor memory usage

✅ Search logs using grep

✅ Replace text using sed

✅ Extract columns using awk

✅ Schedule backup using cron

✅ Create a user using a script

✅ Find large files

---

# Cheat Sheet

| Task | Command |
|------|---------|
| Debug Script | `bash -x script.sh` |
| Exit on Error | `set -e` |
| Debug Mode | `set -x` |
| Read File | `while read line` |
| Search Text | `grep` |
| Replace Text | `sed` |
| Process Columns | `awk` |
| Extract Fields | `cut` |
| Sort | `sort` |
| Remove Duplicates | `uniq` |
| Follow Logs | `tail -f` |
| Find Files | `find` |
| Archive | `tar -czvf` |
| Extract | `tar -xzvf` |
| Schedule | `crontab -e` |

---

# Summary

In this module, you learned:

- Script debugging
- Error handling
- Logging
- File processing
- Text processing with grep, sed, awk, cut
- Regular expressions
- Output redirection
- Automation scripts
- System health monitoring
- Backup automation
- Best practices
- Interview questions

These concepts are extensively used in Linux administration, DevOps automation, Cloud Support, CI/CD pipelines, and production server management.
# 🚀 Real-World Bash Automation Scripts

## Overview

This section contains practical Bash scripts used by Linux Administrators, Cloud Engineers, DevOps Engineers, and Site Reliability Engineers (SREs) to automate routine system administration tasks.

---

# 1. System Health Check

```bash
#!/bin/bash

echo "========== SYSTEM HEALTH REPORT =========="

echo "Hostname: $(hostname)"
echo "Current Date: $(date)"
echo

echo "========== UPTIME =========="
uptime

echo

echo "========== CPU =========="
lscpu | grep "Model name"

echo

echo "========== MEMORY =========="
free -h

echo

echo "========== DISK =========="
df -h

echo

echo "========== LOAD =========="
uptime

echo

echo "========== TOP CPU =========="
ps -eo pid,user,%cpu,%mem,comm --sort=-%cpu | head

echo

echo "========== NETWORK =========="
ip addr show
```

---

# 2. Automatic Backup Script

```bash
#!/bin/bash

SOURCE="/home/$USER/Documents"

DEST="/home/$USER/Backup"

DATE=$(date +%F)

mkdir -p "$DEST"

tar -czf "$DEST/backup-$DATE.tar.gz" "$SOURCE"

echo "Backup completed successfully."
```

---

# 3. Disk Space Monitoring

```bash
#!/bin/bash

THRESHOLD=80

df -h | awk 'NR>1 {print $5 " " $6}' | while read output
do

usage=$(echo $output | awk '{print $1}' | cut -d'%' -f1)

partition=$(echo $output | awk '{print $2}')

if [ $usage -ge $THRESHOLD ]
then

echo "WARNING: $partition is ${usage}% full"

fi

done
```

---

# 4. Memory Usage Monitor

```bash
#!/bin/bash

free -h

echo

echo "Top Memory Processes"

ps -eo pid,user,%mem,comm --sort=-%mem | head
```

---

# 5. CPU Usage Monitor

```bash
#!/bin/bash

top -bn1 | head -20
```

---

# 6. Internet Connectivity Check

```bash
#!/bin/bash

HOST="8.8.8.8"

if ping -c 3 $HOST > /dev/null
then

echo "Internet Connection Available"

else

echo "Internet Connection Failed"

fi
```

---

# 7. Website Monitoring

```bash
#!/bin/bash

URL="https://google.com"

STATUS=$(curl -o /dev/null -s -w "%{http_code}" $URL)

echo "HTTP Status: $STATUS"
```

---

# 8. Service Status Checker

```bash
#!/bin/bash

SERVICE=ssh

systemctl is-active --quiet $SERVICE

if [ $? -eq 0 ]
then

echo "$SERVICE is Running"

else

echo "$SERVICE is Stopped"

fi
```

---

# 9. Restart Failed Service

```bash
#!/bin/bash

SERVICE=nginx

systemctl restart $SERVICE

systemctl status $SERVICE
```

---

# 10. Create Linux User

```bash
#!/bin/bash

read -p "Enter Username: " USERNAME

sudo useradd -m $USERNAME

echo "User Created Successfully"
```

---

# 11. Delete Linux User

```bash
#!/bin/bash

read -p "Username: " USERNAME

sudo userdel -r $USERNAME

echo "User Deleted"
```

---

# 12. Password Expiry Check

```bash
#!/bin/bash

chage -l $USER
```

---

# 13. Failed Login Report

```bash
#!/bin/bash

lastb
```

---

# 14. Active User Report

```bash
#!/bin/bash

who

echo

w
```

---

# 15. Find Large Files

```bash
#!/bin/bash

find / -type f -size +500M 2>/dev/null
```

---

# 16. Delete Old Log Files

```bash
#!/bin/bash

find /var/log -name "*.log" -mtime +30 -delete
```

---

# 17. Compress Directory

```bash
#!/bin/bash

tar -czvf backup.tar.gz Documents/
```

---

# 18. Extract Archive

```bash
#!/bin/bash

tar -xzvf backup.tar.gz
```

---

# 19. Process Monitor

```bash
#!/bin/bash

ps aux --sort=-%cpu | head

echo

ps aux --sort=-%mem | head
```

---

# 20. Open Ports Report

```bash
#!/bin/bash

ss -tulnp
```

---

# 21. Package Update (Ubuntu)

```bash
#!/bin/bash

sudo apt update

sudo apt upgrade -y
```

---

# 22. Network Information

```bash
#!/bin/bash

hostname -I

ip route

ip addr
```

---

# 23. SSH Connectivity Test

```bash
#!/bin/bash

HOST=192.168.1.10

ssh $HOST
```

---

# 24. Display Logged-in Users

```bash
#!/bin/bash

users

who

w
```

---

# 25. Display Kernel Information

```bash
#!/bin/bash

uname -a
```

---

# 26. Display OS Information

```bash
#!/bin/bash

cat /etc/os-release
```

---

# 27. File Integrity Check

```bash
#!/bin/bash

sha256sum file.txt
```

---

# 28. Backup MySQL Database

```bash
#!/bin/bash

mysqldump -u root -p database_name > backup.sql
```

---

# 29. Search Errors in Logs

```bash
#!/bin/bash

grep -i error /var/log/syslog
```

---

# 30. Daily System Report

```bash
#!/bin/bash

echo "System Report"

echo

hostname

echo

date

echo

uptime

echo

free -h

echo

df -h
```

---

# Recommended Repository Structure

```
Shell-Scripting/

│── README.md

│── scripts/

│     ├── backup.sh
│     ├── health_check.sh
│     ├── disk_monitor.sh
│     ├── memory_monitor.sh
│     ├── cpu_monitor.sh
│     ├── internet_check.sh
│     ├── website_monitor.sh
│     ├── service_status.sh
│     ├── restart_service.sh
│     ├── create_user.sh
│     ├── delete_user.sh
│     ├── active_users.sh
│     ├── failed_login.sh
│     ├── package_update.sh
│     ├── network_info.sh
│     ├── kernel_info.sh
│     ├── os_info.sh
│     ├── compress.sh
│     ├── extract.sh
│     ├── mysql_backup.sh
│     ├── log_cleanup.sh
│     ├── log_error_check.sh
│     ├── process_monitor.sh
│     ├── open_ports.sh
│     └── system_report.sh
```

---

# Skills Demonstrated

- Bash Scripting
- Linux Administration
- Automation
- Process Monitoring
- User Management
- Backup & Restore
- System Health Monitoring
- Log Management
- Package Management
- Networking
- Service Management
- Cron Automation
- Troubleshooting
- Security Basics
- Production Support

---

# Interview Questions

### Why is shell scripting important?

It automates repetitive tasks, reduces manual effort, minimizes errors, and improves operational efficiency.

---

### Which shell scripts are commonly used in production?

- Backup automation
- Disk monitoring
- Memory monitoring
- Health checks
- Log cleanup
- User provisioning
- Service monitoring
- Database backup
- Network monitoring
- Scheduled maintenance

---

### How are shell scripts scheduled automatically?

Using **cron** (`crontab`) for recurring jobs or **systemd timers** on modern Linux systems.

---

# Summary

This module contains production-oriented Bash automation scripts that demonstrate practical Linux administration skills. These scripts are valuable portfolio examples for Cloud Support, Linux Administrator, DevOps, and Infrastructure Engineer roles.
- Interview questions

These are the building blocks of Bash scripting and are widely used in Linux administration, Cloud Support, DevOps, and automation.
