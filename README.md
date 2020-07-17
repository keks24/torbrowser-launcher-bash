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

# Installation
Clone the repository into your current working directory:
```bash
$ git clone "https://gitlab.com/keks24/torbrowser-launcher-bash.git"
```

Copy all necessary files:
```bash
$ cd "torbrowser-launcher-bash/"
$ cp "home/username/bin/torbrowser" "/home/username/bin/"
$ chmod 755 "/home/username/bin/torbrowser"
```

# Usage
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
