### Add User to Groups

```
usermod -a -G group1,group2 username
```

### Rename User

https://askubuntu.com/questions/558669/renaming-user-name

```
exec sudo -i
killall -u [oldname]
id [oldname]
usermod -l [newname] [oldname]
groupmod -n [newname] [oldname]
usermod -d /home/[newname] -m [newname]
usermod -c "[full name (new)]" [newname]
id [newname]
```
