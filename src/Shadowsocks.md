# Shadowsocks

## Install shadowsocks on CentOS 8
`pip` is `pip-3` or `pip-3.6` on CentOS 8. `/usr/bin/pip-3.6`

```
pip-3.6 install shadowsocks

cat > /etc/shadowsocks.json
{
  "server": "141.164.41.55",
  "server_port": 13800,
  "local_address": "127.0.0.1",
  "local_port": 8080,
  "password": "18989487630",
  "timeout": 300,
  "method": "aes-256-cfb",
  "fast_open": false
}

firewall-cmd --add-port=8080/tcp --zone=public --permanent
firewall-cmd --add-port=13800/tcp --zone=public --permanent

firewall-cmd --list-ports
firewall-cmd --reload

ssserver -c /etc/shadowsocks.json -d start

# If Error
# undefined symbol: EVP_CIPHER_CTX_cleanup
vi /usr/local/lib/python3.6/site-packages/shadowsocks/crypto/openssl.py
%s/CIPHER_CTX_cleanup/CIPHER_CTX_reset/g

ssserver -c /etc/shadowsocks.json -d stop
```
