# Logs and Journal Checks

## Commands

| Command | Purpose | Example |
|---|---|---|
| `journalctl -b` | Show journal entries from the current boot | `journalctl -b` |
| `journalctl -u` | Filter by systemd unit | `journalctl -u ssh` |
| `journalctl --since` | Limit the time window | `journalctl --since '15 minutes ago'` |
| `journalctl -p` | Filter by priority | `journalctl -p warning` |
| `tail -n` | Show the last lines of a text log | `tail -n 30 /var/log/syslog` |
| `tail -f` | Follow new lines | `tail -f /var/log/syslog` |
| `less` | Read a large file page by page | `less /var/log/syslog` |
| `grep` | Find matching lines | `grep -i error application.log` |

## Service investigation

```bash
systemctl status <service> --no-pager
sudo journalctl -u <service> -n 50 --no-pager
sudo journalctl -u <service> --since '15 minutes ago' --no-pager
```

Filtering by service and time keeps the first review focused.

## Boot messages

```bash
journalctl -b -p warning
dmesg --level=err,warn
```

`dmesg` shows kernel messages. Access may be restricted for normal users.

## Verification

After fixing a service, check only new entries:

```bash
sudo journalctl -u <service> --since '2 minutes ago' --no-pager
```

This helps separate the old error from the result of the latest attempt.

## Common mistakes

- `journalctl -xe` is broad; a unit and time filter are often easier to read first.
- `grep error` can miss other useful words such as `failed`, `denied` or an exit code.
- `cat` can flood the terminal with a large log. Use `less`, `tail` or a time filter.
- Logs can contain usernames, IP addresses, hostnames and tokens. Remove private data before publishing an example.
