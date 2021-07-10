# Managing User Accounts and Groups on Unix

Create a new user:

```
useradd -d <home dir> -m -g <group name or number> -s <login shell> -c <comment> NEW_USER
```
`-m` : Create the user's home directory if it does not exist.

`-g` : Optional. If not specified, a new group will be created with same name as username.
       If specified, the group name must exist.

Example:
```
useradd -d /home/srvmnh -m -g ctm -s /bin/bash -c "awesome user" srvmnh
```

-----------------------------

Delete a user:

```
TODO
```
