# Managing User Accounts on OpenVMS

All of the following must be done with a SYSTEM account.

-----------------------------
## Run Authorize Utility.

This is the main interface for managing user accounts.

```
SET DEFAULT SYS$SYSTEM
RUN AUTHORIZE
```

-----------------------------
## Show All Accounts

1) Run Authorize Utility

2) `UAF> show * /brief`

-----------------------------
## Add New Account

Enter a question mark (?) in any field for more information. For instance, when prompted for a unique UIC group and member number, this will list existing values.

`@SYS$EXAMPLES:ADDUSER.COM`

-----------------------------
## Modify Existing Account

First run Authorize Utility.

### Change password, expiration and lifetime

`UAF> modify <username> /password=<new-password> /nopwdexpired /nopwdlifetime`

### Add/Remove User Privileges

```
UAF> modify <username> /priv=(NO)<privilege name>
UAF> modify <username> /defpriv=(NO)<privilege name>
```

Prepend `NO` to privilege name to remove it. For example to grant `OPER` privilege to `USER1`: `modify USER1 /priv=OPER`. To revoke this privilege: `modify USER1 /priv=NOOPER`
