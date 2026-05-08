# Absolute Path vs Relative Path

## Relative Path

Relative path is the path according to your current location. Let's say you're in your own user home directory and there are multiple directories. You can `cd` the directory name right away without the leading `/`.

``` sh
user:~$ pwd
/home/user
user:~$ ls
Documents
Downloads
user:~$ cd Downloads #Notice there's no leading slash '/' on the path
user:~/Downloads$
```

## Absolute Path

Absolute path is when the path started with root or `/`. For example, the system log is located at `/var/log`. And you can show the contents inside that directory with the following command.

``` sh
ls /var/log #Notice the leading slash `/` before the path
```

## When to use absolute path

With the absolute path, you can do anything with any files or directories provided you're giving the full path. You can do something in `/mnt` or `/opt` while your current working directory is in you own user home directory.

Let's say you're in your own user home directory. You typed in `pwd` to show your current directory and its `/home/user/`. And when you want to, let's say, list what's in the `/var/log/`, you don't have to `cd` to the location and then `ls`. Or worse, you went to root `/` first by `cd ..` until you get to root, and then `cd var/log`.

``` sh
user:~$ pwd
/home/user
user:/home$ cd ..
user:/home$ pwd
/home
user:/home$ cd ..
user:/$ pwd
/
user:/$ cd var
user:/var$ pwd
/var
user:/var$ cd log
user:/var/log$ pwd
/var/log
```

I know this is hyperbolic and unpractical, but we've been there at some point (at least I have). The ability to be able to do something outside my current working directory makes me think on the system-wide perspective.

## When to use relative path

Even when absolute path is powerful, its often a nuisance when you have to type a long path back-to-back. My rule of thumb is to `cd` to the directory that I'm gonna work on, using absolute path if needed. And then use relative path to work with the files or directory that I needed.

Other use case to use relative path is when I'm about to delete or do something with high risk command on a certain file/directory. Using absolute path is very risky, you can mistype or accidentally pressed enter before typing the full path, resulting in the unintentional deletion of files and directories.

Relative path helps in that case because you can be sure you're in the right place and have the right files/directories to delete. You can `cd` to the intended working directory first and then start deleting (or other high risk command) using relative path to the intended files/directories. If there was any damage done, the damage will be limited to the working directory.
