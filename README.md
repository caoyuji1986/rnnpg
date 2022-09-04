{
  "log": {
    "error": "",
    "loglevel": "info",
    "access": ""
  },
  "inbounds": [
    {
      "sniffing": {
        "enabled": true,
        "destOverride": [
          "tls",
          "http"
        ]
      },
      "listen": "127.0.0.1",
      "protocol": "socks",
      "settings": {
        "udp": true,
        "auth": "noauth"
      },
      "port": "1080"
    },
    {
      "sniffing": {
        "enabled": true,
        "destOverride": [
          "tls",
          "http"
        ]
      },
      "listen": "127.0.0.1",
      "protocol": "http",
      "settings": {
        "timeout": 360
      },
      "port": "1087"
    }
  ],
  "outbounds": [
    {
      "mux": {
        "enabled": true,
        "concurrency": 8
      },
      "protocol": "vmess",
      "streamSettings": {
        "network": "tcp",
        "tcpSettings": {
          "header": {
            "type": "none"
          }
        },
        "security": "none"
      },
      "tag": "proxy",
      "settings": {
        "vnext": [
          {
            "address": "108.174.198.111",
            "users": [
              {
                "id": "82cad70b-5add-4898-81be-b85e63a7cbd9",
                "alterId": 0,
                "level": 1,
                "security": "auto"
              }
            ],
            "port": 8888
          }
        ]
      }
    },
    {
      "tag": "direct",
      "protocol": "freedom",
      "settings": {
        "domainStrategy": "UseIP",
        "userLevel": 0
      }
    },
    {
      "tag": "block",
      "protocol": "blackhole",
      "settings": {
        "response": {
          "type": "none"
        }
      }
    }
  ],
  "dns": {},
  "routing": {
    "settings": {
      "domainStrategy": "AsIs",
      "rules": []
    }
  },
  "transport": {}
}
