# 🌐 Linux Networking

## Overview

Networking is one of the most important concepts in Linux System Administration, Cloud Computing, and DevOps. Every server, virtual machine, container, and cloud service communicates over a network.

A Linux administrator must understand how data travels across a network, how to configure network interfaces, troubleshoot connectivity issues, and secure network communication.

This guide covers Linux networking concepts, commands, practical examples, troubleshooting techniques, and interview questions.

---

# Learning Objectives

After completing this module, you will be able to:

- Understand networking basics
- Understand TCP/IP model
- Configure network interfaces
- Check IP addresses
- Test network connectivity
- Troubleshoot DNS issues
- Transfer files securely
- Monitor network connections
- Diagnose network problems

---

# What is Networking?

Networking is the process of connecting two or more devices so they can exchange data.

Examples

- Laptop ↔ Router
- Laptop ↔ Cloud Server
- Web Browser ↔ Website
- EC2 ↔ RDS
- Docker Container ↔ Internet

---

# Types of Networks

## LAN

Local Area Network

Example

Office Network

---

## WAN

Wide Area Network

Example

Internet

---

## MAN

Metropolitan Area Network

Example

City-wide Network

---

## PAN

Personal Area Network

Example

Bluetooth

---

# OSI Model

| Layer | Name |
|--------|------|
|7|Application|
|6|Presentation|
|5|Session|
|4|Transport|
|3|Network|
|2|Data Link|
|1|Physical|

---

# TCP/IP Model

| Layer | Protocol |
|--------|-----------|
|Application|HTTP HTTPS FTP SSH DNS SMTP|
|Transport|TCP UDP|
|Internet|IP ICMP|
|Network Access|Ethernet Wi-Fi|

---

# IPv4 Address

Example

```
192.168.1.10
```

Structure

```
Network ID

Host ID
```

---

# Public IP

Reachable over the Internet.

Example

```
34.201.xx.xx
```

---

# Private IP

Used inside private networks.

Ranges

```
10.0.0.0/8

172.16.0.0 - 172.31.255.255

192.168.0.0/16
```

---

# Loopback Address

```
127.0.0.1
```

Represents the local machine.

---

# Display IP Address

Ubuntu

```bash
ip addr
```

or

```bash
ip a
```

Example Output

```
inet 192.168.1.25/24
```

---

# Display Interface Details

```bash
ip link
```

---

# Display Routing Table

```bash
ip route
```

Example

```
default via 192.168.1.1
```

---

# Display Hostname

```bash
hostname
```

---

# Display FQDN

```bash
hostname -f
```

---

# Change Hostname

```bash
sudo hostnamectl set-hostname cloud-server
```

Verify

```bash
hostname
```

---

# Ping Command

```bash
ping google.com
```

Purpose

Checks network connectivity.

Stop

```
Ctrl + C
```

---

# Ping Specific Count

```bash
ping -c 4 google.com
```

---

# Check DNS Resolution

```bash
ping amazon.com
```

If the domain resolves to an IP, DNS is working.

---

# traceroute

Shows the path packets take.

Install

```bash
sudo apt install traceroute
```

Run

```bash
traceroute google.com
```

---

# tracepath

```bash
tracepath google.com
```

---

# Display ARP Table

```bash
arp -a
```

or

```bash
ip neigh
```

---

# Display Network Statistics

```bash
ss -tulnp
```

Shows

- Listening Ports
- TCP Connections
- UDP Connections

---

# netstat

Install

```bash
sudo apt install net-tools
```

Run

```bash
netstat -tulnp
```

---

# Display Listening Ports

```bash
ss -l
```

---

# Display TCP Connections

```bash
ss -t
```

---

# Display UDP Connections

```bash
ss -u
```

---

# Display Established Connections

```bash
ss -ant
```

---

# DNS Lookup

```bash
nslookup google.com
```

---

# dig Command

Install

```bash
sudo apt install dnsutils
```

Run

```bash
dig google.com
```

---

# host Command

```bash
host google.com
```

---

# Display DNS Servers

```bash
cat /etc/resolv.conf
```

---

# Check Internet

```bash
curl ifconfig.me
```

Displays public IP.

---

# Download Webpage

```bash
curl https://example.com
```

---

# Download File

```bash
wget https://example.com/file.zip
```

---

# Secure Copy

```bash
scp file.txt user@server:/home/user
```

---

# Secure Login

```bash
ssh user@192.168.1.50
```

---

# Generate SSH Keys

```bash
ssh-keygen
```

---

# Copy SSH Key

```bash
ssh-copy-id user@server
```

---

# Test Port Connectivity

```bash
nc -zv google.com 443
```

---

# Display Open Files

```bash
lsof -i
```

---

# Monitor Bandwidth

```bash
iftop
```

Install

```bash
sudo apt install iftop
```

---

# Display Interface Statistics

```bash
ip -s link
```

---

# Check Gateway

```bash
ip route
```

Look for

```
default via
```

---

# Restart Network

Ubuntu

```bash
sudo systemctl restart NetworkManager
```

---

# Check Network Service

```bash
systemctl status NetworkManager
```

---

# Common Troubleshooting

## Cannot Ping Website

Check

```bash
ip addr
```

Then

```bash
ip route
```

Then

```bash
ping 8.8.8.8
```

Then

```bash
ping google.com
```

---

## DNS Not Working

Check

```bash
cat /etc/resolv.conf
```

Try

```bash
nslookup google.com
```

---

## SSH Connection Refused

Check

```bash
systemctl status ssh
```

Restart

```bash
sudo systemctl restart ssh
```

---

## Interface Down

Check

```bash
ip link
```

Bring interface up

```bash
sudo ip link set eth0 up
```

---

# Best Practices

- Use SSH instead of Telnet.
- Disable unused network services.
- Regularly monitor open ports.
- Use key-based SSH authentication.
- Keep DNS configuration documented.
- Verify firewall rules before troubleshooting.

---

# Interview Questions

### What is an IP Address?

A unique numerical address assigned to a device on a network.

---

### Difference between Public and Private IP?

Public IP is reachable over the Internet.

Private IP is used inside internal networks.

---

### Difference between TCP and UDP?

TCP is connection-oriented and reliable.

UDP is connectionless and faster.

---

### What is DNS?

DNS (Domain Name System) translates domain names into IP addresses.

---

### Difference between ping and traceroute?

`ping` checks connectivity.

`traceroute` shows the complete path packets take.

---

### What is SSH?

SSH (Secure Shell) is a secure protocol used for remote login and remote command execution.

---

### What is the purpose of netstat or ss?

To display network connections, listening ports, routing information, and socket statistics.

---

# Hands-on Practice

✅ Display your IP address

✅ Check your hostname

✅ Ping google.com

✅ Display routing table

✅ Find your DNS server

✅ Generate an SSH key pair

✅ Connect to another Linux machine using SSH

✅ Download a file using wget

✅ View open ports using ss

✅ Check active network connections

---

# Cheat Sheet

| Task | Command |
|------|---------|
| IP Address | `ip addr` |
| Interfaces | `ip link` |
| Routing Table | `ip route` |
| Hostname | `hostname` |
| Ping | `ping` |
| Traceroute | `traceroute` |
| DNS Lookup | `nslookup` |
| Advanced DNS | `dig` |
| Host Lookup | `host` |
| Network Statistics | `ss -tulnp` |
| Legacy Network Stats | `netstat -tulnp` |
| Download File | `wget` |
| HTTP Request | `curl` |
| SSH Login | `ssh` |
| Secure Copy | `scp` |
| Generate SSH Keys | `ssh-keygen` |
| Open Files | `lsof -i` |

---

# Summary

In this module, you learned:

- Networking fundamentals
- OSI & TCP/IP models
- IPv4 addressing
- Network interfaces
- Routing
- DNS
- SSH
- SCP
- curl & wget
- Network diagnostics
- Troubleshooting
- Best practices

  ---

# Advanced Linux Networking

## Introduction

Advanced networking concepts are essential for Linux Administrators, Cloud Engineers, DevOps Engineers, and Site Reliability Engineers (SREs). This section covers IP addressing, subnetting, ports, protocols, firewall configuration, packet analysis, and real-world troubleshooting.

---

# IP Address Classes

IPv4 addresses are divided into different classes.

| Class | Range | Default Subnet Mask | Usage |
|--------|----------------|-----------------|----------------|
| A | 1.0.0.0 – 126.255.255.255 | 255.0.0.0 | Large Networks |
| B | 128.0.0.0 – 191.255.255.255 | 255.255.0.0 | Medium Networks |
| C | 192.0.0.0 – 223.255.255.255 | 255.255.255.0 | Small Networks |
| D | 224.0.0.0 – 239.255.255.255 | N/A | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | N/A | Research |

---

# CIDR Notation

CIDR (Classless Inter-Domain Routing) replaces traditional subnet masks.

Examples

```
192.168.1.0/24
10.0.0.0/16
172.16.0.0/12
192.168.1.5/32
```

Common CIDR Values

| CIDR | Subnet Mask | Hosts |
|------|--------------|-------|
| /8 | 255.0.0.0 | 16,777,214 |
| /16 | 255.255.0.0 | 65,534 |
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |
| /32 | Single Host | 1 |

---

# Understanding Subnetting

Example

```
Network

192.168.10.0/24
```

Network Address

```
192.168.10.0
```

Broadcast Address

```
192.168.10.255
```

Usable Hosts

```
192.168.10.1

to

192.168.10.254
```

Total Hosts

```
254
```

---

# Broadcast Address

Broadcast sends data to all devices in a subnet.

Example

```
192.168.1.255
```

---

# Gateway

A gateway connects one network to another.

Display gateway

```bash
ip route
```

Output

```
default via 192.168.1.1
```

---

# MAC Address

A unique hardware address assigned to every network interface.

Check

```bash
ip link
```

Example

```
08:00:27:ae:7f:91
```

---

# Important Network Protocols

| Protocol | Port | Purpose |
|----------|------|----------------------|
| FTP | 21 | File Transfer |
| SSH | 22 | Secure Remote Login |
| Telnet | 23 | Remote Login |
| SMTP | 25 | Mail Transfer |
| DNS | 53 | Name Resolution |
| DHCP | 67/68 | IP Assignment |
| HTTP | 80 | Web |
| POP3 | 110 | Email Retrieval |
| IMAP | 143 | Email |
| HTTPS | 443 | Secure Web |
| MySQL | 3306 | Database |
| PostgreSQL | 5432 | Database |
| Redis | 6379 | Cache |
| MongoDB | 27017 | Database |

---

# TCP vs UDP

| TCP | UDP |
|------|------|
| Reliable | Faster |
| Connection-oriented | Connectionless |
| Error Checking | No Error Recovery |
| Ordered Delivery | Unordered |
| Used for HTTP, HTTPS, SSH | Used for DNS, Streaming |

---

# HTTP vs HTTPS

| HTTP | HTTPS |
|-------|--------|
| Port 80 | Port 443 |
| Not Encrypted | Encrypted |
| Less Secure | More Secure |
| No SSL/TLS | Uses SSL/TLS |

---

# FTP vs SFTP vs SCP

| FTP | SFTP | SCP |
|------|------|------|
| Port 21 | Port 22 | Port 22 |
| Not Secure | Secure | Secure |
| Separate Protocol | SSH Based | SSH Based |

---

# DHCP

Dynamic Host Configuration Protocol automatically assigns IP addresses.

Renew IP

```bash
sudo dhclient
```

Release IP

```bash
sudo dhclient -r
```

---

# ARP

Maps IP addresses to MAC addresses.

Display

```bash
arp -a
```

or

```bash
ip neigh
```

---

# ICMP

Internet Control Message Protocol.

Used by

```
ping
```

and

```
traceroute
```

---

# Packet Capture

Install

```bash
sudo apt install tcpdump
```

Capture packets

```bash
sudo tcpdump
```

Capture on interface

```bash
sudo tcpdump -i eth0
```

Capture specific port

```bash
sudo tcpdump port 80
```

Save capture

```bash
sudo tcpdump -w capture.pcap
```

---

# Port Scanning

Install

```bash
sudo apt install nmap
```

Scan host

```bash
nmap 192.168.1.100
```

Scan ports

```bash
nmap -p 1-1000 localhost
```

Service detection

```bash
nmap -sV localhost
```

OS detection

```bash
sudo nmap -O localhost
```

---

# Firewall (UFW)

Enable firewall

```bash
sudo ufw enable
```

Status

```bash
sudo ufw status
```

Allow SSH

```bash
sudo ufw allow 22
```

Allow HTTP

```bash
sudo ufw allow 80
```

Allow HTTPS

```bash
sudo ufw allow 443
```

Delete rule

```bash
sudo ufw delete allow 80
```

Disable

```bash
sudo ufw disable
```

---

# iptables

View rules

```bash
sudo iptables -L
```

Flush rules

```bash
sudo iptables -F
```

Allow SSH

```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

---

# Network Troubleshooting Flow

Step 1

Check interface

```bash
ip addr
```

↓

Step 2

Check gateway

```bash
ip route
```

↓

Step 3

Ping gateway

```bash
ping 192.168.1.1
```

↓

Step 4

Ping Google DNS

```bash
ping 8.8.8.8
```

↓

Step 5

Check DNS

```bash
nslookup google.com
```

↓

Step 6

Check firewall

```bash
sudo ufw status
```

↓

Step 7

Check listening ports

```bash
ss -tulnp
```

---

# Real-world Scenario 1

Cannot access website.

Check

```bash
ping google.com
```

If fails

```bash
nslookup google.com
```

If DNS fails

```bash
cat /etc/resolv.conf
```

---

# Real-world Scenario 2

Cannot SSH into server.

Verify

```bash
ping server-ip
```

Then

```bash
systemctl status ssh
```

Then

```bash
ss -tulnp
```

Verify port

```
22
```

---

# Real-world Scenario 3

Port 80 not working.

Check

```bash
ss -tulnp
```

Restart service

```bash
sudo systemctl restart nginx
```

Check firewall

```bash
sudo ufw status
```

---

# Best Practices

- Use SSH instead of Telnet.
- Disable unused ports.
- Keep firewall enabled.
- Regularly update DNS settings.
- Use HTTPS whenever possible.
- Monitor open ports.
- Restrict SSH access using keys.

---

# Interview Questions

### What is CIDR?

CIDR is a notation that specifies the network prefix length.

Example

```
192.168.1.0/24
```

---

### What is subnetting?

Subnetting divides a large network into smaller, manageable subnetworks.

---

### Difference between TCP and UDP?

TCP is reliable and connection-oriented.

UDP is faster and connectionless.

---

### What is a MAC Address?

A unique hardware address assigned to a network interface.

---

### What is the purpose of DNS?

Converts domain names into IP addresses.

---

### Difference between HTTP and HTTPS?

HTTPS encrypts communication using SSL/TLS, while HTTP sends data in plain text.

---

### What is a firewall?

A firewall controls incoming and outgoing network traffic based on security rules.

---

### What is Nmap?

A network scanning tool used to discover hosts, services, and open ports.

---

### What is tcpdump?

A packet capture tool used to analyze network traffic.

---

### Difference between SSH and Telnet?

SSH encrypts all communication.

Telnet sends data in plain text.

---

# Practice Tasks

✅ Find your IP address

✅ Find your MAC address

✅ Display routing table

✅ Find gateway

✅ Ping Google

✅ Perform DNS lookup

✅ Capture packets using tcpdump

✅ Scan localhost using nmap

✅ Enable UFW

✅ Allow SSH

✅ Verify firewall rules

---

# Cheat Sheet

| Task | Command |
|------|---------|
| Show IP | `ip addr` |
| Show MAC | `ip link` |
| Show Gateway | `ip route` |
| Ping | `ping` |
| DNS Lookup | `nslookup` |
| Advanced DNS | `dig` |
| Packet Capture | `tcpdump` |
| Port Scan | `nmap` |
| Firewall Status | `ufw status` |
| Enable Firewall | `ufw enable` |
| List Ports | `ss -tulnp` |
| Routing Table | `ip route` |
| SSH | `ssh` |
| SCP | `scp` |
| Download File | `wget` |
| HTTP Request | `curl` |

---

# Summary

In this module you learned:

- IP Classes
- CIDR
- Subnetting
- Gateway
- MAC Address
- TCP vs UDP
- HTTP vs HTTPS
- FTP, SFTP & SCP
- DHCP
- ARP
- ICMP
- tcpdump
- nmap
- UFW
- iptables
- Network Troubleshooting
- Interview Questions
- Best Practices

These concepts form the foundation of Linux Networking and are frequently asked in Linux Administrator, Cloud Support, AWS, Azure, DevOps, and Infrastructure Engineer interviews.
- Interview questions

These concepts are essential for Linux Administration, Cloud Support, DevOps, AWS, Azure, and Infrastructure Engineering roles.
