# 📂 Linux File Management

## Overview

File management is one of the most important responsibilities of a Linux System Administrator. Every file, directory, configuration file, log file, application, and service in Linux is managed through the Linux file system.

Understanding file management is essential for Cloud Engineers, DevOps Engineers, Linux Administrators, and System Engineers.

---

# Objectives

After completing this module, you will be able to:

- Navigate the Linux file system
- Create files and directories
- Copy and move files
- Rename files
- Delete files safely
- Search files
- View file contents
- Check disk usage
- Compress files
- Archive directories
- Create symbolic links
- Manage hidden files
- Work with absolute and relative paths

---

# Linux File System Structure

```
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

## Important Directories

| Directory | Description |
|------------|-------------|
| / | Root Directory |
| /home | User Home Directories |
| /etc | Configuration Files |
| /bin | Essential Commands |
| /usr | Installed Programs |
| /var | Logs & Variable Data |
| /tmp | Temporary Files |
| /root | Root User Home |
| /dev | Device Files |
| /proc | Process Information |

---

# Present Working Directory

## Command

```bash
pwd
```

### Description

Displays the current directory.

### Example

```bash
$ pwd

/home/samruddhi
```

---

# List Files

```bash
ls
```

Lists files and directories.

Example

```bash
Desktop
Downloads
Documents
Pictures
```

---

# Long Listing

```bash
ls -l
```

Output

```
-rw-r--r-- 1 user user 1200 Jul 20 notes.txt
```

Explanation

- File Permission
- Links
- Owner
- Group
- Size
- Date
- Filename

---

# Hidden Files

```bash
ls -la
```

Displays hidden files beginning with '.'

Example

```
.bashrc
.profile
.gitconfig
```

---

# Create Directory

```bash
mkdir Linux
```

---

# Create Multiple Directories

```bash
mkdir DevOps AWS Docker Linux
```

---

# Create Nested Directories

```bash
mkdir -p Projects/Linux/Practice
```

---

# Change Directory

```bash
cd Linux
```

---

# Move One Directory Back

```bash
cd ..
```

---

# Go Home

```bash
cd
```

or

```bash
cd ~
```

---

# Go Root Directory

```bash
cd /
```

---

# Create Empty File

```bash
touch notes.txt
```

---

# Create Multiple Files

```bash
touch file1.txt file2.txt file3.txt
```

---

# Copy File

```bash
cp file1.txt backup.txt
```

---

# Copy Directory

```bash
cp -r Linux LinuxBackup
```

---

# Move File

```bash
mv notes.txt Documents/
```

---

# Rename File

```bash
mv old.txt new.txt
```

---

# Delete File

```bash
rm file.txt
```

---

# Delete Multiple Files

```bash
rm file1.txt file2.txt file3.txt
```

---

# Delete Directory

```bash
rm -r Linux
```

---

# Delete Empty Directory

```bash
rmdir Linux
```

---

# Force Delete

```bash
rm -rf Linux
```

⚠ Be careful with this command.

---

# View File

```bash
cat notes.txt
```

---

# Display First 10 Lines

```bash
head notes.txt
```

---

# Display Last 10 Lines

```bash
tail notes.txt
```

---

# View File Page by Page

```bash
less notes.txt
```

Exit using

```
q
```

---

# Count Lines

```bash
wc -l notes.txt
```

---

# Count Words

```bash
wc -w notes.txt
```

---

# Search Text

```bash
grep "Linux" notes.txt
```

---

# Recursive Search

```bash
grep -r "password" /etc
```

---

# Find File

```bash
find /home -name "*.txt"
```

---

# Locate File

```bash
locate notes.txt
```

Update Database

```bash
sudo updatedb
```

---

# Sort File

```bash
sort numbers.txt
```

---

# Remove Duplicate Lines

```bash
uniq names.txt
```

---

# Compare Files

```bash
diff file1.txt file2.txt
```

---

# Check File Type

```bash
file image.png
```

---

# Display Disk Usage

```bash
du -sh *
```

---

# Display Free Disk Space

```bash
df -h
```

---

# Compress File

```bash
gzip notes.txt
```

---

# Decompress

```bash
gunzip notes.txt.gz
```

---

# Create Archive

```bash
tar -cvf backup.tar Linux
```

---

# Extract Archive

```bash
tar -xvf backup.tar
```

---

# Create Tar.gz

```bash
tar -czvf backup.tar.gz Linux
```

---

# Extract Tar.gz

```bash
tar -xzvf backup.tar.gz
```

---

# Create Symbolic Link

```bash
ln -s original.txt shortcut.txt
```

---

# Create Hard Link

```bash
ln original.txt hardlink.txt
```

---

# Check File Size

```bash
ls -lh
```

---

# Display Calendar

```bash
cal
```

---

# Display Date

```bash
date
```

---

# Clear Screen

```bash
clear
```

Shortcut

```
Ctrl + L
```

---

# Keyboard Shortcuts

| Shortcut | Description |
|----------|-------------|
| Ctrl + C | Stop Process |
| Ctrl + D | Logout |
| Ctrl + L | Clear Screen |
| Ctrl + A | Beginning of Line |
| Ctrl + E | End of Line |
| Ctrl + R | Search History |
| Tab | Auto Complete |
| Arrow Up | Previous Command |

---

# Best Practices

- Never use `rm -rf /`
- Always verify before deleting files.
- Keep backups of important files.
- Use meaningful filenames.
- Organize files into directories.
- Avoid using root unless necessary.
- Use relative paths whenever possible.

---

# Common Interview Questions

### What is the difference between cp and mv?

cp copies a file.

mv moves or renames a file.

---

### Difference between rm and rmdir?

rm removes files.

rmdir removes empty directories only.

---

### Difference between absolute path and relative path?

Absolute path starts from root (/).

Relative path starts from current directory.

---

### Difference between hard link and symbolic link?

Hard link points directly to inode.

Symbolic link points to another file.

---

### Difference between cat, less and more?

cat prints the complete file.

less allows scrolling both directions.

more allows forward scrolling only.

---

# Mini Practice Tasks

✅ Create a directory named Cloud.

✅ Create five text files.

✅ Copy all files into Backup directory.

✅ Rename one file.

✅ Delete one file.

✅ Search for all `.txt` files.

✅ Compress the Backup folder.

✅ Extract the archive.

✅ Display disk usage.

✅ Create a symbolic link.

---

# Summary

In this module, you learned:

- Linux file system
- File creation
- Directory management
- Copying files
- Moving files
- Deleting files
- Searching files
- Viewing files
- Disk usage
- Compression
- Archiving
- Links
- Best practices
- Interview questions

This module forms the foundation for Linux Administration, Cloud Support, and DevOps roles.
