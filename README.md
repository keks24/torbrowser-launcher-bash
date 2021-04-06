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

* The `Tor Browser Developers` GPG public key is `imported` and `signed by your private key`:
```bash
$ gpg --auto-key-locate nodefault,wkd --locate-keys torbrowser@torproject.org
```
```no-highlight
gpg: key 4E2C6E8793298290: public key "Tor Browser Developers (signing key) <torbrowser@torproject.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1
pub   rsa4096 2014-12-15 [C] [expires: 2025-07-21]
      EF6E286DDA85EA2A4BA7DE684E2C6E8793298290
uid           [ unknown] Tor Browser Developers (signing key) <torbrowser@torproject.org>
sub   rsa4096 2018-05-26 [S] [expires: 2020-12-19]
```
```bash
$ gpg --lsign-key EF6E286DDA85EA2A4BA7DE684E2C6E8793298290
```
```no-highlight
pub  rsa4096/4E2C6E8793298290
     created: 2014-12-15  expires: 2025-07-21  usage: C
     trust: unknown       validity: unknown
The following key was revoked on 2015-08-26 by RSA key 4E2C6E8793298290 Tor Browser Developers (signing key) <torbrowser@torproject.org>
sub  rsa4096/2D000988589839A3
     created: 2014-12-15  revoked: 2015-08-26  usage: S
sub  rsa4096/EB774491D9FF06E2
     created: 2018-05-26  expires: 2020-12-19  usage: S
[ unknown] (1). Tor Browser Developers (signing key) <torbrowser@torproject.org>


pub  rsa4096/4E2C6E8793298290
     created: 2014-12-15  expires: 2025-07-21  usage: C
     trust: unknown       validity: unknown
 Primary key fingerprint: EF6E 286D DA85 EA2A 4BA7  DE68 4E2C 6E87 9329 8290

     Tor Browser Developers (signing key) <torbrowser@torproject.org>

This key is due to expire on 2025-07-21.
Are you sure that you want to sign this key with your
key "Ramon Fischer (ramon@sharkoon) <Ramon_Fischer@hotmail.de>" (155BE26413E699BF)

The signature will be marked as non-exportable.

Really sign? (y/N) y
```
```bash
$ gpg --list-keys EF6E286DDA85EA2A4BA7DE684E2C6E8793298290
```
```no-highlight
pub   rsa4096 2014-12-15 [C] [expires: 2025-07-21]
      EF6E286DDA85EA2A4BA7DE684E2C6E8793298290
uid           [  full  ] Tor Browser Developers (signing key) <torbrowser@torproject.org>
sub   rsa4096 2018-05-26 [S] [expires: 2020-12-19]
```

Sources:
* [Torproject - How to verify signature](https://support.torproject.org/tbb/how-to-verify-signature/)
* [Superuser - How to locally sign a GPG public key](https://superuser.com/a/1435150)

# Installation
Clone the repository into your current working directory:
```bash
$ git clone "https://codeberg.org/keks24/torbrowser-launcher-bash.git"
```

Copy all necessary files:
```bash
$ cd "torbrowser-launcher-bash/"
$ cp "home/username/bin/torbrowser" "/home/$(id --user --name)/bin/"
$ chmod 755 "/home/$(id --user --name)/bin/torbrowser"
```

# Usage
1. Execute `torbrowser`. This will download the `latest` archive from https://dist.torproject.org/torbrowser/ to `/home/$(id --user --name)/.cache/torbrowser/`:
```bash
$ torbrowser
```
```no-highlight
08/01 21:26:58 [NOTICE] Downloading 2 item(s)

08/01 21:26:58 [WARN] aria2c had to connect to the other side using an unknown TLS protocol. The integrity and confidentiality of the connection might be compromised.
Peer: dist.torproject.org (2a01:4f8:fff0:4f:266:37ff:feae:3bbc:443)

08/01 21:26:58 [WARN] aria2c had to connect to the other side using an unknown TLS protocol. The integrity and confidentiality of the connection might be compromised.
Peer: dist.torproject.org (2a01:4f8:fff0:4f:266:37ff:feae:3bbc:443)

08/01 21:26:59 [NOTICE] Download complete: /home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.3_en-US.tar.xz.asc
[#e200c8 66MiB/75MiB(88%) CN:1 DL:14MiB]
08/01 21:27:04 [NOTICE] Download complete: /home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.3_en-US.tar.xz

Download Results:
gid   |stat|avg speed  |path/URI
======+====+===========+=======================================================
923966|OK  |    15KiB/s|/home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.3_en-US.tar.xz.asc
e200c8|OK  |    13MiB/s|/home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.3_en-US.tar.xz

Status Legend:
(OK):download completed.
gpg: Signature made Fri Jul 24 18:13:05 2020 CEST
gpg:                using RSA key EB774491D9FF06E2
gpg: Good signature from "Tor Browser Developers (signing key) <torbrowser@torproject.org>" [full]
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
tor-browser_en-US/Browser/TorBrowser/Data/Tor/
tor-browser_en-US/Browser/TorBrowser/Data/Tor/geoip
tor-browser_en-US/Browser/TorBrowser/Data/Tor/geoip6
tor-browser_en-US/Browser/TorBrowser/Data/Tor/torrc
tor-browser_en-US/Browser/TorBrowser/Data/Tor/torrc-defaults
tor-browser_en-US/Browser/TorBrowser/Data/fontconfig/
tor-browser_en-US/Browser/TorBrowser/Data/fontconfig/fonts.conf
tor-browser_en-US/Browser/TorBrowser/Docs/
tor-browser_en-US/Browser/TorBrowser/Docs/ChangeLog.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Firefox.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/HTTPS-Everywhere.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Libevent.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/NoScript.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Noto-CJK-Font.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Noto-Fonts.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/PluggableTransports/
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/PluggableTransports/LICENSE
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/PluggableTransports/LICENSE.CC0
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/PluggableTransports/LICENSE.GO
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/PluggableTransports/LICENSE.SNOWFLAKE
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Tor-Launcher.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Tor.txt
tor-browser_en-US/Browser/TorBrowser/Docs/Licenses/Torbutton.txt
tor-browser_en-US/Browser/TorBrowser/Tor/
tor-browser_en-US/Browser/TorBrowser/Tor/PluggableTransports/
[...]
tor-browser_en-US/Browser/removed-files
tor-browser_en-US/Browser/start-tor-browser
tor-browser_en-US/Browser/start-tor-browser.desktop
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

# Parameters
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
     Remove all files in '/home/ramon/.cache/torbrowser' and redownload the latest torbrowser version.

  -t, --torbrowser-version <version>
     Specify an existing torbrowser version.

  -v, --version
     Displays the current version of this script.

EXAMPLES:
  Download and run the latest alpha build:
     torbrowser --include-alpha-builds

  Download and run a specific torbrowser version:
     torbrowser --torbrowser-version 9.5

  Download and run a specific torbrowser alpha version:
     torbrowser --include-alpha-builds --torbrowser-version 10.0a2

  Remove all files in '/home/ramon/.cache/torbrowser', download and run the latest alpha build:
     torbrowser --redownload --include-alpha-builds

  Remove all files in '/home/ramon/.cache/torbrowser' and download a specific torbrowser version:
     torbrowser --redownload --torbrowser-version 9.5.1
```
