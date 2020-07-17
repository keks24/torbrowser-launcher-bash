# Introduction
`torbrowser-launcher-bash` downloads and runs torbrowser via https://dist.torproject.org/torbrowser/ using bash.

# Prerequisites
* The following packages are installed:
```no-highlight
aria2c
curl
gpg
grep
head
id
mkdir
pixz
rm
sed
sort
tar
```

* The path `/home/$(id --user --name)/bin/` exists in the `${PATH}` variable:
```bash
$ echo "${PATH//:/\n}"
```
```
/home/ramon/bin
/usr/local/bin
/usr/bin
/bin
/usr/local/sbin
/usr/sbin
/sbin
/usr/local/games
/usr/games
/usr/lib/llvm/6/bin
/opt/bin
```

# Installation
Clone the repository into your current working directory:
```bash
$ git clone "https://gitlab.com/keks24/torbrowser-launcher-bash.git"
```

Copy all necessary files:
```bash
$ cd "torbrowser-launcher-bash/"
$ cp "home/username/bin/torbrowser" "/home/$(id --user --name)/bin/"
$ chmod 755 "/home/$(id --user --name)/bin/torbrowser"
```

# Usage
1. Execute `torbrowser`. This will download the `latest` archive from https://dist.torproject.org/torbrowser/ to `/home/username/.cache/torbrowser/`:
```bash
$ torbrowser
```
```no-highlight
07/17 20:33:42 [NOTICE] Downloading 2 item(s)

07/17 20:33:42 [WARN] aria2c had to connect to the other side using an unknown TLS protocol. The integrity and confidentiality of the connection might be compromised.
Peer: dist.torproject.org (2a01:4f8:fff0:4f:266:37ff:fe2c:5d19:443)

07/17 20:33:42 [WARN] aria2c had to connect to the other side using an unknown TLS protocol. The integrity and confidentiality of the connection might be compromised.
Peer: dist.torproject.org (2a01:4f8:fff0:4f:266:37ff:fe2c:5d19:443)

07/17 20:33:42 [NOTICE] Download complete: /home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.1_en-US.tar.xz.asc

07/17 20:33:42 [WARN] aria2c had to connect to the other side using an unknown TLS protocol. The integrity and confidentiality of the connection might be compromised.
Peer: dist.torproject.org (2a01:4f8:fff0:4f:266:37ff:fe2c:5d19:443)
[#c3547d 65MiB/75MiB(86%) CN:1 DL:13MiB]
07/17 20:33:48 [NOTICE] Download complete: /home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.1_en-US.tar.xz

Download Results:
gid   |stat|avg speed  |path/URI
======+====+===========+=======================================================
6c6998|OK  |    15KiB/s|/home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.1_en-US.tar.xz.asc
c3547d|OK  |    13MiB/s|/home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.1_en-US.tar.xz

Status Legend:
(OK):download completed.
gpg: assuming signed data in '/home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.1_en-US.tar.xz'
gpg: Signature made Mon Jun 29 20:11:14 2020 CEST
gpg:                using RSA key EB774491D9FF06E2
gpg: Can't check signature: No public key
tor-browser_en-US/
tor-browser_en-US/Browser/
tor-browser_en-US/Browser/.config/
tor-browser_en-US/Browser/.config/gtk-3.0/
tor-browser_en-US/Browser/.config/gtk-3.0/settings.ini
tor-browser_en-US/Browser/TorBrowser/
tor-browser_en-US/Browser/TorBrowser/Data/
tor-browser_en-US/Browser/TorBrowser/Data/Browser/
tor-browser_en-US/Browser/TorBrowser/Data/Browser/Caches/
tor-browser_en-US/Browser/TorBrowser/Data/Browser/profile.default/
tor-browser_en-US/Browser/TorBrowser/Data/Browser/profile.default/bookmarks.html
tor-browser_en-US/Browser/TorBrowser/Data/Browser/profile.default/extensions/
tor-browser_en-US/Browser/TorBrowser/Data/Browser/profile.default/extensions/https-everywhere-eff@eff.org.xpi
tor-browser_en-US/Browser/TorBrowser/Data/Browser/profile.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}.xpi
tor-browser_en-US/Browser/TorBrowser/Data/Browser/profiles.ini
[...]
tor-browser_en-US/Browser/tbb_version.json
tor-browser_en-US/Browser/update-settings.ini
tor-browser_en-US/Browser/updater
tor-browser_en-US/Browser/updater.ini
tor-browser_en-US/start-tor-browser.desktop
Launching './Browser/start-tor-browser --detach'...
```

2. It might be necessary to provide a specific version, since this script is not perfect:
```bash
$ torbrowser --torbrowser-version 9.5.1
```

---

```bash
$ torbrowser --help
```
```no-highlight
torbrowser - Download and run the latest torbrowser version

Usage: torbrowser [options]

OPTIONS
  -h, --help
     Display this help text.

  -i, --include-alpha-builds
     Include alpha builds.

  -r, --redownload
     Remove all files in '/home/username/.cache/torbrowser' and redownload the latest torbrowser version.

  -t, --torbrowser-version <version>
     Specify an existing torbrowser version.

  -v, --version
     Displays the current version of this script.

EXAMPLES:
  Download and run the latest alpha build:
     torbrowser --include-alpha-builds

  Download and run a specific torbrowser version:
     torbrowser --torbrowser-version 9.5

  Remove all files in '/home/username/.cache/torbrowser', download and run the latest alpha build:
     torbrowser --redownload --include-alpha-builds

  Remove all files in '/home/username/.cache/torbrowser' and download a specific torbrowser version:
     torbrowser --redownload --torbrowser-version 9.5.1
```
