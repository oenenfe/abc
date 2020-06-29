# Ubuntu 18.04

- [Ubuntu releases](http://releases.ubuntu.com/)
- [Verify iso how to](https://help.ubuntu.com/community/VerifyIsoHowto)

## Enable Wi-Fi Adapter (Lenove R720)

```console
$ rfkill list all

$ sudo -i touch /etc/modprobe.d/ideapad.conf cat > /etc/modprobe.d/ideapad.conf
$ blacklist ideapad_laptop

$ reboot
```

## Install basic development tools

```console
$ sudo apt install build-essential

# required for npm
# https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally#manually-change-npms-default-directory
$ sudo apt install libtool
```

## UFW

[Firewalls introducations](https://help.ubuntu.com/community/Firewall)

The default firewall configuration tool for Ubuntu is ufw. **By default UFW is
disabled.**
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

```console
# Enable ufw
$ sudo ufw enable

# To check the status of UFW:
$ sudo ufw status verbose
[sudo] password for youruser:
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

# Disable ufw
$ sudo ufw disable

# Allow
# sudo ufw allow <port>/<optional: protocol>

# To allow incoming tcp packets on port 53
$ sudo ufw allow 53/tcp

# To allow incoming udp packets on port 53
$ sudo ufw allow 53/udp

# To allow incoming tcp and udp packet on port 53
$ sudo ufw allow 53

# Deny
# sudo ufw deny <port>/<optional: protocol>

$ sudo ufw deny 53/tcp
$ sudo ufw deny 53/udp
$ sudo ufw deny 53

# Delete Existing Rule
# To delete a rule, simply prefix the original rule with delete. For example, if the original rule was:
$ sudo ufw delete deny 80/tcp
```

## Tutorials

- [How to verify your Ubuntu
  Download](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)
- [Create a bootable USB stick on
  Ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

