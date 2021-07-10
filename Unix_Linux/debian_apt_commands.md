# Using apt commands on Debian Linux

APT (Advanced Package Tool) is a command line tool to interact with the Debian software packaging system. Packages in Debian are `.deb` files, downloaded from online repositories, which contain installable software bundles.

There are two main APT tools:

+ `apt-get` -- For installing, upgrading and cleaning packages.
+ `apt-cache` -- For finding new packages.

-----------------------------

Command `apt-get` basically works on a database (a.k.a index) of available packages. This database is downloaded and synchronized from online sources specified in file `/etc/apt/sources.list`. Without updating this database the system does not know if there are newer packages available. In fact, this is the first command you need to run in any Linux system after a fresh install.

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

To search for packages in the current package database, use `apt-cache` commands. These commands do not modify the system but rather search and generate output from the package metadata. As explained above, the metadata is acquired and updated via the `update` command of `apt-get`. Therefore it might be outdated if the last update was too long ago. In exchange `apt-cache` works offline.

To perform a text search in the package database use this command (sudo is not required)

```
apt-cache search <search term>
```

The search term need not be an exact package name. The search is performed in the package names and their short descriptions.

If you just want to search for packages whose name starts with a given prefix, use this command:

```
apt-cache pkgnames <prefix>
```

Once you know the exact package name, you can get more information about it such as version, dependencies etc by using the command below:

```
apt-cache showpkg <package_name>
```

-----------------------------

To install a specific package use this command:

```
sudo apt-get install <package_name>
```

This command has auto-completion. So if you are not sure about the exact package name, you can type a few letters, press tab and it will suggest all packages available that start with those letters.

You can install multiple packages at the same time, like this:

```
sudo apt-get install <package_1> <package_2> <package_3>
```

If you run the above commands for a package which is already installed, apt-get will look in the package database: if a newer version is found then the existing package will be upgraded.

-----------------------------

To remove an installed package use this command:

```
sudo apt-get remove <package_name>
```

Auto-completion works here as well. So you can type the first few letters of a package name, press tab, and it will suggest all installed packages starting with those letters. Note that removing a package just removes the binaries but leaves its configuration files on the system. To remove the configuration files as well use `purge`:

```
sudo apt-get purge <package_name>
```

-----------------------------

You can clean your system and free up some disk space by clearing out the local repository of retrieved package files. Use the following command:

```
sudo apt-get clean
```

An alternative way is to use `autoclean`. Like `clean`, `autoclean` clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless (e.g. a newer version exists). This allows a cache to be maintained over a long period without it growing out of control.

```
sudo apt-get autoclean
```

Another way to free up disk space is to use `autoremove`. It removes libraries and packages that were installed automatically to satisfy the dependencies of an installed package. If that package is removed, these automatically installed packages are useless in the system.

```
sudo apt-get autoremove
```

-----------------------------

To add a new repository use the `add-apt-repository` command. This will add a line with the external APT repository to `/etc/apt/sources.list` or add a file in `/etc/apt/sources.list.d/` directory. For example to add the latest vim version, run the following:

```
sudo add-apt-repository ppa:jonathonf/vim
```

Then run `sudo apt-get update` to update the local package database. Finally install it with `sudo apt install vim`
