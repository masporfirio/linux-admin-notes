📜 Logs & System Analysis (Linux)

🎯 Objective

Understand how to analyze logs and diagnose system issues in Linux.

⸻

🧠 Key Concepts

* System logs
* Service logs
* Log levels
* Real-time monitoring

⸻

## ⚡ Command Reference

| Command | Description | Example | Notes |
|--------|------------|--------|------|
| `journalctl` | View system logs | `journalctl` | Main systemd log viewer |
| `journalctl -u` | View logs for a specific service | `journalctl -u ssh` | Focus on one service |
| `journalctl -xe` | Show detailed errors | `journalctl -xe` | Useful for troubleshooting failures |
| `journalctl -f` | Follow logs in real time | `journalctl -f` | Similar to `tail -f` |
| `journalctl -n` | Show last N log entries | `journalctl -n 20` | Quick recent logs |
| `tail -f` | Follow log file in real time | `tail -f /var/log/syslog` | Works on traditional log files |
| `tail -n` | Show last lines of a file | `tail -n 20 file.log` | Quick inspection |
| `less` | View large log files | `less /var/log/syslog` | Scrollable, safer than `cat` |
| `grep` | Search inside logs | `grep error /var/log/syslog` | Filter relevant entries |
| `dmesg` | Show kernel messages | `dmesg` | Hardware and boot logs |

____

🧪 Mini Lab (Real Scenario)

Scenario

A service is failing and you need to check logs to find the issue.

⸻

Tasks

1. Check service logs
```bash
journalctl -u ssh
```

2. View recent logs
```bash
journalctl -n 20
```

3. Monitor logs in real time
```bash
journalctl -f
```

4. Search for errors
```bash
journalctl | grep error
```

____

🔍 Troubleshooting

❌ Problem 1: Service not starting
```bash
systemctl status nginx
```

✅ Fix
```bash
journalctl -u nginx
```

👉 Check detailed logs

⸻

❌ Problem 2: No logs appearing

Symptom

Logs not showing expected output

✅ Fix
```bash
journalctl -xe
```

👉 Check system-level errors

⸻

❌ Problem 3: Log file too large

Symptom

File hard to read

✅ Fix
```bash
less /var/log/syslog
```

👉 Use paging instead of cat

⸻

⚠️ Common Mistakes

* Not checking logs first
* Using cat on large files
* Ignoring system logs
* Not filtering output

⸻

🧠 Tips (LPIC + Real World)

* Logs are your best troubleshooting tool
* Use journalctl -u for services
* Combine grep to filter logs
* Use -f for live monitoring

⸻

🧪 Challenge

Simulate:

* Service failure
* Identify issue using logs

⸻

🚀 Real-World Usage

* Check failed service:
```bash
journalctl -u nginx
```

* Monitor logs:
```bash
tail -f /var/log/syslog
```

* Search for errors:
```bash
grep error /var/log/syslog
```

📌 Summary

Log analysis is essential for:

* Troubleshooting system issues
* Diagnosing failures
* Monitoring system behavior
* Maintaining system reliability

Mastering logs is one of the most important skills in Linux administration.
