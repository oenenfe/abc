# grin

[https://github.com/mimblewimble/docs/wiki](https://github.com/mimblewimble/docs/wiki)

## Install on Ubuntu

```
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

```
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

```
# If the recipient is running an HTTP listener, you can send an amount from your wallet to theirs and post the transaction to the chain in a single step:
grin.wallet send -d http://10.20.20.1:3415 10.25
# If successful, the amounts will be confirmed in both wallets after a few blocks have been found.
```

