# 📂 Directory Navigation (Linux)

## 🎯 Objective

Understand and practice directory navigation in Linux using real-world scenarios.

---

## 🧠 Key Concepts

- Absolute path → /etc/nginx/nginx.conf  
- Relative path → ../logs  
- Home directory → ~  
- Previous directory → -  
- Parent directory → ..  

---

## ⚡ Command Reference

| Command | Purpose | Example |
|--------|--------|--------|
| pwd | Show current directory | pwd |
| cd <path> | Change directory | cd /etc |
| cd ~ | Go to home directory | cd ~ |
| cd .. | Go to parent directory | cd .. |
| cd - | Go to previous directory | cd - |
| ls | List files | ls |
| ls -l | Detailed list | ls -l |
| ls -a | Show hidden files | ls -a |
| ls -la | Detailed + hidden | ls -la |

---

## 🧪 Mini Lab (Real Scenario)

### Scenario

You are connected to a Linux server and need to:

- Navigate to configuration files  
- Check log directories  
- Return to your working directory  

---

### Tasks

1. Check current directory
```bash
pwd
```

2. Go to system configuration directory

```bash
cd /etc 
```

3. List files with details
```bash
ls -la 
```

4. Move to logs directory
```bash
cd /var/log 
```
5. Return to previous directory
```bash
cd - 
```

6. Go back to home directory
```bash
cd ~ 
```

---

## 🔍 Troubleshooting

### ❌ Problem 1: Directory not found

```bash
cd etc
``` 

### Error

```bash
No such file or directory
```

### ✅ Fix

```bash
cd /etc
```

👉 Missing absolute path

---

### ❌ Problem 2: Permission denied

```bash
cd /root 
```

### Error

```bash
Permission denied
```

### ✅ Fix

```bash
sudo -i cd /root
``` 

👉 Requires root privileges

---

### ❌ Problem 3: Getting lost in directories

### Symptom
You don’t know where you are

### ✅ Fix

```bash
pwd 
```

👉 Always check your current location

---

## ⚠️ Common Mistakes

- Forgetting / in absolute paths  
- Confusing ~ with /  
- Not using cd - to return quickly  
- Ignoring hidden files (ls -a)  

---

## 🧠 Tips (LPIC + Real World)

- cd - is frequently used in real environments  
- Logs are usually in /var/log  
- Configuration files are typically in /etc  
- Always verify location before running commands  

---

## 🧪 Challenge

You are in:
```bash
/home/user/Documents
```

Navigate to:
```bash
/var/log
```

👉 Try using:

- Absolute path  
- Relative path  

---

## 🚀 Real-World Usage

- Navigating to check logs:
```bash
cd /var/log 
```

- Accessing configuration files:
```bash
cd /etc 
```

- Switching between directories quickly:
```
cd - 
```

---

## 📌 Summary

Directory navigation is a fundamental Linux skill used in:

- System administration  
- Troubleshooting  
- Log analysis  
- Configuration management  

Mastering it improves speed and efficiency in real-world environments.
