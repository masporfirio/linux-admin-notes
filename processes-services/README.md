⚙️ Processes & Services (Linux)

🎯 Objective

Understand and manage processes and services in Linux using real-world scenarios.

⸻

🧠 Key Concepts

* Process → running program
* PID → Process ID
* Service → managed process (systemd)
* Foreground vs background
* Service lifecycle (start, stop, restart)

___

## ⚡ Command Reference

| Command | Description | Example | Notes |
|--------|------------|--------|------|
| `ps aux` | List all running processes | `ps aux` | Useful for identifying active processes |
| `top` | Real-time process monitoring | `top` | Shows CPU and memory usage |
| `htop` | Interactive process viewer | `htop` | Easier to use than `top` (if installed) |
| `kill` | Terminate a process | `kill 1234` | Sends SIGTERM (graceful stop) |
| `kill -9` | Force kill a process | `kill -9 1234` | ⚠️ Force termination (SIGKILL) |
| `systemctl status` | Check service status | `systemctl status ssh` | First step in troubleshooting |
| `systemctl start` | Start a service | `systemctl start nginx` | Requires sudo in most cases |
| `systemctl stop` | Stop a service | `systemctl stop nginx` | Stops running service |
| `systemctl restart` | Restart a service | `systemctl restart nginx` | Common fix for issues |
| `systemctl enable` | Enable service at boot | `systemctl enable nginx` | Persists after reboot |
| `systemctl disable` | Disable service at boot | `systemctl disable nginx` | Prevents auto start |
| `systemctl --failed` | List failed services | `systemctl --failed` | Useful for quick diagnostics |

___

🧪 Mini Lab (Real Scenario)

Scenario

A service is not responding and you need to:

* Identify running processes
* Check service status
* Restart the service

⸻

Tasks

1. List running processes
```bash
ps aux | grep ssh
```

2. Check service status
```bash
systemctl status ssh
```

3. Restart service
```bash
sudo systemctl restart ssh
```

4. Monitor processes
```bash
top
```

⸻

🔍 Troubleshooting

❌ Problem 1: Service not starting
```bash
systemctl start nginx
```

Error
```bash
Failed to start nginx.service
```

✅ Fix
```bash
systemctl status nginx
journalctl -xe
```

👉 Check logs for root cause

⸻

❌ Problem 2: Process stuck
```bash
kill 1234
```

Issue

Process does not stop

✅ Fix
```bash
kill -9 1234
```

👉 Force termination

⸻

❌ Problem 3: Service not enabled at boot

Symptom

Service stops after reboot

✅ Fix
```bash
systemctl enable nginx
```

⚠️ Common Mistakes

* Killing wrong process
* Using kill -9 unnecessarily
* Forgetting to check logs
* Not enabling service at boot

⸻

🧠 Tips (LPIC + Real World)

* Always check with systemctl status first
* Use journalctl for detailed logs
* Prefer kill before kill -9
* Use htop for easier visualization

⸻

🧪 Challenge

Simulate:

* Start a service
* Stop it
* Restart it
* Check logs

⸻

🚀 Real-World Usage

* Restart SSH service:
```bash
sudo systemctl restart ssh
```

* Check failed services:
```bash
systemctl --failed
```

* View logs:
```bash
journalctl -u nginx
```

⸻

📌 Summary

Process and service management is critical for:

* Troubleshooting system issues
* Maintaining uptime
* Diagnosing failures
* Managing system resources

These skills are essential for any Linux administrator.
