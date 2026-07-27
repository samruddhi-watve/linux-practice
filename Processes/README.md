# ⚙️ Linux Process Management

## Overview

A process is a running instance of a program. Every command or application you execute in Linux creates one or more processes.

Linux provides powerful tools to monitor, control, prioritize, and terminate processes. Understanding process management is essential for Linux System Administrators, Cloud Engineers, DevOps Engineers, and Site Reliability Engineers (SREs).

---

# Learning Objectives

After completing this module, you will be able to:

- Understand processes
- Monitor running processes
- Find Process IDs (PID)
- Kill and terminate processes
- Change process priority
- Manage foreground and background jobs
- Monitor system performance
- Manage Linux services
- View system logs
- Schedule jobs using cron
- Troubleshoot high CPU and memory usage

---

# What is a Process?

A process is a program currently being executed by the operating system.

Examples:

- Google Chrome
- SSH Server
- Nginx
- MySQL
- Docker
- Bash Shell

Every process has:

- Process ID (PID)
- Parent Process ID (PPID)
- User
- CPU Usage
- Memory Usage
- State

---

# Process States

| State | Meaning |
|--------|---------|
| R | Running |
| S | Sleeping |
| D | Waiting |
| T | Stopped |
| Z | Zombie |

---

# Display Running Processes

```bash
ps
```

Example

```
PID TTY TIME CMD
1542 pts/0 00:00:00 bash
1678 pts/0 00:00:00 ps
```

---

# Full Process List

```bash
ps -ef
```

Shows:

- UID
- PID
- PPID
- CPU Time
- Command

---

# Process Tree

```bash
pstree
```

Example

```
systemd
 ├── sshd
 ├── nginx
 ├── docker
 └── bash
```

---

# Find Process by Name

```bash
pidof nginx
```

or

```bash
pgrep nginx
```

---

# Search Process

```bash
ps -ef | grep nginx
```

---

# Interactive Process Monitor

```bash
top
```

Important Keys

| Key | Action |
|------|---------|
| P | Sort by CPU |
| M | Sort by Memory |
| k | Kill Process |
| q | Quit |

---

# Enhanced Process Viewer

Install

```bash
sudo apt install htop
```

Run

```bash
htop
```

Features

- Colorful interface
- Mouse support
- Easy sorting
- Better visualization

---

# Kill Process

```bash
kill PID
```

Example

```bash
kill 2450
```

---

# Force Kill

```bash
kill -9 PID
```

Example

```bash
kill -9 2450
```

---

# Kill by Process Name

```bash
killall firefox
```

---

# pkill Command

```bash
pkill nginx
```

---

# Foreground Process

Example

```bash
ping google.com
```

Runs in foreground.

Stop

```
Ctrl + C
```

---

# Background Process

```bash
sleep 200 &
```

Output

```
[1] 2450
```

---

# View Background Jobs

```bash
jobs
```

---

# Bring Job to Foreground

```bash
fg %1
```

---

# Send Process to Background

```
Ctrl + Z
```

Then

```bash
bg
```

---

# nohup Command

Runs a process even after logout.

```bash
nohup python app.py &
```

Output stored in

```
nohup.out
```

---

# Process Priority

Check Priority

```bash
top
```

Look for

```
PR
NI
```

---

# nice Command

Start a process with lower priority

```bash
nice -n 10 python app.py
```

---

# renice Command

Change priority of running process

```bash
sudo renice 5 PID
```

---

# CPU Information

```bash
lscpu
```

---

# Memory Information

```bash
free -h
```

---

# Uptime

```bash
uptime
```

Example

```
11:35 up 5 days, 3 users
```

---

# System Load

```bash
uptime
```

Shows

- Load Average
- Users
- Running Time

---

# Disk Usage

```bash
df -h
```

---

# Memory Usage

```bash
vmstat
```

---

# I/O Statistics

```bash
iostat
```

---

# Running Services

```bash
systemctl list-units --type=service
```

---

# Service Status

```bash
systemctl status nginx
```

---

# Start Service

```bash
sudo systemctl start nginx
```

---

# Stop Service

```bash
sudo systemctl stop nginx
```

---

# Restart Service

```bash
sudo systemctl restart nginx
```

---

# Reload Service

```bash
sudo systemctl reload nginx
```

---

# Enable Service at Boot

```bash
sudo systemctl enable nginx
```

---

# Disable Service

```bash
sudo systemctl disable nginx
```

---

# View Logs

```bash
journalctl
```

---

# View Recent Logs

```bash
journalctl -xe
```

---

# View Logs of Service

```bash
journalctl -u nginx
```

---

# Follow Logs

```bash
journalctl -f
```

---

# Cron Jobs

Edit Cron

```bash
crontab -e
```

View Cron

```bash
crontab -l
```

Delete Cron

```bash
crontab -r
```

Example

```
0 2 * * * /home/user/backup.sh
```

Runs every day at 2 AM.

---

# at Command

Schedule one-time task

```bash
at 6:30 PM
```

---

# Monitor Open Files

```bash
lsof
```

---

# Monitor Network Connections

```bash
ss -tulnp
```

---

# Real-world Scenario 1

Problem

Server CPU is 100%.

Solution

```bash
top
```

Identify high CPU process.

Kill if necessary.

```bash
kill PID
```

---

# Real-world Scenario 2

Application is not responding.

Check

```bash
systemctl status app
```

Restart

```bash
sudo systemctl restart app
```

---

# Real-world Scenario 3

Server is slow.

Check

```bash
free -h

top

df -h

uptime
```

---

# Common Errors

Permission denied

Use

```bash
sudo
```

---

No such process

Verify PID

```bash
ps -ef
```

---

Service not found

Check

```bash
systemctl list-unit-files
```

---

# Best Practices

- Never kill random processes.
- Use SIGTERM before SIGKILL.
- Monitor logs before restarting services.
- Keep cron jobs documented.
- Avoid running unnecessary background jobs.
- Monitor CPU, memory, and disk regularly.

---

# Interview Questions

### What is a process?

A running instance of a program.

---

### What is PID?

Process ID used to uniquely identify a process.

---

### Difference between kill and kill -9?

- `kill` sends SIGTERM (graceful termination).
- `kill -9` sends SIGKILL (forceful termination).

---

### Difference between top and htop?

- `top` is built into most Linux distributions.
- `htop` provides a more interactive and user-friendly interface.

---

### What is a zombie process?

A process that has completed execution but still has an entry in the process table because its parent has not collected its exit status.

---

### What is the purpose of nohup?

It keeps a process running even after the user logs out.

---

### What is systemctl?

A command used to manage services on systems using systemd.

---

### What is journalctl?

A command used to view logs collected by systemd.

---

### What is cron?

A scheduler that executes recurring tasks automatically.

---

# Hands-on Practice

✅ Run `top`

✅ Install `htop`

✅ Create a background process

✅ Bring it to the foreground

✅ Kill a process

✅ Restart a service

✅ View logs using `journalctl`

✅ Create a cron job

✅ Check memory usage

✅ Monitor CPU usage

---

# Cheat Sheet

| Task | Command |
|------|---------|
| Running Processes | `ps` |
| Full Process List | `ps -ef` |
| Process Tree | `pstree` |
| Search Process | `pgrep` |
| Monitor System | `top` |
| Enhanced Monitor | `htop` |
| Kill Process | `kill PID` |
| Force Kill | `kill -9 PID` |
| Kill by Name | `killall process` |
| Background Jobs | `jobs` |
| Foreground Job | `fg` |
| Background Job | `bg` |
| Keep Running After Logout | `nohup` |
| CPU Info | `lscpu` |
| Memory Info | `free -h` |
| Disk Usage | `df -h` |
| System Load | `uptime` |
| Open Files | `lsof` |
| Start Service | `systemctl start` |
| Stop Service | `systemctl stop` |
| Restart Service | `systemctl restart` |
| View Logs | `journalctl` |
| Edit Cron | `crontab -e` |

---

# Summary

In this module, you learned:

- Linux processes
- Process states
- Monitoring processes
- Killing processes
- Foreground and background jobs
- Process priorities
- Managing services with systemctl
- Viewing logs with journalctl
- Scheduling tasks using cron
- Troubleshooting high CPU, memory, and service issues

These skills are fundamental for Linux Administration, Cloud Support, DevOps, and Infrastructure Engineering roles.
