# File Management in Linux

File management is one of the most important Linux administration tasks. Linux provides various commands to create, copy, move, rename, delete, search, and view files and directories.

## Create a File

```bash
touch file1.txt
```

Creates an empty file.

---

## Create Multiple Files

```bash
touch file1.txt file2.txt file3.txt
```

---

## Create Directory

```bash
mkdir Projects
```

---

## Create Nested Directories

```bash
mkdir -p Cloud/Linux/Practice
```

---

## List Files

```bash
ls
```

---

## Detailed Listing

```bash
ls -l
```

---

## Hidden Files

```bash
ls -la
```

---

## Copy File

```bash
cp file1.txt backup.txt
```

---

## Copy Directory

```bash
cp -r Projects Backup
```

---

## Move/Rename File

```bash
mv file1.txt newfile.txt
```

---

## Delete File

```bash
rm file1.txt
```

---

## Delete Directory

```bash
rm -r Projects
```

---

## View File

```bash
cat file.txt
```

---

## First 10 Lines

```bash
head file.txt
```

---

## Last 10 Lines

```bash
tail file.txt
```

---

## Search File

```bash
find /home -name "*.txt"
```

---

## Disk Usage

```bash
du -sh *
```

---

## Free Disk Space

```bash
df -h
```

---

## Interview Question

Q. Difference between cp and mv?

Answer:
cp creates a copy while mv moves or renames a file.
