# Bitcoin Core

Download: https://bitcoin.org/en/download

## Option 1

```console
$ cd ~/Download

$ wget https://bitcoin.org/bin/bitcoin-core-0.18.1/bitcoin-0.18.1-x86_64-linux-gnu.tar.gz

# Download the release signature document
$ wget https://bitcoin.org/bin/bitcoin-core-0.18.1/SHA256SUMS.asc

# 1. First verify that the signature document itself is authentic
# Download the relevant GPG signing key
$ wget https://bitcoin.org/laanwj-releases.asc

# - 1.1 Import the public key
$ gpg --import laanwj-releases.asc

# - 1.2 Verify that key was imported
$ gpg --list-keys

# - 1.3 Check Signatures Document
$ gpg --verify SHA256SUMS.asc

# 2. Check the Authenticity of the Download: SHA256 Checksum
$ sha256sum -c SHA256SUMS.asc 2>&1 | grep OK
bitcoin-0.18.1-x86_64-linux-gnu.tar.gz: OK
```

## Option 2 

```console
$ cd ~/Download

$ wget https://bitcoin.org/bin/bitcoin-core-0.18.1/bitcoin-0.18.1-x86_64-linux-gnu.tar.gz
$ wget https://bitcoin.org/bin/bitcoin-core-0.18.1/SHA256SUMS.asc

# 1. First verify that the signature document itself is authentic
# - 1.1 Find out the key id
$ gpg --verify SHA256SUMS.asc
gpg: Signature made Fri 09 Aug 2019 03:08:43 PM CST
gpg:                using RSA key 90C8019E36C2E964
gpg: Can't check signature: No public key

# - 1.2 Request key from the Ubuntu key server.
# Note that the ID numbers are hexadecimal, so we prefix them with 0x:
$ gpg --recv-keys 0x90C8019E36C2E964 --keyserver hkp://keyserver.ubuntu.com

# - 1.3 Verify that key was imported
$ gpg --list-keys 0x90C8019E36C2E964 --with-fingerprint

# - 1.4 Verify the checksum file using the signature
$ gpg --verify SHA256SUMS.asc

# 2. Check the Authenticity of the Download
$ sha256sum -c SHA256SUMS.asc 2>&1 | grep OK
bitcoin-0.18.1-x86_64-linux-gnu.tar.gz: OK
```

