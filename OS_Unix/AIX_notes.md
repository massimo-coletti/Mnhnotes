# Find last logins to machine

The `last` command displays, in reverse chronological order, all previous logins and logoffs still recorded in the `/var/adm/wtmp file`. However the output does not contain the year. Instead of this you can use


```
/usr/sbin/acct/fwtmp < /var/adm/wtmp
```

to show directly the parsed contents of the `/var/adm/wtmp file`.
