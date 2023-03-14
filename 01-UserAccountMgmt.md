# Create user accounts

`useradd` 

`-c` comment 

```
sudo useradd -c "Test User" testuser
sudo useradd -c "Ashish Singh Baghel" ashish
```

Change Password 

```
sudo passwd ashish
```

Check status of a user account 
```
sudo passwd -S ashish
ashish PS 2023-03-14 0 99999 7 -1 (Password set, SHA512 crypt.)
```

PS - password for user is set 
LK - account is locked

Expire a password 

```
sudo passwd -e ashish 
```

```
sudo passwd -S ashish 
ashish PS 1970-01-01 0 99999 7 -1 (Password set, SHA512 crypt.)
```

You can see that the password now has the last changed time of 1970-01-01. If you know any Linux or UNIX history, you'll recognize that the beginning of the computing world was 1970-01-01, so setting the last changed time to outside of the epoch time expires the password. 

Once a password has expired, either by policy or by manually expiring it, you can't unexpire it. The system will prompt the user to change passwords upon their next login.

You also can't unlock an account that has no password set. If you create a new user account and don't set the password, the account is locked. To unlock it, you have to set a password.

Lock a user's account 

```
sudo passwd -l ashish
```

Unlock account 

```
sudo passwd -u ashish
```

`-n` minimum password lifetime
`-x` maximum password lifetime
`-w` warning before expiration 
`-i` inactive to disabled in days

```
sudo passwd -n 1 -x 90 -w 3 -i 10 ashish
```

It's good to set the `-n` to at least one day because this prevents a user from repetitively changing their passwords.

Remove User Accounts

```
sudo userdel -r ashish
```
