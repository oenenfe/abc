# Ubuntu 18.04

- [Ubuntu releases](http://releases.ubuntu.com/)
- [Verify iso how to](https://help.ubuntu.com/community/VerifyIsoHowto)

## Enable Wi-Fi Adapter (Lenove R720)

```console
rfkill list all

sudo -i touch /etc/modprobe.d/ideapad.conf cat > /etc/modprobe.d/ideapad.conf
blacklist ideapad_laptop

reboot
```

# Tutorials

- [How to verify your Ubuntu
  Download](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)
- [Create a bootable USB stick on
  Ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)
