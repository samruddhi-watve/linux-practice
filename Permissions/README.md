# 🔐 File Permissions

Linux permissions control who can read, write, and execute files.

---

## 📚 Commands

| Command | Description |
|---------|-------------|
| `ls -l` | View file permissions |
| `chmod` | Change file permissions |
| `chown` | Change file owner |
| `umask` | Set default permissions |

---

## 💻 Examples

```bash
ls -l
chmod 755 script.sh
chmod +x app.sh
chown user:user file.txt
umask
```

---

## Permission Values

| Number | Permission |
|--------|------------|
| 7 | Read + Write + Execute |
| 6 | Read + Write |
| 5 | Read + Execute |
| 4 | Read Only |

---

## 🎯 Learning Outcome

- Understand Linux file permissions
- Modify permissions using chmod
- Manage file ownership
