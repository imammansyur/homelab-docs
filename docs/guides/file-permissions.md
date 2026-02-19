# Permissions

## chmod

`chmod` is mainly used to change the permission of files. You can apply the permission change to a file with just `chmod [permission] [filename]` or recursively using `-R` arguments `chmod -R [permission] [directory]`.

### Add Permission to Execute

You can use `+x` to give the owner of the group permission to execute the file. On in the case you want everyone to be able to execute the file, use `a+x` instead.

```
chmod +x [filename]
```

### Read, Write, and Execute Permission

You often see the term `777` or `755` on chmod. It comes from the binary 111 that represents read (100 or 4), write (010 or 2), and execute (001 or 1) that adds up to 7 in decimal. and there are 3 entities: user (owner), group, and others. I personally hate using numbers for the non user friendly nature of it. Instead, I use this

```
chmod u=rwx,g=rwx,o=rwx [filename]
```

You can just edit only one. If I want to only edit the permission of user, it will be like this:

```
chmod u=rwx [filename]
```

## chown

`chown` is used to change the owner of the file. Similar to `chmod`, you can do it recursively using `-R` arguments. If you want to change only the user, you can do this:

```
userown [user] [filename]
```

You can also change the user and the group like this:

```
userown [user]:[group] [filename]
```

Or if you want to change only the group, you can do this:

```
userown :[group] [filename]
```
