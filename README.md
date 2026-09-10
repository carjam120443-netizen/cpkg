# cpkg

**cpkg** is a lightweight, universal package-manager frontend.

It currently supports:

- **Debian/Ubuntu and compatible systems** through APT
- **Arch Linux and compatible systems** through pacman

cpkg does not replace either distro's repository system. It detects the package manager already installed on the host and forwards commands to it, so you can use the same `cpkg` command style across different Linux families.

## Install

### Debian/Ubuntu

The GitHub Actions build produces a `.deb` package:

```bash
sudo apt install ./cpkg_1.1.0-1_all.deb
```

Or install directly from a cloned checkout:

```bash
sudo install -m 755 cpkg /usr/local/bin/cpkg
```

### Arch Linux

The GitHub Actions build also produces a pacman package in the requested `.pkg.tar.xz` format:

```bash
sudo pacman -U ./cpkg-1.1.0-1-any.pkg.tar.xz
```

Or install directly from a cloned checkout:

```bash
sudo install -m 755 cpkg /usr/local/bin/cpkg
```

## Commands

| cpkg command | APT backend | pacman backend |
|---|---|---|
| `cpkg install <pkg...>` | Install packages | Install packages |
| `cpkg remove <pkg...>` | Remove packages | Remove packages |
| `cpkg purge <pkg...>` | Remove packages and configuration files | Not supported |
| `cpkg update` | Refresh APT package lists | Refresh pacman databases |
| `cpkg upgrade` | Upgrade installed packages | Upgrade packages |
| `cpkg full-upgrade` | Full APT upgrade | Full pacman upgrade |
| `cpkg autoremove` | Remove unused dependencies | Remove orphaned packages |
| `cpkg search <term>` | Search APT packages | Search pacman repositories |
| `cpkg show <pkg...>` | Show package information | Show package information |
| `cpkg list` | List installed packages | List installed packages |
| `cpkg policy <pkg...>` | Show package versions and policy | Show repository package information |
| `cpkg clean` | Clean downloaded package files | Clean pacman cache |
| `cpkg autoclean` | Remove obsolete APT package files | Not supported |
| `cpkg backend` | Print `apt` | Print `pacman` |

## Examples

```bash
cpkg backend
cpkg update
cpkg install firefox git
cpkg search terminal
cpkg show bash
cpkg upgrade
```

On Debian or Ubuntu, `cpkg install firefox` ultimately uses APT. On Arch Linux, the same command uses pacman. Your normal system repositories and dependency handling remain in control.

## Package builds

GitHub Actions automatically builds both package formats:

- `.deb` for Debian/Ubuntu
- `.pkg.tar.xz` for Arch/pacman

The workflows are in `.github/workflows/` and can also be started manually with **workflow_dispatch**.

## Philosophy

cpkg is meant to be a **universal command interface**, not a new repository ecosystem. The goal is to make common package-management commands feel familiar across multiple Linux families while still using each distribution's native package manager underneath.

## License

See the repository license for project licensing information.
