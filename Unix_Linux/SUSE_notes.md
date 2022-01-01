## zypper commands

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
