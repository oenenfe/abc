# grin

[https://github.com/mimblewimble/docs/wiki](https://github.com/mimblewimble/docs/wiki)

## Install on Ubuntu

```console
$ snap install grin

# run a grin node
$ grin

# Data directory
$ ls snap/grin/current/.grin

# Create a new wallet
$ grin.wallet init

# Restore wallet
$ grin.wallet init -r
```

Run a node on CentOS: [https://snapcraft.io/install/grin/centos](https://snapcraft.io/install/grin/centos).

## Sending and receiving grins

- [How to use the grin Wallet](https://github.com/mimblewimble/docs/wiki/How-to-use-the-Grin-wallet)
- [Grin wallet user guide](https://github.com/mimblewimble/docs/wiki/Wallet-User-Guide)

### 1. Via file

```console
# 1. Sender create a transaction file called `my_grin_transaction.tx` 
# in the current directory.
$ grin.wallet send -m file -d my_grin_transaction.tx 1.01

# 2. Recipienter create a response file called
# `my_grin_transaction.tx.response` which you must then send back to
# the sender to complete and post to the chain.
$ grin.wallet receive -i my_grin_transaction.tx

# 3. Sender post the transaction to the listening grin node, and the
# balances should confirm in both your wallet and the recipient's
# wallet after a few blocks have been found.
$ grin.wallet finalize -i my_grin_transaction.response
```

### 2. Via a running wallet listener

```console
# If the recipient is running an HTTP listener, you can send an amount
# from your wallet to theirs and post the transaction to the chain in
# a single step. If successful, the amounts will be confirmed in both
# wallets after a few blocks have been found.
$ grin.wallet send -d http://10.20.20.1:3415 10.25
```

## Configure listener

```console
# Listening via TOR
# As of v3.0.0, the wallet listener is capable of listening via a TOR
# hidden service. This means that listeners do not have to worry about
# configuring their network or firewalls so long as your machine can
# connect to the TOR network.

# The wallet listener will automatically listen via TOR so long as the
# `tor` or `tor.exe` executable is available on the system path. If
# TOR is found, the wallet will automatically configure a hidden service
# and display the wallet's listening address. This address can then be
# provided to other users to send you funds via the send command.

# Note that the TOR listener still requires the http listener to be
# active, however it does not need to be listening externally
# (i.e. with the -e) flag. So long as the TOR executable is on the
# path, it should suffice to run grin-wallet listen.

$ grin.wallet listen

# You can prevent starting the TOR listener with the `-n`,`--no-tor` flag.
# Prevent starting the TOR listener, and listen externally.
$ grin.wallet -e listen -n
```

### Example on Ubuntu

```
$ snap install grin

# Run grin node, and wait for it fully synced.
$ grin

$ grin.wallet -e listen -n
$ grin.wallet init -r

# Open port 3415/tcp
$ sudo ufw allow 3415/tcp

# Go to router settings page, and forward port 3415 for TCP.
# http://192.168.3.1

# Find external IP. If a VPN is running, just check your local external
# IP on router settings page.
$ curl ipecho.net/plain; echo
183.105.6.128

# Go to exchange's withdrawal page.
$ grin-wallet send -d http://183.105.6.128:3415 10.05
```
