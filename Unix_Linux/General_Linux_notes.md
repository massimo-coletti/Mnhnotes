## Run du without traversing mounted file systems
```
for i in /*; do if ! mountpoint -q "$i"; then du -sh $i; fi; done
```

-----------------------------

## Setup passwordless SSH

* https://www.thegeekdiary.com/centos-rhel-how-to-setup-passwordless-ssh-login/

* [Troubleshooting: Why am I still getting a password prompt with SSH with public key authentication?](https://unix.stackexchange.com/questions/36540/why-am-i-still-getting-a-password-prompt-with-ssh-with-public-key-authentication)

* https://linuxize.com/post/how-to-setup-passwordless-ssh-login/

* https://phoenixnap.com/kb/setup-passwordless-ssh

* https://help.ubuntu.com/community/SSH/OpenSSH/Keys

* https://www.thegeekdiary.com/how-to-configure-passwordless-ssh-in-solaris/

* [Solaris: How to Generate a Public/Private Key Pair for Use With SSH](https://docs.oracle.com/cd/E53394_01/html/E54793/sshuser-33.html)

-----------------------------


