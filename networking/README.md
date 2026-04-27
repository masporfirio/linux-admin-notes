🌐 Networking (Linux)

🎯 Objective

Understand and troubleshoot basic Linux networking using real-world scenarios.

⸻

🧠 Key Concepts

* IP addressing (IPv4/IPv6)
* DNS resolution
* Network interfaces
* Routing basics

____

## ⚡ Command Reference

| Command | Description | Example | Notes |
|--------|------------|--------|------|
| `ip a` | Show IP addresses | `ip a` | Replaces `ifconfig` |
| `ip route` | Show routing table | `ip route` | Check default gateway |
| `ping` | Test connectivity | `ping google.com` | ICMP test |
| `ss -tulnp` | Show open ports | `ss -tulnp` | Replaces `netstat` |
| `netstat -tulnp` | Show ports (legacy) | `netstat -tulnp` | Requires net-tools |
| `traceroute` | Trace network path | `traceroute google.com` | Diagnose routing issues |
| `tracepath` | Trace path (no root) | `tracepath google.com` | Alternative without sudo |
| `dig` | DNS query | `dig google.com` | Detailed DNS info |
| `nslookup` | DNS lookup | `nslookup google.com` | Simpler DNS tool |
| `host` | Resolve hostname | `host google.com` | Quick DNS check |

____

## 🧪 Mini Lab (Guided Scenario)

### Scenario

A user reports that the server cannot access the internet.

---

🔍 Step 1: Check IP Address

```bash
ip a
```

👉 Verify that the interface has a valid IP address
✔️ If no IP → interface or DHCP issue

⸻

🔍 Step 2: Test Raw Connectivity
```bash
ping 8.8.8.8
```

❌ Possible Error
```bash
Network is unreachable
```

👉 Indicates routing issue

⸻

🔍 Step 3: Check Routing Table
```bash
ip route
```

❌ Possible Issue
```bash
(no default route)
```

✅ Fix (example)
```bash
sudo ip route add default via 192.168.1.1
```

🔍 Step 4: Test DNS Resolution
```bash
ping google.com
```

❌ Possible Error
```bash
Temporary failure in name resolution
```

👉 Network OK, DNS broken

⸻

🔍 Step 5: Check DNS Configuration
```bash
cat /etc/resolv.conf
```

❌ Possible Issue
```bash
nameserver 127.0.0.53
```

(or invalid/missing entry)

⸻

✅ Fix (example)
```bash
sudo nano /etc/resolv.conf
```

Add:
```bash
nameserver 8.8.8.8
```

🔍 Step 6: Check Open Ports
```bash
ss -tulnp
```

❌ Possible Issue

Service not listening on expected port

Example
```bash
LISTEN 0 128 127.0.0.1:8080
```

👉 Service bound to localhost only

⸻

✅ Fix (example)

* Reconfigure service to listen on 0.0.0.0
* Restart service:
```bash
sudo systemctl restart <service>
```
____

🧠 Key Takeaways

* Always test IP connectivity first
* Then test DNS resolution
* Check routing before assuming network failure
* Validate if services are listening on correct interfaces


⸻

⚠️ Common Mistakes

* Confusing network vs DNS issue
* Not checking IP before testing DNS
* Ignoring routing table
* Using outdated commands (ifconfig)

⸻

🧠 Tips (LPIC + Real World)

* Always test connectivity with IP first
* Then test DNS resolution
* Use ss instead of netstat
* Check /etc/resolv.conf for DNS issues

⸻

🧪 Challenge

Simulate:

* No internet connection
* Broken DNS

👉 Diagnose step by step

⸻

🚀 Real-World Usage

* Check active ports:
```bash
ss -tulnp
```

* Diagnose DNS:
```bash
dig google.com
```

* Verify connectivity:
```bash
ping 8.8.8.8
```

📌 Summary

Networking is essential for:

* Troubleshooting connectivity
* Diagnosing DNS issues
* Managing services and ports
* Supporting production systems

Understanding these commands is critical for any Linux administrator.

____

## 🔗 Related Lab

Apply these concepts in real-world troubleshooting scenarios:

👉 Networking DNS & Routing Lab (linux-troubleshooting-labs)

Covers:
- DNS resolution failure  
- Missing default route  
- ❌ Port not accessible (service not listening / blocked)
