Container combining AdGuard Home and Unbound. I don't like the fact you cannot use 127.0.0.1 as an Upstream DNS server when trying to combine these two programs as seperate containers. The only way I found was using the Docker container IP address, which to me isn't reliable enough.

Base: alpine:3.13.5 \
Unbound: 1.13.0-r3 \
AdGuardHome: 0.106.3

Use the same volumemappings as the original AdGuardHome container. In fact, you can just swap in this image and everything still works. You only have to update your Upstream DNS server to __127.0.0.1:5053__, which enables Unbound.

As with the original AdGuardHome image, this exposes the following: \
**Volumes:** \
/opt/adguardhome/work \
/opt/adguardhome/conf

For Unbound: \
/opt/unbound (Needs unbound.conf)

**Ports:**
53/tcp 53/udp 67/udp 68/udp 80/tcp 443/tcp 853/tcp 3000/tcp 5053/tcp 5053/udp
