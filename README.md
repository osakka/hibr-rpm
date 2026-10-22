# hibr dnf repository

Fedora, RHEL and openSUSE packages of [hibr](https://github.com/osakka/hibr),
a small, fast shell that runs the bash you already write.

## Install

```text
sudo curl -fsSL -o /etc/yum.repos.d/hibr.repo https://osakka.github.io/hibr-rpm/hibr.repo
sudo dnf install hibr
```

`dnf upgrade` keeps it current from then on. dnf asks once to import the
repository's key; check its fingerprint against the one below before saying
yes. On openSUSE, `sudo zypper addrepo https://osakka.github.io/hibr-rpm/hibr.repo`
and `sudo zypper install hibr`.

Then `hibr` runs a script, `man hibr` lists every option, and
[From bash to hibr, in ten minutes](https://github.com/osakka/hibr/blob/main/docs/tutorial.md)
is the place to start.

## What there is

| | |
|---|---|
| architectures | x86_64 (aarch64 to follow) |
| needs | glibc 2.35 or later: Fedora 36 or newer, RHEL 10, openSUSE Leap 15.6 or Tumbleweed |
| installs | `/usr/bin/hibr`, modules in `/usr/lib/hibr`, `man hibr`, and the text desktop (`desktop`) |

The package holds the same files as the Debian package of the same version,
byte for byte, and depends on nothing but glibc. What a module loads only
when it is first wanted -- libpng and libturbojpeg for pictures, OpenSSL for
TLS, FFmpeg, Poppler, Argon2, Xvfb -- is a weak dependency, named by library
so it resolves on any of these distributions.

## The signing key

```text
hibr apt repository (signs https://github.com/osakka/hibr-apt) <osakka@gmail.com>
fingerprint A1E3 CA78 8A8F B020 52DA  22B4 1303 5BE1 B167 4431
```

The same key signs the apt, dnf and pacman repositories. Every package is
signed, and so is the metadata (`repodata/repomd.xml.asc`).
