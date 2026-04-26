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

⚡ Command Reference
Command

Purpose

Example

touch

Create empty file

touch file.txt

cp

Copy file

cp file.txt /tmp/

cp -r

Copy directory

cp -r dir/ /tmp/

mv

Move or rename

mv file.txt new.txt

rm

Remove file

rm file.txt

rm -r

Remove directory

rm -r dir/

rm -rf

Force remove

rm -rf dir/

cat

Show file content

cat file.txt

less

View file (paged)

less file.txt

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
