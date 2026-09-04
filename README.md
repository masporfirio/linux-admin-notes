# Linux Admin Notes

These are short Linux administration notes from my study and virtual-machine practice. I use them as a reminder of what a command checks, why I would use it and how to verify the result.

The examples are written for learning. Distribution names, service names and available options can differ, so I check the local manual page before making a system change.

## Notes

| Topic | What it covers |
|---|---|
| [Navigation](navigation/) | paths, `pwd`, `cd` and `ls` |
| [File operations](file-operations/) | creating, copying, moving, finding and archiving files |
| [Processes and services](processes-services/) | `ps`, signals, `systemctl` and unit logs |
| [Networking](networking/) | interfaces, addresses, routes, sockets and basic tests |
| [Logs](logs/) | `journalctl`, `less`, `tail` and `grep` |
| [Permissions](permissions/) | modes, ownership and ACL checks |
| [Users and groups](users-groups/) | identity, group membership and account checks |
| [Packages](packages/) | Debian and RPM package checks |
| [Storage](storage/) | block devices, filesystems, mounts and space |
| [DNS](dns/) | resolver checks and name-resolution tools |

## How I use these notes

For a troubleshooting check, I try to record:

1. **Command** - what I ran.
2. **Purpose** - the question it answers.
3. **Example** - a small, reproducible use.
4. **Verification** - how I know the result changed.
5. **Common mistake** - a limit or risk to remember.

Longer exercises are kept in [Linux Troubleshooting Labs](https://github.com/masporfirio/linux-troubleshooting-labs).
