# MTProxy

## On CentOS/RHEL:

```console
$ yum install openssl-devel zlib-devel
$ yum groupinstall "Development Tools"

$ git clone https://github.com/TelegramMessenger/MTProxy

$ cd MTProxy
$ make && cd objs/bin

$ curl -s https://core.telegram.org/getProxySecret -o proxy-secret
$ curl -s https://core.telegram.org/getProxyConfig -o proxy-multi.conf

$ head -c 16 /dev/urandom | xxd -ps

$ firewall-cmd --zone=public --permanent --add-port=8888/tcp
$ firewall-cmd --zone=public --permanent --add-port=443/tcp

$ firewall-cmd --reload

$ ./mtproto-proxy -u nobody -p 8888 -H 443 -S <secret> --aes-pwd proxy-secret proxy-multi.conf -M 1
```

