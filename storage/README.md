# Storage and Filesystems

## Commands

| Command | Purpose | Example |
|---|---|---|
| `lsblk -f` | Show block devices, filesystems and mount points | `lsblk -f` |
| `blkid` | Show filesystem UUIDs and types | `sudo blkid` |
| `df -hT` | Show space by mounted filesystem | `df -hT` |
| `du -xhd1` | Summarize one filesystem by directory | `sudo du -xhd1 /var` |
| `findmnt` | Show the current mount tree | `findmnt` |
| `mount` | Mount a filesystem | `sudo mount /dev/vdb1 /mnt/lab` |
| `umount` | Unmount a filesystem | `sudo umount /mnt/lab` |

`df` reports filesystem usage. `du` adds the files visible under a directory. Their totals can differ because of deleted-open files, mount points or permissions.

## Space investigation

```bash
df -hT
sudo du -xhd1 /var | sort -h
sudo find /var -xdev -type f -size +500M -print
```

`-xdev` keeps the search on one filesystem. File size alone does not prove that a file is safe to delete.

## Mount verification

After changing a lab entry in `/etc/fstab`:

```bash
sudo mount -a
findmnt /mnt/lab
```

`mount -a` helps detect an invalid entry before the next reboot.

## Common mistakes

- Device names such as `/dev/sdb1` can change. UUIDs are normally more stable for `/etc/fstab`.
- Do not run `fsck` on a mounted read-write filesystem.
- Check the current kernel before removing files from `/boot`.
- `du` without `-x` can cross into other mounted filesystems.
- Always confirm the exact device and mount point before formatting or unmounting.
