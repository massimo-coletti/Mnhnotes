# AIX Notes

-----------------------------
## Install from NIM Server
```
   smitty nim_inst_latest
```
Select target client to install software. Select lpp source.
Press PF4 to select desired software, agree to licences and Enter.

-----------------------------

## Restart NIS subsystem
```
   stopsrc -g yp
   startsrc -g yp
```

-----------------------------

## Restart sshd
```
   stopsrc -s sshd
   startsrc -s sshd
```

-----------------------------

## How to Expand Filesystem

https://www.wachid.web.id/2018/05/how-to-extend-aix-file-system-df-lsvg.html

http://geekswing.com/geek/how-to-expand-a-filesystem-in-aix-df-lsvg-chfs/

-----------------------------

## Restart system logging daemon
```
   refresh -s syslogd
```

-----------------------------

## NIS client: master and slaves list
```
    # cat /var/yp/binding/<nis-domain>/ypservers
       ip-address-1
       ip-address-2
       ...
       ip-address-n
```

-----------------------------

## Find last logins to machine

The `last` command displays, in reverse chronological order, all previous logins and logoffs still recorded in the `/var/adm/wtmp file`. However the output does not contain the year. Instead of this you can use the following:


```
/usr/sbin/acct/fwtmp < /var/adm/wtmp
```

to show directly the parsed contents of the `/var/adm/wtmp file`.

-----------------------------

## HMC: Hardware Management Console

Hardware Management Console (HMC) is a Physical / Virtual appliance used to manage IBM Systems. HMC supports command line (ssh) as well
as web (https) user interfaces. Using an HMC, the system administrator can manage many systems and partitions. It can also be used for monitoring and servicing a system.

https://www.ibm.com/support/knowledgecenter/TI0003N/p8hat/p8hat_partitioningwithanhmc.htm

-----------------------------

## HMC Commands

+ List details for all LPARs of all managed systems on HMC:
```
    for s in $(lssyscfg  -r sys -F name); do
       lssyscfg -r prof -m $s -F lpar_name,desired_mem,desired_procs --header
    done
```

+ Show details of specific LPAR:
```
    lssyscfg  -r lpar -m HOU-PBLADE01-SN102D64B | grep va-hou-btk-dv01
```

+ Reboot LPAR:
```
    chsysstate -r lpar -m Server-8202-E4B-SN064A13R -o shutdown --immed --restart -n va-tlv-ctm-qa03
```

+ Turn on LPAR:
```
    chsysstate -o on -r lpar -n va-tlv-ctm-pt01 -m Server-7895-43X-SN210110C
```

+ List memory resources of managed system:
```
    lshwres -r mem -m Server-8202-E4B-SN06EB53P --level sys
```

+ List CPU resources of managed system:
```
    lshwres -r proc -m Server-8202-E4B-SN06EB53P --level sys
```

-----------------------------

## Command on vio to get into shell
```
  oem_setup_env
```
