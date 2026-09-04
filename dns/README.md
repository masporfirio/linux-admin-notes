# DNS Client Checks

## Commands

| Command | Purpose | Example |
|---|---|---|
| `getent hosts` | Test the system's configured name service | `getent hosts example.com` |
| `resolvectl status` | Show resolver and per-link DNS state | `resolvectl status` |
| `resolvectl query` | Query through `systemd-resolved` | `resolvectl query example.com` |
| `dig` | Display a detailed DNS response | `dig example.com` |
| `host` | Make a short DNS query | `host example.com` |
| `nslookup` | Use an interactive or simple DNS lookup | `nslookup example.com` |

The last three commands may be provided by a package such as `dnsutils` or `bind-utils`.

## Files to inspect

```bash
cat /etc/nsswitch.conf
ls -l /etc/resolv.conf
cat /etc/resolv.conf
cat /etc/hosts
```

- `/etc/nsswitch.conf` controls the order of sources used for host lookups.
- `/etc/resolv.conf` lists resolver information, but it may be managed by another service.
- `/etc/hosts` provides local static name mappings.

## Separate network and DNS

```bash
ping -c 3 1.1.1.1
getent hosts example.com
dig example.com
```

If the IP test works but the name lookups fail, the problem is more likely in DNS configuration or access to the DNS server.

## Verification

```bash
resolvectl query example.com
getent hosts example.com
```

Testing through the system resolver is important because a direct `dig` query and an application lookup do not always use the same path.

## Common mistakes

- `nameserver` selects a DNS server; `search` supplies suffixes for short names.
- A loopback resolver address such as `127.0.0.53` can be normal when `systemd-resolved` is active.
- Editing a generated `/etc/resolv.conf` directly may be temporary.
- A DNS response can be cached, so compare the time and resolver used before assuming the fix worked.
