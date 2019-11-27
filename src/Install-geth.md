# Install geth

- https://github.com/ethereum/wiki/wiki/JSON-RPC
- https://ethereum.gitbooks.io/frontier-guide/content/index.html

## Option 1 (Fast install on Ubuntu)

```console
$ sudo add-apt-repository -y ppa:ethereum/ethereum
$ sudo apt update
$ sudo apt install ethereum
```

## Option 2

Download: https://geth.ethereum.org/downloads/

### 1. Verify Download

#### 1.1 MD5 checksum

Be aware that the MD5 checksums are provided by our binary hosting platform
(Azure Blobstore) to help check for download errors. For security guarantees
please verify any downloads via the attached PGP signature files (see OpenPGP
Signatures below for details).

```console
$ cd ~/Download

$ wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.9.7-a718daa6.tar.gz

$ md5sum geth-linux-amd64-1.9.7-a718daa6.tar.gz
1d699d7b4450b4fc82c5ebf3a6c2936f  geth-linux-amd64-1.9.7-a718daa6.tar.gz
# Compare `1d699d7b4450b4fc82c5ebf3a6c2936f` to Checksum (MD5) on
# https://geth.ethereum.org/downloads/.
```

#### 1.2 GPG checksum

```console
$ cd ~/Download

$ wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.9.7-a718daa6.tar.gz

# Import Public Key (Found Linux Builder ID on
# https://geth.ethereum.org/downloads/)
$ gpg --recv-keys 9BA28146

# Verify builds
$ gpg --verify geth-linux-amd64-1.5.0-d0c820ac.tar.gz.asc
gpg: assuming signed data in 'geth-linux-amd64-1.9.7-a718daa6.tar.gz'
gpg: Signature made Thu 07 Nov 2019 04:37:00 PM CST
gpg:                using RSA key A61A13569BA28146
gpg: Good signature from "Go Ethereum Linux Builder <geth-ci@ethereum.org>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: FDE5 A1A0 44FA 13D2 F7AD  A019 A61A 1356 9BA2 8146
```

### 2. Install

```console
$ tar xzf geth-linux-amd64-1.9.7-a718daa6.tar.gz
$ sudo install -m 0755 -o root -g root -t /usr/local/bin bitcoin-0.18.0/bin/* geth-linux-amd64-1.9.7-a718daa6/geth
$ which geth
/usr/local/bin/geth
```

