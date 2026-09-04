# Package Management

## Debian and Ubuntu

| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh repository metadata |
| `apt list --upgradable` | Show available upgrades |
| `sudo apt install <package>` | Install through configured repositories |
| `sudo apt remove <package>` | Remove a package and keep configuration |
| `sudo apt purge <package>` | Remove a package and its package-managed configuration |
| `apt-cache policy <package>` | Show available and installed versions |
| `dpkg -L <package>` | List files installed by a package |
| `dpkg -S <path>` | Find which installed package owns a path |
| `sudo dpkg --audit` | Report incomplete package states |
| `sudo apt-get check` | Check dependency consistency |

`apt update` refreshes metadata; it does not upgrade installed packages.

## RPM-based systems

| Command | Purpose |
|---|---|
| `dnf info <package>` | Show package information |
| `sudo dnf install <package>` | Install a package |
| `sudo dnf remove <package>` | Remove a package after reviewing the transaction |
| `rpm -q <package>` | Query an installed package |
| `rpm -ql <package>` | List files from an installed package |
| `rpm -qf <path>` | Find the package that owns a path |

## Verification

```bash
command -v <program>
<program> --version
dpkg -s <package>
```

The program check and package database answer different questions. A package may be installed without placing its command in the current `PATH`.

## Common mistakes

- Do not delete package-manager lock files. Check which package process owns the lock.
- Review the removal list before confirming `apt remove`, `apt autoremove` or `dnf remove`.
- A package download succeeding does not prove that configuration finished; check `dpkg --audit` after a Debian repair.
- `dpkg -i` installs a local package but does not provide the same dependency handling as installing through `apt`.
