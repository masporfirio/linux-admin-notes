# Users and Groups

## Read-only checks

| Command | Purpose | Example |
|---|---|---|
| `id` | Show UID, primary group and supplementary groups | `id marcelo` |
| `groups` | List a user's groups | `groups marcelo` |
| `getent passwd` | Query the configured account database | `getent passwd marcelo` |
| `getent group` | Query group membership | `getent group support` |
| `last` | Show recent login records | `last -n 10` |
| `who` | Show current login sessions | `who` |

`getent` is useful because accounts may come from local files or another configured identity source.

## Basic administration in a lab VM

```bash
sudo groupadd support
sudo useradd -m -s /bin/bash trainee
sudo passwd trainee
sudo usermod -aG support trainee
```

The `-aG` combination appends a supplementary group. Using `-G` without `-a` can replace existing supplementary groups.

## Verification

```bash
id trainee
getent passwd trainee
getent group support
```

A new login session is normally required before a running shell receives updated group membership.

## Account files

- `/etc/passwd` stores account information, not password hashes.
- `/etc/shadow` stores password hashes and aging information and is restricted.
- `/etc/group` stores local group information.
- `/etc/skel` provides initial files for a new home directory.

## Common mistakes

- Do not publish `/etc/shadow` or password hashes.
- Avoid editing account databases directly when commands such as `useradd`, `usermod` and `passwd` can validate the change.
- Confirm the username before locking, deleting or changing an account.
- A service account may use a non-login shell intentionally.
