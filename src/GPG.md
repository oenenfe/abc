GPG
===

## Example

### 1. Bitcoin core

```console
cd ~/Download

wget https://bitcoin.org/bin/bitcoin-core-0.18.1/bitcoin-0.18.1-x86_64-linux-gnu.tar.gz
wget https://bitcoin.org/bin/bitcoin-core-0.18.1/SHA256SUMS.asc
wget https://bitcoin.org/laanwj-releases.asc

gpg --import laanwj-releases.asc

# 1. Using GPG signature to verify checksum file
gpg --verify SHA256SUMS.asc

# 2. Verify the downloaded file.
sha256sum -c SHA256SUMS.asc 2>&1 | grep OK
```

### Geth (Go ethereum)

```console
$ cd ~/Download
$ wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.9.7-a718daa6.tar.gz

# Import Public Key (Found Linux Builder ID on https://geth.ethereum.org/downloads/)
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

----

## Common usage commands

### List keys

```console
$ gpg --list-keys
$ gpg --list-keys --keyid-format short
$ gpg --list-keys --keyid-format long
$ gpg --list-keys --with-fingerprint

$ gpg --list-keys --keyid-format short --with-fingerprint
$ gpg --list-keys --keyid-format long --with-fingerprint
```

### Import keys

```console
$ wget https://bitcoin.org/laanwj-releases.asc
$ gpg --import laanwj-releases.asc

# Import from key server with KEYID
$ gpg --recv-keys 9BA28146

$ gpg --verify SHA256SUMS.gpg --keyid-format short
$ gpg --verify SHA256SUMS.gpg --keyid-format long
gpg: Signature made Thu Apr  5 22:19:36 2018 EDT
                    using DSA key ID 46181433FBB75451
gpg: Can't check signature: No public key

# Prefix them with `0x`:
$ gpg --recv-keys 0x46181433FBB75451 --keyserver hkp://keyserver.ubuntu.com
```

### Delete keys

```console
$ gpg --list-keys --keyid-format short
/home/foobar/.gnupg/pubring.kbx
------------------------------
pub   rsa4096/D2A67EAC 2016-11-07 [SC]
      Key fingerprint = C4B3 2BB1 F603 4241 A9E6  50A1 9417 309E D2A6 7EAC
uid         [ unknown] Go Ethereum Windows Builder <geth-ci@ethereum.org>

$ gpg --delete-keys D2A67EAC
```

----

## md5 & sha256

```console
$ wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.9.7-a718daa6.tar.gz
$ md5sum geth-linux-amd64-1.9.7-a718daa6.tar.gz
1d699d7b4450b4fc82c5ebf3a6c2936f  geth-linux-amd64-1.9.7-a718daa6.tar.gz

$ wget https://releases.parity.io/ethereum/v2.5.10/x86_64-unknown-linux-gnu/parity
$ sha256sum parity
9a746fa8a480e8c8828f7b9f54b74e102db5624f121a3b4f7329a380382cf032  parity
```
