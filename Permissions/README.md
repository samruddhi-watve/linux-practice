# 🔐 Linux File Permissions

## Overview

Linux is a multi-user operating system where security is enforced using file and directory permissions. Every file and directory has an owner, an associated group, and a set of permissions that control who can read, write, or execute it.

Understanding Linux permissions is essential for Linux Administrators, Cloud Engineers, DevOps Engineers, System Engineers, and Security Professionals.

---

# Learning Objectives

After completing this module, you will be able to:

- Understand Linux permission model
- Read permission strings
- Use chmod, chown and chgrp
- Work with symbolic and numeric permissions
- Understand ownership
- Secure files and directories
- Troubleshoot permission errors
- Apply permission best practices

---

# Permission Structure

Example

```bash
-rwxr-xr--
```

Breakdown

```
-
rwx
r-x
r--
```

| Part | Meaning |
|------|---------|
| - | File Type |
| rwx | Owner Permission |
| r-x | Group Permission |
| r-- | Others Permission |

---

# File Types

| Symbol | Meaning |
|---------|----------|
| - | Regular File |
| d | Directory |
| l | Symbolic Link |
| c | Character Device |
| b | Block Device |
| p | Named Pipe |
| s | Socket |

Example

```
drwxr-xr-x
```

means Directory.

---

# Permission Meaning

## Read (r)

Allows viewing file contents.

Value

```
4
```

---

## Write (w)

Allows editing the file.

Value

```
2
```

---

## Execute (x)

Allows execution.

Value

```
1
```

---

# Numeric Permission Table

| Number | Permission |
|----------|-------------|
|0|---|
|1|--x|
|2|-w-|
|3|-wx|
|4|r--|
|5|r-x|
|6|rw-|
|7|rwx|

---

# Example

Permission

```
755
```

means

Owner

```
rwx
```

Group

```
r-x
```

Others

```
r-x
```

---

# Another Example

```
644
```

Owner

```
rw-
```

Group

```
r--
```

Others

```
r--
```

---

# Check Permissions

Command

```bash
ls -l
```

Example Output

```
-rw-r--r-- 1 samruddhi users 250 Jul 25 notes.txt
```

Explanation

```
-rw-r--r--
```

Permission

```
samruddhi
```

Owner

```
users
```

Group

---

# Change Permission

Command

```bash
chmod 755 script.sh
```

Verify

```bash
ls -l
```

Output

```
-rwxr-xr-x
```

---

# Read Only File

```bash
chmod 444 notes.txt
```

Nobody can modify the file.

---

# Owner Full Access

```bash
chmod 700 secret.txt
```

Only owner can access.

---

# Remove Execute Permission

```bash
chmod -x script.sh
```

---

# Add Execute Permission

```bash
chmod +x script.sh
```

---

# Add Write Permission

```bash
chmod u+w file.txt
```

---

# Remove Write Permission

```bash
chmod u-w file.txt
```

---

# Give Group Write Access

```bash
chmod g+w project.txt
```

---

# Remove Others Permission

```bash
chmod o-rwx confidential.txt
```

---

# Symbolic Mode

| Symbol | Meaning |
|---------|----------|
|u|User|
|g|Group|
|o|Others|
|a|All|

Examples

```bash
chmod u+x file.sh

chmod g-w file.txt

chmod o-r file.txt

chmod a+r file.txt
```

---

# Numeric Mode

```bash
chmod 755 script.sh
```

```bash
chmod 644 file.txt
```

```bash
chmod 600 passwords.txt
```

```bash
chmod 777 test.txt
```

---

# Common Numeric Permissions

| Permission | Usage |
|-------------|--------|
|777|Full Access (Avoid)|
|755|Scripts & Directories|
|700|Private Files|
|644|Normal Files|
|600|Passwords & Keys|

---

# Change Owner

```bash
sudo chown john file.txt
```

Verify

```bash
ls -l
```

---

# Change Group

```bash
sudo chgrp developers file.txt
```

---

# Change Owner and Group

```bash
sudo chown john:developers file.txt
```

---

# Recursive Permission Change

```bash
chmod -R 755 Project/
```

---

# Recursive Ownership

```bash
sudo chown -R john:developers Project/
```

---

# Directory Permissions

Create

```bash
mkdir Linux
```

Permission

```bash
chmod 755 Linux
```

Meaning

Owner

```
rwx
```

Group

```
r-x
```

Others

```
r-x
```

---

# Why Execute Permission on Directory?

Without execute permission

```
cd Directory
```

will fail.

---

# Permission Denied Error

Example

```
bash: ./script.sh: Permission denied
```

Solution

```bash
chmod +x script.sh
```

Run

```bash
./script.sh
```

---

# Another Error

```
cannot open file
```

Check

```bash
ls -l
```

Correct permission if necessary.

---

# Best Practices

✅ Never use 777 unless absolutely required.

✅ Use 644 for normal files.

✅ Use 755 for executable scripts.

✅ Keep private files as 600.

✅ Change ownership carefully.

✅ Verify permissions after using chmod.

---

# Real-world Examples

### Example 1

Private SSH Key

```
600
```

---

### Example 2

Shell Script

```
755
```

---

### Example 3

HTML File

```
644
```

---

### Example 4

Configuration File

```
640
```

---

### Example 5

User Home Directory

```
700
```

---

# Practice Tasks

✔ Create a file

✔ Check permission

✔ Change to 755

✔ Change to 644

✔ Remove execute permission

✔ Add execute permission

✔ Change owner

✔ Change group

✔ Verify changes

---

# Interview Questions

### What is chmod?

Used to change file permissions.

---

### What is chown?

Changes file ownership.

---

### What is chgrp?

Changes the group ownership of a file.

---

### Difference between 755 and 777?

755:
- Owner has full access.
- Group and others can only read and execute.

777:
- Everyone has full access.
- Not recommended because it is insecure.

---

### What does 644 mean?

Owner: Read & Write

Group: Read

Others: Read

---

### What does execute permission do?

Allows a file to be run as a program or script. For directories, it allows users to enter the directory.

---

# Summary

In this module you learned:

- Linux permission model
- Owner, Group and Others
- Numeric permissions
- Symbolic permissions
- chmod
- chown
- chgrp
- Recursive permissions
- Directory permissions
- Best practices
- Common errors
- Interview questions

These concepts are fundamental for Linux Administration, Cloud Support, DevOps, and Infrastructure Engineering roles.

---

# Advanced Linux Permissions

Linux provides advanced permission mechanisms beyond basic read, write, and execute permissions. These features are essential for system administrators to manage shared directories, executables, and fine-grained access control.

---

# Understanding umask

## What is umask?

`umask` (User File Creation Mask) determines the default permissions assigned to newly created files and directories.

Default Permissions

| Object | Default Permission |
|---------|-------------------|
| File | 666 |
| Directory | 777 |

The umask value removes permissions from these defaults.

---

## Check Current umask

```bash
umask
```

Example Output

```text
0022
```

---

## How umask Works

Default file permission:

```text
666
```

umask:

```text
022
```

Final permission:

```text
644
```

---

Default directory permission:

```text
777
```

umask:

```text
022
```

Final permission:

```text
755
```

---

## Change umask Temporarily

```bash
umask 027
```

Now

Files

```
640
```

Directories

```
750
```

---

## Make umask Permanent

Ubuntu

```bash
nano ~/.bashrc
```

Add

```bash
umask 027
```

Reload

```bash
source ~/.bashrc
```

---

# Special Permissions

Linux supports three special permissions.

1. SUID

2. SGID

3. Sticky Bit

---

# SUID (Set User ID)

## Purpose

When SUID is set on an executable, it runs with the permissions of the file owner instead of the user executing it.

Example

```bash
ls -l /usr/bin/passwd
```

Output

```text
-rwsr-xr-x
```

Notice

```
s
```

instead of

```
x
```

---

## Set SUID

```bash
chmod u+s program
```

Numeric

```bash
chmod 4755 program
```

Remove

```bash
chmod u-s program
```

---

## Real-world Example

The `passwd` command needs temporary root privileges to update `/etc/shadow`, so it uses the SUID bit.

---

# SGID (Set Group ID)

## Purpose

When SGID is set on a directory, all new files created inside inherit the directory's group.

---

## Set SGID

```bash
chmod g+s SharedFolder
```

Numeric

```bash
chmod 2755 SharedFolder
```

---

## Verify

```bash
ls -ld SharedFolder
```

Output

```text
drwxr-sr-x
```

---

## Practical Example

Create project directory

```bash
mkdir Project
```

Assign group

```bash
sudo chgrp developers Project
```

Enable SGID

```bash
chmod g+s Project
```

Now every new file belongs to the `developers` group automatically.

---

# Sticky Bit

## Purpose

Allows users to delete only their own files inside a shared directory.

---

Example

```bash
/tmp
```

Permissions

```text
drwxrwxrwt
```

Notice

```
t
```

---

## Set Sticky Bit

```bash
chmod +t SharedFolder
```

Numeric

```bash
chmod 1777 SharedFolder
```

Remove

```bash
chmod -t SharedFolder
```

---

## Real-world Example

Shared upload folders

```
/tmp
```

College computer labs

Shared team directories

---

# stat Command

Displays detailed information about files.

```bash
stat file.txt
```

Example Output

```
File
Size
Permissions
Owner
Group
Access Time
Modify Time
```

---

# Access Control Lists (ACL)

ACL allows permissions for specific users and groups without changing ownership.

---

## Install ACL

Ubuntu

```bash
sudo apt install acl
```

---

## Check ACL

```bash
getfacl file.txt
```

---

## Grant User Permission

```bash
setfacl -m u:john:rwx file.txt
```

---

## Grant Group Permission

```bash
setfacl -m g:developers:r-x file.txt
```

---

## Remove ACL

```bash
setfacl -b file.txt
```

---

## View ACL

```bash
getfacl file.txt
```

---

# Permission Calculation

Read

```
4
```

Write

```
2
```

Execute

```
1
```

Example

Owner

```
rwx
```

```
4+2+1=7
```

Group

```
r-x
```

```
4+1=5
```

Others

```
r--
```

```
4
```

Permission

```
754
```

---

# Security Best Practices

- Never use `777` on production servers.
- Use `600` for SSH private keys.
- Use `644` for configuration files unless stricter permissions are required.
- Use `755` for executable scripts and directories.
- Use SGID for collaborative project directories.
- Use Sticky Bit for shared writable directories.
- Audit permissions regularly using `find` and `stat`.

---

# Common Permission Errors

## Permission denied

```text
Permission denied
```

Possible Causes

- Missing execute permission
- Wrong owner
- Wrong group
- Missing ACL
- Parent directory lacks execute permission

---

## Script Not Executing

Check

```bash
ls -l script.sh
```

Fix

```bash
chmod +x script.sh
```

---

## Cannot Write to File

Check owner

```bash
ls -l
```

Fix

```bash
sudo chown username file.txt
```

or

```bash
chmod u+w file.txt
```

---

# Practical Labs

## Lab 1

Create directory

```bash
mkdir LinuxLab
```

Create files

```bash
touch file1 file2 file3
```

Change permission

```bash
chmod 755 file1
chmod 644 file2
chmod 600 file3
```

Verify

```bash
ls -l
```

---

## Lab 2

Create user

```bash
sudo adduser clouduser
```

Assign ownership

```bash
sudo chown clouduser file1
```

Verify

```bash
ls -l
```

---

## Lab 3

Create shared directory

```bash
mkdir Shared
```

Assign group

```bash
sudo chgrp developers Shared
```

Enable SGID

```bash
chmod 2775 Shared
```

---

## Lab 4

Create upload folder

```bash
mkdir Upload
```

Apply Sticky Bit

```bash
chmod 1777 Upload
```

---

# Interview Questions

### What is umask?

It defines the default permissions for newly created files and directories.

---

### What is SUID?

Runs an executable with the owner's privileges.

---

### What is SGID?

Makes new files inherit the directory's group.

---

### What is Sticky Bit?

Allows users to delete only their own files in a shared directory.

---

### Difference between chmod and chown?

- `chmod` changes permissions.
- `chown` changes ownership.

---

### Difference between symbolic and numeric permissions?

- Symbolic uses letters (`u`, `g`, `o`, `+`, `-`, `=`).
- Numeric uses octal values like `755` or `644`.

---

### Why should SSH private keys have permission 600?

To ensure only the owner can read and modify the key, preventing unauthorized access.

---

# Quick Cheat Sheet

| Task | Command |
|------|---------|
| Check permissions | `ls -l` |
| Change permission | `chmod 755 file` |
| Make executable | `chmod +x file` |
| Change owner | `chown user file` |
| Change group | `chgrp group file` |
| Change owner & group | `chown user:group file` |
| Check umask | `umask` |
| Set umask | `umask 022` |
| View file details | `stat file` |
| Set SUID | `chmod 4755 file` |
| Set SGID | `chmod 2755 dir` |
| Set Sticky Bit | `chmod 1777 dir` |
| View ACL | `getfacl file` |
| Set ACL | `setfacl -m u:user:rwx file` |

---

# Conclusion

Linux permissions are the foundation of system security. Mastering standard permissions, ownership, `umask`, SUID, SGID, Sticky Bit, and ACLs enables administrators to build secure, collaborative, and maintainable systems. These topics are frequently tested in Linux Administrator, Cloud Support, DevOps, and AWS interviews.
