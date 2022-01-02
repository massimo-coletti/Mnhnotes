## SUSEConnect commands

Check subscription status
```
SUSEConnect --status-text
```

Register
```
SUSEConnect -r <Registration ID> -e email --url https://scc.suse.com
```

Unregister
```
SUSEConnect --de-register
SUSEConnect --cleanup
```

## zypper commands

Add repository with no gpg check. Note the repo alias at end of command
```
zypper addrepo --no-gpgcheck https://download.opensuse.org/repositories/Java:Factory/SLE_15_SP3 pxinstjre
```

Remove repository by alias
```
zypper removerepo pxinstjre
```

Search only installed packages
```
zypper search --installed-only '*java*'
```

Install/remove without confirmation.
The --non-interactive flag applies to other zypper commands as well. 
```
zypper --non-interactive install java-1_8_0-openjdk
zypper --non-interactive remove java-1_8_0-openjdk java-1_8_0-openjdk-headless
```
