# Managing User Accounts and Groups on Unix

Create a new user:

```
useradd -d <home dir> -m -g <group name or number> -s <login shell> NEW_USER
```
`-m` : Create the user's home directory if it does not exist.

Example: 
```
useradd -d /home/srvmnh -m -g ctm -s /usr/bin/tcsh srvmnh
```

-----------------------------
