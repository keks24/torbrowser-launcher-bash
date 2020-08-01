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
gpg: assuming signed data in '/home/ramon/.cache/torbrowser/tor-browser-linux64-9.5.3_en-US.tar.xz'
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
