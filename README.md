# biglinux-mirrorlist

Mirrorlists for the BigLinux pacman repositories
(`packages.biglinux.com.br`). With them, `/etc/pacman.conf` does not carry
server URLs, like the Arch Linux and Manjaro repositories:

```ini
[biglinux-testing]
SigLevel = PackageRequired
Include = /etc/pacman.d/biglinux-testing-mirrorlist

[biglinux-stable]
SigLevel = PackageRequired
Include = /etc/pacman.d/biglinux-stable-mirrorlist

[biglinux-extra]
SigLevel = PackageRequired
Include = /etc/pacman.d/biglinux-extra-mirrorlist
```

`biglinux-testing` is optional: it receives packages before `biglinux-stable`.
`biglinux-extra` holds AUR and third-party packages.

There is one file per repository because pacman only expands `$repo` (the
section name, e.g. `biglinux-stable`) and `$arch` in a server URL, while the
directories on the server are `testing`, `stable` and `extra`.

## Files

| File | Installed to |
|---|---|
| `biglinux-testing-mirrorlist` | `/etc/pacman.d/biglinux-testing-mirrorlist` |
| `biglinux-stable-mirrorlist` | `/etc/pacman.d/biglinux-stable-mirrorlist` |
| `biglinux-extra-mirrorlist` | `/etc/pacman.d/biglinux-extra-mirrorlist` |

The files are marked as `backup` in the package: local edits are kept on
upgrade (pacman saves the new version as `.pacnew`).

## Adding a mirror

Add a `Server =` line to each file, in order of preference, and build a new
version of the package. The version comes from the build date.

The packages are signed: see
[biglinux-keyring](https://github.com/biglinux/biglinux-keyring) to trust the
BigLinux key.

## License

MIT
