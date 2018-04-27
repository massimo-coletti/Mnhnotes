# Using apt commands on Linux

There are two main tools around `apt`: `apt-get` and `apt-cache`. `apt-get` is for installing, upgrading and cleaning packages while `apt-cache` is used for finding new packages.

-----------------------------

Command `apt-get` basically works on a database of available packages. Without updating this database the system does not know if there are newer packages available. In fact, this is the first command you need to run in any Linux system after a fresh install.

```
sudo apt-get update
```

When you run this command, you’ll see information being retrieved from various servers.

There are three types of lines: `Hit`, `Get` and `Ign`.

+ `Hit`: There is no change in package version
+ `Ign`: The package is being ignored. There could be various reasons for this.
+ `Get`: There is a new version available. It will download information about the new package, not the package itself.

-----------------------------

Once you have updated the package database with the above command, you are ready to actually upgrade the installed packages themselves. The most convenient way is to upgrade all packages that have updates available, using the command below:

```
sudo apt-get upgrade
```

To upgrade only a specific package, use this command:

```
sudo apt-get upgrade <package_name>
```

-----------------------------

