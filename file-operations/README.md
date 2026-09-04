# File and Directory Operations

## Commands

| Command | Purpose | Example |
|---|---|---|
| `touch` | Create an empty file or update its timestamp | `touch notes.txt` |
| `mkdir -p` | Create a directory path | `mkdir -p lab/input` |
| `cp -i` | Copy and ask before overwriting | `cp -i notes.txt lab/` |
| `mv -i` | Move or rename and ask before overwriting | `mv -i notes.txt linux-notes.txt` |
| `rm -i` | Remove a file with a prompt | `rm -i old-notes.txt` |
| `find` | Search the live directory tree | `find . -type f -name '*.log'` |
| `file` | Inspect the detected file type | `file download.bin` |
| `stat` | Show size, mode and timestamps | `stat notes.txt` |
| `tar` | Create or extract an archive | `tar -czf lab.tar.gz lab/` |

## Practice

```bash
mkdir -p file-lab/input
touch file-lab/input/example.log
cp -i file-lab/input/example.log file-lab/example-copy.log
find file-lab -type f -name '*.log'
tar -czf file-lab.tar.gz file-lab/
tar -tzf file-lab.tar.gz
```

`tar -t` lists an archive without extracting it. This is a useful check before unpacking files into the current directory.

## Verification

```bash
ls -l file-lab
find file-lab -type f -print
tar -tzf file-lab.tar.gz
```

## Common mistakes

- `rm` does not normally move files to a recycle bin.
- `rm -r` can remove a whole directory tree. Check the exact path first.
- Shell wildcards are expanded before the command runs. Preview a pattern with `printf '%s\n' pattern*` or `ls` before using it with a destructive command.
- A file extension does not prove the file type; use `file` when the source is uncertain.
- Quote paths that contain spaces: `cp 'my notes.txt' backup/`.
