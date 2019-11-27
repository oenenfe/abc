# Nodejs

## Install Node.js via binary archive on Ubuntu

```console
$ wget https://nodejs.org/dist/v12.13.1/node-v12.13.1-linux-x64.tar.xz

$ sudo mkdir -p /usr/local/lib/nodejs
$ sudo tar -xJvf node-v12.13.1-linux-x64.tar.xz -C /usr/local/lib/nodejs

$ vi ~/.profile
VERSION=v12.13.1
DISTRO=linux-x64
export PATH=/usr/local/lib/nodejs/node-$VERSION-DISTRO/bin:$PATH
```

