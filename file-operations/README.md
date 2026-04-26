📄 File Operations (Linux)

🎯 Objective

Understand and practice file management in Linux using real-world scenarios.

⸻

🧠 Key Concepts

* Copying files → cp
* Moving/renaming → mv
* Removing files → rm
* Creating files → touch
* Viewing content → cat, less

⸻

## ⚡ Command Reference

| Command | Description | Example | Notes |
|--------|------------|--------|------|
| `touch` | Create an empty file | `touch file.txt` | Useful for creating new files quickly |
| `cp` | Copy a file | `cp file.txt /tmp/` | Overwrites by default |
| `cp -r` | Copy directories recursively | `cp -r dir/ /tmp/` | Required for directories |
| `cp -i` | Copy with confirmation | `cp -i file.txt /tmp/` | Prevents accidental overwrite |
| `mv` | Move or rename files | `mv file.txt new.txt` | Used for both move and rename |
| `rm` | Remove a file | `rm file.txt` | Permanent deletion |
| `rm -r` | Remove directory | `rm -r dir/` | Recursive delete |
| `rm -rf` | Force remove | `rm -rf dir/` | ⚠️ Dangerous, no confirmation |
| `cat` | Display file content | `cat file.txt` | Good for small files |
| `less` | View file (paged) | `less file.txt` | Better for large files |

___

🧪 Mini Lab (Real Scenario)

Scenario

You need to manage files on a Linux server:

* Create a file
* Copy it to another directory
* Rename it
* Remove it

⸻

Tasks

1. Create a file
```bash
touch test.txt
```

2. Copy file to /tmp
```bash
cp test.txt /tmp/
```

3. Rename the file
```bash
mv test.txt file-renamed.txt
```

4. View file content
```bash
cat file-renamed.txt
```

5. Remove file
```bash
rm file-renamed.txt
```
___

🔍 Troubleshooting

❌ Problem 1: File not found
```bash
cp file.txt /tmp/
```

Error
```bash
cp: cannot stat 'file.txt': No such file or directory
```

✅ Fix
```bash
ls
cp correct-file.txt /tmp/
```

👉 Verify file name before operations

⸻

❌ Problem 2: Permission denied
```bash
rm /root/file.txt
```

Error
```bash
Permission denied
```

✅ Fix
```bash
sudo rm /root/file.txt
```

👉 Requires elevated privileges

⸻

❌ Problem 3: Deleting wrong files

Risk

Using:
```bash
rm -rf *
```

✅ Advice

* Always check directory:
```bash
pwd
ls
```

👉 Avoid destructive commands without validation

⸻

⚠️ Common Mistakes

* Using rm -rf without checking directory
* Forgetting -r when copying directories
* Overwriting files accidentally with cp
* Not verifying file paths

⸻

🧠 Tips (LPIC + Real World)

* Use cp -i to avoid overwriting files
* Prefer less over cat for large files
* Always double-check before using rm -rf
* Use mv for both rename and move operations

⸻

🧪 Challenge

Create a directory structure:
```bash
project/
 ├── file1.txt
 └── backup/
```

Tasks:

* Copy file1.txt to backup/
* Rename it to file1.bak
* Delete original file

⸻

🚀 Real-World Usage

* Backup configuration file:
```bash
cp /etc/nginx/nginx.conf /tmp/nginx.conf.bak
```

* Rename log file:
```bash
mv app.log app.log.old
```

* Remove temporary files:
```bash
rm -rf /tmp/*
```

📌 Summary

File operations are essential for:

* System administration
* Backup and recovery
* Log management
* Troubleshooting tasks

Mastering them prevents critical mistakes in production systems.
