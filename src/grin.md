# grin

[https://github.com/mimblewimble/docs/wiki](https://github.com/mimblewimble/docs/wiki)

## Run a node on vultr

[https://snapcraft.io/install/grin/centos](https://snapcraft.io/install/grin/centos)

```console
$ wget https://github.com/mimblewimble/grin/releases/download/v3.1.1/grin-v3.1.1-linux-amd64.tar.gz
$ sha256sum grin-v3.1.1-linux-amd64.tar.gz
7f0346b7ca0768989a0a11f62e56da743a72a208e99d5f3409f22112c4dd8def  grin-v3.1.1-linux-amd64.tar.gz

$ tar -xzvf grin-v3.1.1-linux-amd64.tar.gz

$ ./grin/grin
./grin/grin: error while loading shared libraries: libncursesw.so.5: cannot open shared object file: No such file or directory

$ yum install libncurses*

$ ./grin/grin
```

## Install on Ubuntu

```console
snap install grin

# run a grin node
grin

# Data directory
ls snap/grin/current/.grin

# Create a new wallet
grin.wallet init

# Restore wallet
# grin.wallet init -r
```

## Sending and receiving grins

[How to use the grin Wallet](https://github.com/mimblewimble/docs/wiki/How-to-use-the-Grin-wallet)

### 1. Via file

```console
# 1.Sender
grin.wallet send -m file -d my_grin_transaction.tx 1.01
# This will create a transaction file called `my_grin_transaction.tx` in the current directory.

# 2.Recipienter
grin.wallet receive -i my_grin_transaction.tx
# This will create a response file called `my_grin_transaction.tx.response` which you must then send back to the sender to complete and post to the chain.

# 3.Sender
grin.wallet finalize -i my_grin_transaction.response
# This will post the transaction to the listening grin node, and the balances should confirm in both your wallet and the recipient's wallet after a few blocks have been found.
```

### 2. Via a running wallet listener

```console
# If the recipient is running an HTTP listener, you can send an amount from your wallet to theirs and post the transaction to the chain in a single step:
grin.wallet send -d http://10.20.20.1:3415 10.25
# If successful, the amounts will be confirmed in both wallets after a few blocks have been found.
```

## Configure listener

```console
# 在 v2.0.0 版本下；grin-wallet 默认只监听本地的请求。
grin.wallet listen

# 有两种方式可以开启监听外部请求。
# 1. 编辑 grin-wallet.toml，把 api_listener_interface 的值 127.0.0.1 改为 # 0.0.0.0。
# 2. 或者直接加参数 -e。
grin.wallet -e listen

# 从 v3.0.0 开始，grin-wallet 默认会以 tor 服务进行监听；只要 tor
# 可执行文件在路径中可用，钱包侦听器会自动通过 tor 监听。这种情况下，无需 -e 参数；然而假如 tor 不可用，此时因为没有加 -e 参数，默认 http 只监听本地。
grin.wallet listen

# 不启用 tor 模式监听；并且开启外部请求监听。
grin.wallet -e listen -n
```
