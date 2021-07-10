## Run du without traversing mounted file systems
```
for i in /*; do if ! mountpoint -q "$i"; then du -sh $i; fi; done
```

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

-----------------------------

## Reinstall missing stock CentOS repos

Find name of centos-release package for this OS version:
```
rpm -qa | grep -i centos-release
```

For example:
```
# rpm -qa | grep -i centos-release
centos-release-7-1.1503.el7.centos.2.8.x86_64
```

Now google and download corresponding rpm, for example:
```
cd /tmp
wget https://some-url/centos-release-7-1.1503.el7.centos.2.8.x86_64.rpm
```

Finally reinstall this rpm using following command:
```
rpm -ivh --replacepkgs --replacefiles <downloaded rpm>
```

-----------------------------
