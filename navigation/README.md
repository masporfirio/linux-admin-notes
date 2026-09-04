# Directory Navigation

## Paths

- An absolute path starts at `/`, for example `/var/log`.
- A relative path starts from the current directory, for example `../logs`.
- `~` expands to the current user's home directory in the shell.
- `.` means the current directory and `..` means its parent.

## Commands

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Print the current directory | `pwd` |
| `ls` | List directory contents | `ls /etc` |
| `ls -la` | Include hidden files and details | `ls -la ~` |
| `cd` | Change directory | `cd /var/log` |
| `cd -` | Return to the previous directory | `cd -` |
| `cd ~` | Go to the current user's home | `cd ~` |

## Practice

```bash
pwd
cd /etc
ls -la
cd /var/log
cd -
cd ~
pwd
```

## Verification

Run `pwd` after `cd` when the next command depends on the current location.

```bash
cd /var/log && pwd
```

The `&&` means `pwd` runs only if `cd` succeeds.

## Common mistakes

- `cd etc` looks for an `etc` directory under the current path; `cd /etc` uses the system directory.
- `sudo cd /root` does not work because `cd` is a shell builtin. To open a root login shell, use `sudo -i`, then check the location with `pwd`.
- Hidden files begin with a dot and are not shown by plain `ls`.
- Before deleting or moving files with relative paths, confirm the current directory.
