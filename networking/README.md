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

🧪 Mini Lab (Real Scenario)

Scenario

A user reports that the server cannot access the internet.

⸻

Tasks

1. Check IP address
```bash
ip a
```

2. Check connectivity
```bash
ping 8.8.8.8
```

3. Test DNS resolution
```bash
ping google.com
```

4. Check open ports
```bash
ss -tulnp
```
___

🔍 Troubleshooting

❌ Problem 1: No internet access
```bash
ping 8.8.8.8
```

Error
```bash
Network is unreachable
```

✅ Fix
```bash
ip route
```

👉 Check if default gateway exists

⸻

❌ Problem 2: DNS not resolving
```bash
ping google.com
```

Error
```bash
Temporary failure in name resolution
```

✅ Fix
```bash
cat /etc/resolv.conf
```

👉 Verify DNS server configuration

⸻

❌ Problem 3: Port not accessible

Symptom

Service running but not reachable

✅ Fix
```bash
ss -tulnp
```

👉 Check if service is listening on correct port

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
