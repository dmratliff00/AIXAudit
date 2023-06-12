# AIXAudit
These are commands to help assist with retrieving the server version, password settings, and users with administrative access to the server. The commands are designed to only read data and will not modify or create data in the server.

## Server Version
This will show the version of the AIX server.

``` Bash
oslevel -s > version.txt
```

## Password Settings
This will show the password settings of user accounts on the AIX server.

``` Bash
/etc/passwd > PasswordSettings.txt
```

If the above command doesn't work, try one of the following.

``` Bash
sudo passwd --status --all > PasswordSettings.txt
```
``` Bash
sudo passwd -S -a > PasswordSettings.txt
```

## Extended User Attributes
The /etc/security/user file contains extended user attributes. This is an ASCII file that contains attribute stanzas for users. If an attribute is not defined for a user, the default value for the attribute is used.

``` Bash
/etc/security/user > SecurityUser.txt
```

## Users
This will show the user accounts on the AIX server.

``` Bash
lsuser -C -a id login admin account_locked default_roles groups pgrp roles shell su sugroups admgroups gecos auth1 auth2  dictionlist expires histexpire histsize loginretries maxage minage minlen pwdchecks rlogin ALL > Users.txt
```

## Login Shells
This will show the valid login shells on the AIX server.

``` Bash
sudo cat/etc/shells > LoginShells.txt
```

## Groups
This will show the user groups on the AIX server.

``` Bash
lsgroup -C -a adms admin id users ALL > Groups.txt
```

## Sudo
This is to determine what groups/accounts can run commands as root.

``` Bash
sudo cat /etc/sudoers > Sudo.txt
```
