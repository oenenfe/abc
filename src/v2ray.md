# v2ray

## On Linux

```console
$ bash <(curl -L -s https://install.direct/go.sh)

$ vi /etc/v2ray/config.json
{
  "log": {
    "loglevel": "warning"
  },
  "inbounds": [{
    "port": 1080,
    // IP address to listen on. Change to "0.0.0.0" to listen on all network interfaces.
    "listen": "127.0.0.1",
    "tag": "socks-inbound",
    "protocol": "socks", // "http" on Windows 10
    "settings": {
      "auth": "noauth",
      "udp": true
    },
    "sniffing": {
      "enabled": true,
      "destOverride": ["http", "tls"]
    }
  }],
  "outbounds": [{
    "protocol": "vmess",
    "settings": {
      "vnext": [{
        "address": "*.*.*.*",
        "port": 23783,
        "users": [{
          "id": "********-****-****-****-************",
          "alterId": 64
        }]
      }]
    },
    "tag": "direct"
  },{
    "protocol": "blackhole",
    "settings": {},
    "tag": "blocked"
  }, {
    "protocol": "freedom",
    "settings": {},
    "tag": "direct"
}],

  // Transport is for global transport settings. If you have multiple transports with same settings
  // (say mKCP), you may put it here, instead of in each individual inbound/outbounds.
  //"transport": {},

  // Routing controls how traffic from inbounds are sent to outbounds.
  "routing": {
    "domainStrategy": "IPOnDemand",
    "rules":[
      {
        // Blocks access to private IPs. Remove this if you want to access your router.
        "type": "field",
        "ip": ["geoip:cn", "geoip:private"],
        "outboundTag": "direct"
      },
      {
        // Blocks major ads.
        "type": "field",
        "domain": ["geosite:cn","geosite:category-ads"],
        "outboundTag": "direct"
      }
    ]
  },

  // Dns settings for domain resolution.
  "dns": {
    // Static hosts, similar to hosts file.
    "hosts": {
      // Match v2ray.com to another domain on CloudFlare. This domain will be used when querying IPs for v2ray.com.
      "domain:v2ray.com": "www.vicemc.net",

      // The following settings help to eliminate DNS poisoning in mainland China.
      // It is safe to comment these out if this is not the case for you.
      "domain:github.io": "pages.github.com",
      "domain:wikipedia.org": "www.wikimedia.org",
      "domain:shadowsocks.org": "electronicsrealm.com"
    },
    "servers": [
      "1.1.1.1",
      {
        "address": "114.114.114.114",
        "port": 53,
        // List of domains that use this DNS first.
        "domains": [
          "geosite:cn"
        ]
      },
      "8.8.8.8",
      "localhost"
    ]
  },

  // Policy controls some internal behavior of how V2Ray handles connections.
  // It may be on connection level by user levels in 'levels', or global settings in 'system.'
  "policy": {
    // Connection policys by user levels
    "levels": {
      "0": {
        "uplinkOnly": 0,
        "downlinkOnly": 0
      }
    },
    "system": {
      "statsInboundUplink": false,
      "statsInboundDownlink": false
    }
  },

  // Stats enables internal stats counter.
  // This setting can be used together with Policy and Api. 
  //"stats":{},

  // Api enables gRPC APIs for external programs to communicate with V2Ray instance.
  //"api": {
    //"tag": "api",
    //"services": [
    //  "HandlerService",
    //  "LoggerService",
    //  "StatsService"
    //]
  //},

  // You may add other entries to the configuration, but they will not be recognized by V2Ray.
  "other": {}
}

$ service v2ray start
```
