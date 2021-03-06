
# to install

```
go get github.com/xtaci/kcptun/client
go get github.com/xtaci/kcptun/server
```

- instructions: https://github.com/xtaci/kcptun/blob/master/README.en.md
    - lots of params to play with

## on example server

```
cd /optvar/go/bin
server -t "localhost:9900"  -l ":4000" -mode fast2 --key '7454' --parityshard 2
ufw allow 4000/udp
```

## on example client
```
client -r 94.23.38.89:4000 -l ":9900" -mode fast2 --key '7454' --parityshard 2
```

- 94.23.38.89 is the server addr where the proxy is hosted
- 4000 is the udp port on the server (make sure no firewall is blocking it)

# example with polipo proxy on server

```
apt install polipo
mkdir -p /etc/polipo
curl https://raw.githubusercontent.com/despiegk/tips/master/polipo > /etc/polipo/config
cd /etc/polipo
polipo -c config
```

- on port 9900
- now configure web proxy as localhost:9900

# to test performance

- fast.com
- http://www.speedtest.net/nl/

# to also use client side proxy

#will go to master polipo server over the udp tunnel
```
mkdir -p /tmp/polipo_cache
curl https://raw.githubusercontent.com/despiegk/tips/master/polipo_client > ~/.config/polipo
polipo -c ~/.config/polipo
```

to see webinterface: http://localhost:8123/polipo/
http://localhost:8123/polipo/status?
