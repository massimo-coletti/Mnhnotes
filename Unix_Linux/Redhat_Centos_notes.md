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

## Build vim from source

**First time only:** remove existing vim, and install required dev/build packages.
```
# find existing installation and vim packages
type -a vim
whereis vim
yum list installed | grep vim
rpm -qa | grep vim

# yum remove above vim packages *except* vim-minimal which is required for other OS functionality
yum remove ...

# Install required dev/build packages
yum group install "development tools"
yum install ncurses-devel
```

Build latest vim from source (also update previously built vim)
```
cd /tmp
git clone https://github.com/vim/vim.git
cd vim
./configure --with-features=huge --enable-multibyte --enable-cscope --prefix=/usr/local
make install
cd /tmp
rm -rf /tmp/vim
```

Verify new vim version
```
type -a vim
whereis vim
vim
```

-----------------------------
