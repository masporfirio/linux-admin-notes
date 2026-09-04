# Linux Networking Checks

## Commands

| Command | Purpose | Example |
|---|---|---|
| `ip link` | Show interfaces and link state | `ip link` |
| `ip addr` | Show assigned addresses | `ip addr show` |
| `ip route` | Show routes and the default gateway | `ip route` |
| `ss -ltnp` | Show listening TCP sockets | `sudo ss -ltnp` |
| `ping` | Test ICMP reachability | `ping -c 3 1.1.1.1` |
| `getent hosts` | Test system name resolution | `getent hosts example.com` |
| `nc -vz` | Test a TCP port | `nc -vz example.com 443` |
| `curl -I` | Request HTTP headers | `curl -I https://example.com` |

## Basic order of checks

```bash
ip link
ip addr
ip route
ping -c 3 <gateway-ip>
ping -c 3 <remote-ip>
getent hosts <hostname>
nc -vz <hostname> <port>
```

This order moves from the local interface to routing, remote reachability, DNS and the application port.

## Local service check

```bash
sudo ss -ltnp | grep ':8080'
curl -I http://127.0.0.1:8080
```

The socket check answers whether something is listening. The HTTP request answers whether the application responds.

## Verification

Repeat the smallest test that showed the original failure, then check the next layer. For example, after restoring a route:

```bash
ip route
ping -c 3 <gateway-ip>
nc -vz <service-ip> <port>
```

## Common mistakes

- `ping hostname` mixes network reachability with DNS resolution.
- Some networks block ICMP, so a failed ping is not enough to prove that every connection is down.
- A listening service bound only to `127.0.0.1` is not reachable from another host.
- `netstat` and `ifconfig` may not be installed; `ss` and `ip` are the current tools on many Linux systems.

DNS-specific notes are kept in [DNS](../dns/).
