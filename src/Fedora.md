# Fedora

## Disable NVIDIA graphic crad in BIOS.

#### → BIOS Settings

- #### ▶︎ Step by step
  1. Press `F2` enter **BIOS**
  2. Select tab `Configuration`
  3. Go to item `Graphic Device`
  4. Select `UMA only`
- #### ▶︎ Visualisation
  - [ ] Information
  - [x] **Configuration**
    - [ ] ...
    - [x] **Graphic Device**
      - [ ] Discrete
      - [x] **UMA only**
    - [ ] ...
  - [ ] Security
  - [ ] Boot
  - [ ] Exit
  
- **[Discrete]** Enable the integrated and discrete graphic controller. System will choose graphic.
- **[UMA only]** Enable integrated graphic controller only.

## Remove old kernels

```console
sudo dnf update kernel*
reboot

uname -a
rpm -qa | grep kernel
sudo dnf remove kernel-4.16.*-300.fc29.x86_64
```

## Enable WI-FI

```console
sudo -i
cat > /etc/modprobe.d/ideapad.conf
blacklist ideapad_laptop

reboot
```

## Install flash (64-bit x86_64)

```console
sudo rpm -ivh http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm
sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
sudo dnf install flash-plugin alsa-plugins-pulseaudio libcurl
```
