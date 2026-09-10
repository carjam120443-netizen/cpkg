# cpkg

**cpkg** is a renamed, lightweight package-manager frontend for Debian and Ubuntu.

It does not replace APT's repository system. Instead, it provides the `cpkg` command while using the system's existing APT configuration, Debian/Ubuntu repositories, package database, and dependency resolver.

## Install

From a cloned checkout:

```bash
sudo install -m 755 cpkg /usr/local/bin/cpkg
```

Then:

```bash
cpkg update
cpkg install git
cpkg search firefox
cpkg show bash
cpkg upgrade
```

## Commands

| cpkg command | What it does |
|---|---|
| `cpkg install <pkg...>` | Install packages |
| `cpkg remove <pkg...>` | Remove packages |
| `cpkg purge <pkg...>` | Remove packages and configuration files |
| `cpkg update` | Refresh APT package lists |
| `cpkg upgrade` | Upgrade installed packages |
| `cpkg full-upgrade` | Perform a full upgrade |
| `cpkg autoremove` | Remove unused dependencies |
| `cpkg search <term>` | Search available packages |
| `cpkg show <pkg...>` | Show package information |
| `cpkg list` | List installed packages |
| `cpkg policy <pkg...>` | Show package versions and repository policy |
| `cpkg clean` | Clean downloaded package files |
| `cpkg autoclean` | Remove obsolete package files |

## How it works

cpkg is intentionally simple:

- Package downloads come from the repositories configured in `/etc/apt/sources.list` and `/etc/apt/sources.list.d/`.
- Dependency resolution and package installation are handled by Debian/Ubuntu APT and dpkg.
- Privileged operations use `sudo` when cpkg is not already running as root.
- `apt-cache` and `dpkg-query` provide read-only package information.

So on a normal Debian or Ubuntu installation, `cpkg install <package>` ultimately performs the corresponding APT operation.

## Philosophy

cpkg is a renamed package-manager interface, not a new package format or repository ecosystem. The goal is to provide a small, familiar command while remaining compatible with the Debian/Ubuntu package infrastructure.

## License

See the repository license for project licensing information.
