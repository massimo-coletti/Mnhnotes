## How to disable IPv6 on CentOS / RHEL 7
Append below lines to `/etc/sysctl.conf`:
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
```
and then apply with: 
```
# sysctl -p
```

https://www.thegeekdiary.com/centos-rhel-7-how-to-disable-ipv6/
