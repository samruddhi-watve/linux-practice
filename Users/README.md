# 👤 Linux User Management

## Overview

Linux is a multi-user operating system, meaning multiple users can access the same system simultaneously. Each user has a unique identity, permissions, home directory, and security settings.

User management is a critical responsibility for Linux System Administrators, Cloud Engineers, DevOps Engineers, and Infrastructure Engineers.

---

# Learning Objectives

After completing this module, you will be able to:

- Understand Linux users and groups
- Create, modify, and delete users
- Manage passwords
- Manage groups
- Grant sudo privileges
- Lock and unlock accounts
- Understand user IDs (UID)
- Understand group IDs (GID)
- Configure user environments
- Troubleshoot user-related issues

---

# Types of Users

Linux has three main types of users.

## 1. Root User

- Superuser
- Full administrative privileges
- UID = 0
- Can access every file

Example

```bash
root
```

---

## 2. Regular User

Created for normal daily activities.

Example

```bash
samruddhi
```

---

## 3. System User

Used by services and applications.

Examples

```
mysql
www-data
nginx
daemon
```

These users usually cannot log in.

---

# Important User Files

| File | Description |
|------|-------------|
| /etc/passwd | User account information |
| /etc/shadow | Encrypted passwords |
| /etc/group | Group information |
| /etc/gshadow | Secure group passwords |
| /home | User home directories |
| /root | Root home directory |

---

# Check Current User

```bash
whoami
```

Output

```
samruddhi
```

Displays the currently logged-in user.

---

# Display User ID

```bash
id
```

Example

```
uid=1000(samruddhi)
gid=1000(samruddhi)
groups=1000(samruddhi),27(sudo)
```

---

# Display Login Name

```bash
logname
```

---

# Show Logged-in Users

```bash
who
```

Displays users currently logged into the system.

---

# Display User Activity

```bash
w
```

Shows:

- Logged-in users
- Login time
- Running process
- Load average

---

# Last Logged-in Users

```bash
last
```

Displays login history.

---

# Create User

Ubuntu

```bash
sudo adduser john
```

CentOS/RHEL

```bash
sudo useradd john
```

---

# Set Password

```bash
sudo passwd john
```

---

# Change Current Password

```bash
passwd
```

---

# Switch User

```bash
su john
```

Switch to root

```bash
sudo su
```

or

```bash
su -
```

---

# Delete User

```bash
sudo userdel john
```

---

# Delete User with Home Directory

```bash
sudo userdel -r john
```

---

# Lock User Account

```bash
sudo passwd -l john
```

---

# Unlock User

```bash
sudo passwd -u john
```

---

# Expire Password

```bash
sudo passwd -e john
```

User must change password at next login.

---

# Change Username

```bash
sudo usermod -l newname oldname
```

---

# Change Home Directory

```bash
sudo usermod -d /home/newhome john
```

---

# Create Group

```bash
sudo groupadd developers
```

---

# Delete Group

```bash
sudo groupdel developers
```

---

# Rename Group

```bash
sudo groupmod -n dev developers
```

---

# Add User to Group

```bash
sudo usermod -aG developers john
```

---

# Remove User from Group

```bash
sudo gpasswd -d john developers
```

---

# Display User Groups

```bash
groups john
```

---

# Display Current Groups

```bash
groups
```

---

# Grant Sudo Access

```bash
sudo usermod -aG sudo john
```

Verify

```bash
groups john
```

---

# Remove Sudo Access

```bash
sudo deluser john sudo
```

---

# Check User Information

```bash
finger john
```

(if installed)

---

# Display Home Directory

```bash
echo $HOME
```

---

# Display Username

```bash
echo $USER
```

---

# Display Shell

```bash
echo $SHELL
```

---

# Change Default Shell

```bash
sudo chsh -s /bin/bash john
```

---

# Available Shells

```bash
cat /etc/shells
```

---

# Display Environment Variables

```bash
env
```

---

# Important User Files

```
~/.bashrc
~/.profile
~/.bash_logout
```

These files configure the user's shell environment.

---

# View /etc/passwd

```bash
cat /etc/passwd
```

Example

```
john:x:1001:1001:John:/home/john:/bin/bash
```

Meaning

| Field | Description |
|--------|-------------|
| john | Username |
| x | Password placeholder |
|1001|UID|
|1001|GID|
|John|Comment|
|/home/john|Home Directory|
|/bin/bash|Login Shell|

---

# View Password File

```bash
sudo cat /etc/shadow
```

Contains encrypted passwords.

---

# View Groups

```bash
cat /etc/group
```

---

# Check UID

```bash
id -u
```

---

# Check GID

```bash
id -g
```

---

# Difference Between adduser and useradd

| adduser | useradd |
|----------|----------|
| Friendly command | Low-level command |
| Creates home directory | Doesn't always create home |
| Interactive | Manual configuration |

---

# Best Practices

- Use strong passwords.
- Never use root for daily work.
- Grant sudo only when required.
- Remove inactive users.
- Review user accounts regularly.
- Use groups instead of assigning permissions individually.
- Lock unused accounts.
- Audit login history frequently.

---

# Common Errors

### user already exists

```
adduser: The user already exists.
```

Solution

```bash
id username
```

---

### Permission Denied

```
Permission denied
```

Solution

```bash
sudo command
```

---

### User Cannot Login

Check

```bash
cat /etc/passwd
```

Verify login shell

```
/bin/bash
```

---

### Forgot Password

Reset

```bash
sudo passwd username
```

---

# Interview Questions

## What is UID?

UID (User ID) uniquely identifies a user.

Root always has UID 0.

---

## What is GID?

GID identifies a group.

---

## Difference between Root and Normal User?

Root has unrestricted access.

Normal users have limited permissions.

---

## Difference between adduser and useradd?

adduser is interactive.

useradd is low-level and requires manual configuration.

---

## What is sudo?

sudo allows a permitted user to execute commands with elevated (administrator) privileges.

---

## What is /etc/passwd?

Stores user account information.

---

## What is /etc/shadow?

Stores encrypted passwords.

---

## Why should we avoid logging in as root?

For security reasons. Using sudo reduces the risk of accidental or malicious system-wide changes.

---

# Practice Tasks

✅ Create a user named clouduser

✅ Set a password

✅ Create a group named devops

✅ Add clouduser to the devops group

✅ Grant sudo access

✅ Verify group membership

✅ Lock the account

✅ Unlock the account

✅ Change the login shell

✅ Delete the user and remove the home directory

---

# Cheat Sheet

| Task | Command |
|------|---------|
| Current User | whoami |
| User Details | id |
| Logged-in Users | who |
| User Activity | w |
| Add User | sudo adduser username |
| Delete User | sudo userdel username |
| Delete User + Home | sudo userdel -r username |
| Set Password | sudo passwd username |
| Change Password | passwd |
| Add Group | sudo groupadd groupname |
| Delete Group | sudo groupdel groupname |
| Add User to Group | sudo usermod -aG group username |
| Lock User | sudo passwd -l username |
| Unlock User | sudo passwd -u username |
| Grant Sudo | sudo usermod -aG sudo username |
| Show Groups | groups |
| View Passwd File | cat /etc/passwd |
| View Shadow File | sudo cat /etc/shadow |

---

# Summary

In this module, you learned:

- Linux user types
- Root and regular users
- User IDs (UID)
- Group IDs (GID)
- Creating and deleting users
- Password management
- Group management
- Sudo privileges
- Login shells
- User configuration files
- Security best practices
- Troubleshooting
- Interview questions
- Hands-on practice tasks

Mastering Linux user management is an essential skill for Cloud Support Engineers, Linux Administrators, and DevOps professionals.
