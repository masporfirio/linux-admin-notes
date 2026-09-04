# Processes and Services

## Process checks

| Command | Purpose | Example |
|---|---|---|
| `ps aux` | Show a snapshot of processes | `ps aux` |
| `pgrep -a` | Find a PID and full command by name | `pgrep -a sshd` |
| `top` | Watch CPU and memory use | `top` |
| `kill` | Send `SIGTERM` by default | `kill 1234` |
| `kill -l` | List signal names and numbers | `kill -l` |

Before sending a signal, confirm the PID:

```bash
ps -fp <PID>
```

I use normal `kill` before `kill -9`. `SIGKILL` stops a process immediately and does not allow cleanup.

## systemd checks

| Command | Purpose |
|---|---|
| `systemctl status ssh --no-pager` | Show service state and recent messages |
| `systemctl is-active ssh` | Return whether the service is running |
| `systemctl is-enabled ssh` | Return whether the unit starts at boot |
| `systemctl --failed` | List failed units |
| `systemctl cat ssh` | Show the unit file and overrides loaded by systemd |
| `journalctl -u ssh -n 30 --no-pager` | Show recent logs for one unit |

## Practice

```bash
systemctl is-active ssh
systemctl is-enabled ssh
systemctl status ssh --no-pager
journalctl -u ssh -n 30 --no-pager
```

These checks are read-only. A restart should follow evidence from status or logs, not replace the investigation.

## Verification after a change

```bash
systemctl is-active <service>
systemctl status <service> --no-pager
journalctl -u <service> -n 20 --no-pager
```

For a network service, also check its socket or make a local request.

## Common mistakes

- `enabled` means configured for startup; it does not mean currently running.
- The service can be named `ssh` on one distribution and `sshd` on another.
- After editing a unit file, run `sudo systemctl daemon-reload` before restarting it.
- Repeated restarts can hide the first useful error message.
