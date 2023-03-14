# Three types of permissions

- User
- Group 
- Other 

Three types of access:
- Read (r)
- Write (w)
- eXecute (x)

View current ACL 

```
getfacl /accounting
```

Set ACL

`setfacl [option] [action/specification] filename`

-m  modify 
-x  remove 

```
setfacl -d -m accounting:rwx accounting 
```

# Special permission 

Special permissions are available for files and directories and provide additional privileges over the standard permission sets that have been covered.

SUID is the special permission for the user access level and always executes as the user who owns the file, no matter who is passing the command.

SGID allows a file to be executed as the group owner of the file; a file created in the directory has its group ownership set to the directory owner. This is helpful for directories used collaboratively among different members of a group because all members can access and execute new files.

The "sticky bit" is a directory-level special permission that restricts file deletion, meaning only the file owner can remove a file within the directory.

Fourth access level in addition to user, group and other.
Special permission allow for additional privileges over the standard permission sets.

## user + s(pecial)

SUID - the special permission for the user access level has a single function: A file with SUID always executes as the user who owns the file, regardless of the user passing the command. If the file owner doesn't have execute permissions, the use an uppercase S here

example 
```
ls -l /usr/bin/passwd 
-rwsr-xr-x. 1 root root 32648 Aug 10  2021 /usr/bin/passwd
```

Note the `s` where `x` would usually indicate execute permissions for the user.


## group + s(pecial)

SGID - this special permission has a couple of functions:

- If set on a file, it allows the file to be executed as the group that owns the file (similar to SUID)
- If set on a directory, any files created in the directory will have their group ownership set to that of the directory owner

This permission set is noted by a lowercase s where the x would normally indicate execute privileges for the group. It is also especially useful for directories that are often used in collaborative efforts between members of a group. Any member of the group can access any new file. This applies to the execution of files, as well. SGID is very powerful when utilized properly.

As noted previously for SUID, if the owning group does not have execute permissions, then an uppercase S is used.


## other + t(sticky)

The last special permission has been dubbed the "sticky bit." This permission does not affect individual files. However, at the directory level, it restricts file deletion. Only the owner (and root) of a file can remove the file within that directory. A common example of this is the /tmp directory:

```
ls -ld /tmp/
drwxrwxrwt. 6 root root 4096 Mar 14 14:05 /tmp/
```

The permission set is noted by the lowercase t, where the x would normally indicate the execute privilege.

# Setting special permissions

set SGID on the directory `community_content`

symbolic method
```
chmod g+s community_content/
```

numerical method, we need to pass a fourth, preceding digit in chmod command
- Start at 0
- SUID = 4
- SGID = 2
- Sticky = 1

```
chmod X### file | directory 
```
X - special permissions digit

```
chmod 2770 community_content 
```


