# NVIDIA Optimus Bumblebee

Link: https://docs.fedoraproject.org/en-US/quick-docs/bumblebee/index.html

## Quick install

```console
$ sudo dnf install fedora-workstation-repositories
$ sudo dnf config-manager rpmfusion-nonfree-nvidia-driver --set-enabled
$ sudo dnf install akmod-nvidia acpi

$ dnf copr enable chenxiaolong/bumblebee
$ dnf install akmod-bbswitch bumblebee primus

$ gpasswd -a $USER bumblebee

$ systemctl enable bumblebeed

# Enable the bumblebeed service and disable the nvidia-fallback service. This
# service comes from the packaged drivers and will attempt to load nouveau if
# nvidia fails to load. However, when using Bumblebee, neither one should load
# at boot.
$ systemctl mask nvidia-fallback

$ reboot
```

