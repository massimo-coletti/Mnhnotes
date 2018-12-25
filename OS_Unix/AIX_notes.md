# Find last logins to machine

The `last` command displays, in reverse chronological order, all previous logins and logoffs still recorded in the `/var/adm/wtmp file`. However the output does not contain the year. Instead of this you can use


```
/usr/sbin/acct/fwtmp < /var/adm/wtmp
```

to show directly the parsed contents of the `/var/adm/wtmp file`.

# HMC: Hardware Management Console

Hardware Management Console (HMC) is a Physical / Virtual appliance used to manage IBM Systems. HMC supports command line (ssh) as well
as web (https) user interfaces. Using an HMC, the system administrator can manage many systems and partitions. It can also be used for monitoring and servicing a system.

https://www.ibm.com/support/knowledgecenter/TI0003N/p8hat/p8hat_partitioningwithanhmc.htm

