# Permissions and Ownership

## Reading a mode

```text
-rw-r----- 1 marcelo support 1200 Sep 4 10:00 report.txt
```

- The first character identifies the file type.
- The next three positions are owner permissions.
- The next three are group permissions.
- The last three are permissions for others.

For a directory, read permission lists names and execute permission allows traversal.

## Commands

| Command | Purpose | Example |
|---|---|---|
| `ls -l` | Show mode and ownership | `ls -l report.txt` |
| `ls -ld` | Check the directory itself | `ls -ld reports/` |
| `stat` | Show detailed mode and metadata | `stat report.txt` |
| `chmod` | Change mode bits | `chmod 640 report.txt` |
| `chown` | Change owner, optionally group | `sudo chown marcelo:support report.txt` |
| `chgrp` | Change only the group | `sudo chgrp support report.txt` |
| `getfacl` | Display access ACLs | `getfacl report.txt` |
| `setfacl` | Add or change an ACL | `setfacl -m u:analyst:r report.txt` |

## Practice

```bash
touch report.txt
chmod 640 report.txt
ls -l report.txt
stat -c '%A %a %U %G' report.txt
```

The `stat -c` format is from GNU `stat` and may differ on other systems.

## Verification

Test access as the intended account when possible:

```bash
sudo -u <user> test -r /path/to/report.txt
echo $?
```

An exit status of `0` means the read test succeeded.

## Common mistakes

- `chmod 777` grants write access to everyone and usually hides the real ownership or group problem.
- Changing only the file can fail when a parent directory does not allow traversal. Use `namei -l <path>`.
- `chown -R` affects an entire tree. Inspect the exact target first.
- ACL masks can limit the effective permissions shown by `getfacl`.
