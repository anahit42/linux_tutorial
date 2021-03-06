# Table of Contents
  1. [History](#history)
      1. [GNU/Linux Philosophy](#history--philosophy)
      1. [GNU/Linux Distributions](#history--distributions)
  1. [Commands](#commands)
      1. [Man pages](#commands--man)
      1. [Directories](#commands--directories)
      1. [Files](#commands--files)
      1. [File contents](#commands--filecontents)
      1. [File tree](#commands--filetree)
  1. [Users](#users)
     1. [Intro](#users--intro)
     1. [Groups](#users--groups)
  1. [Permissions](#permissions)
     1. [File ownership](#permissions--fileownership)
     1. [List of special files](#permissions--specialfiles)
     1. [Permissions](#permissions--permissions)
  1. [Other](#other)
     1. [Runlevels](#other--runlevels)
     1. [Process Management](#other--processmanagement)
     1. [SSH](#other--ssh)
     1. [Useful commands](#other--commands)

## History

<a name="history--philosophy"></a>
> Based on years of conversations, I am convinced that part of the cause of the problem is the tendency to call the system Linux rather than GNU, and describe it as open source rather than free software.
> -- Richard Stallman

What is GNU? GNU is a recursive acronym for "GNU's Not Unix!"

The GNU is a system that is used every day by many people all of the world. Although many users refer to it by name "Linux" without knowing that it is GNU system that they actually use.

Linux is just a part of this system. It is a kernel:
the program in the system that allocates the machine's resources to the other programs that user runs.

So instead of sounding smart and showing off let's be really smart and know things in their right ways.

You can read about GNU project following these links:

[The GNU Manifesto](https://www.gnu.org/gnu/manifesto.html)

[What is free software?](https://www.gnu.org/philosophy/free-sw.html)

[Philosophy](https://www.gnu.org/philosophy/philosophy.html)

- `Do one thing and do it well`
- `Release early, release often `
- `Free as in Freedom (the GNU philosophy)`

<a name="history--distributions"></a>
#### GNU/Linux Distributions

  A GNU/Linux distribution is an operating system made from a software collection, which is based upon the Linux kernel and, often, a package management system.
      Widely used distributions are:

  **Debian**
  - `Ubuntu, a desktop and server distribution derived from Debian`
  - `Linux Mint Debian Edition`
  - `Linux Mint, a distribution based on and compatible with Ubuntu`

  **Fedora**
  - `Red Hat Enterprise Linux (RHEL)`
  - `CentOS, a distribution derived from the same sources used by Red Hat`

  **Arch Linux**
  - `Manjaro Linux`

  **Gentoo**
  - `Chrome OS, Google's commercial operating system`

You may find and use other distributions.
Each one will have its installation guide, just follow the steps and you'll be fine.
You don't need to be a hacker to install an Ubuntu on your machine.
Though consider which distribution suits your needs best.

##### Which one to choose ?

Distribution name | Reason(s) for using
------------ | -------------
Red Hat Enterprise (RHEL) | You are a manager and you want a good support contract.
CentOS| You want Red Hat without the support contract from Red Hat.
Fedora | You want Red Hat on your laptop/desktop.
Linux Mint | You want a personal graphical desktop to play movies, music and games.
Debian | Good for servers, laptops, and any other device.
Ubuntu | Good for new users. Has a new release each 6 months.
Kali | Designed for digital forensics and penetration testing. Good for hacking (they say).
others | Advanced users may prefer Arch, Gentoo, OpenSUSE, Scientific, etc.

![distros](./images/distros.jpg)

Some useful links:

- [distrowatch](https://distrowatch.com/)
- [Red Hat](https://www.redhat.com/en)
- [Debian](https://www.debian.org/)
- [Linux Mint](https://www.linuxmint.com/)
- [Ubuntu](https://www.ubuntu.com/)
- [Gentoo](https://www.gentoo.org/)

**[⬆ back to top](#table-of-contents)**

## Commands

<a name="commands--man"></a>
#### Man pages
Have you ever came across RTFM? It's an initialism for the expression "read the fucking manual".
Everything (well, almost) could be found in manuals. But you may use search engines too.

Type `man $command_name` to get information about the command. Let's get information about `man` command itself.

```bash
man man
```

Go ahead and read more about `man` command in your terminal.

By the way, the second thing I tried with man command was:

``` man woman ```

And I got "No manual entry for woman". Well, I guess manual pages too can't have answers sometimes.

<a name="commands--directories"></a>
#### Directories

##### pwd

This command displays your current directory. Open a command line (terminal) and type `pwd` there.


##### cd

This command allows you to change your current directory.

```bash
cd /home/user/directory_name
```

Type `cd` without a target directory or as `cd ~` and you'll be in your home directory.

Type `cd ..` to go to the directory above your current directory(i.e. parent directory).

Type `cd -` to go to the previous directory.


##### absolute and relative paths

You should be aware of absolute and relative paths in the file tree.

When you type a path starting with a slash (/), then the root of the file tree is assumed.

If you don't start your path with a slash, then the current directory is assumed as the starting point.

For example if I'm in my `home` directory and I want to navigate to the `marvin` directory there, I need to type either

```bash
cd /home/marvin
```

or

```bash
cd marvin
```

##### path  completion

Use the tab key to type paths without errors as it completes paths. It will also save your time.

##### ls

This command lists the contents of a directory you are in.

Type `ls -a` to see all files, including the hidden files.
When a file name starts with a dot, it is considered a hidden file and it doesn't show up in regular file listings.

##### mkdir

This command let's you create directories.
You have to give the name of the new directory to be created.

```bash
mkdir mydir
```

This will create directory in your current directory.
Give absolute path to create anywhere else.

```bash
mkdir /home/user/some_dir_name/mydir
```

Type `mkdir -p dir_name/sub_dir_name` to create both dir_name and sub_dir_name directories if dir_name does not exist yet.

##### rmdir

This command let's you remove a directory.

Type `rmdir -p` to remove directories recursively.


##### Practice

1. Display your current directory.
2. Change to the `/etc` directory.
3. Now change to your user directory (this could have different name for each of you) in home directory.
4. Go to the parent directory of the current directory.
5. List the contents of the current directory.
6. List all the files (including hidden files) in your `/etc` directory.
7. Create a directory `test_dir` in your home directory.
8. Change to the `/etc` directory, stay here and create a directory `new_dir` in your home
directory.
9. Create in one command the directories `~/dir1/dir2/dir3` (dir3 is a subdirectory from dir2,
10. Remove the directory `test_dir`.
11. Remove the directories `dir1`, `dir2`, `dir3` with one command.
12. Read about `lsof` command for the next session.


<a name="commands--files"></a>
#### Files

Some key points to remember about files:
- They are case sensitive. This means that test1 is different from Test1

- Everything  is  a  file. Directories too, they are special kind of files but still are fils.
Each console window, any hard disk or partition and any process are all represented somewhere in the file system as a file.

- File extensions are not used to determine the file type. Use file command to determine the file type.

```bash
file /home
```

will output as `/home: directory`


##### touch
To create an empty file we can use `touch` command.

##### rm

This command is used to remove a file.
This command removes a file permanently. Be careful when using this command.

The `rm -rf` command will erase anything, if you have proper permission.
Be very careful with `rm -rf` when you are logged in as a root user.
You can mess up everything and regret about what you have done.

##### cp

This commands let's you copy a file. Pass source and a target arguments to it.

```bash
cp original_file original_file.copy
```

If the target argument is a directory, then the original file is copied to that directory.

Type `cp -r` to copy complete directories. The `-r` option is used with some commands to do the task recursively,


##### mv

This command let's you rename a file or move the file to another directory.
It also can be used to rename directories, as directories are also files.


##### lsof

This command lists open files.

Open files in the system include disk files, named pipes, network sockets and devices opened by all processes.

This command can be used to list processes working on some port or vise versa.

To view the port associated with a daemon

```bash
lsof -i -n -P | grep firefox
```


To view which processes use port `443`

```bash
lsof -i :443
```


##### Practice

1. List the files in the /bin directory
2. Display the type of file of `/bin/cat`, `/etc/passwd and`, `/usr/bin/passwd`
3. Create a directory `~/touched` and enter it
4. Create the files today.txt and yesterday.txt in touched
5. Change the date on yesterday.txt to match yesterday's date
6. Copy yesterday.txt to copy.yesterday.txt
7. Rename copy.yesterday.txt to groundhogs_day.txt
8. Create a directory called `~/testbackup` and copy all files from `~/touched` into it
9. Use one command to remove the directory  `~/testbackup` and all files into it

<a name="commands--filecontents"></a>
#### File contents

##### head

You can use `head` to display the first 10 lines of a file.

```bash
head /etc/passwd
```

It can also display the first n lines of a file.


```bash
head -20 /etc/passwd
```

##### tail

The `tail` command will display the last 10 lines of a file.


```bash
tail /etc/passwd
```

It can also display the first n lines of a file.

```bash
tail -20 /etc/passwd
```

##### cat

The `cat` command copies standard input to standard output.

You can use cat to display a file on the screen.
If the file is longer than the screen, it will scroll to the end.


```bash
cat /proc/partitions
```

This will display all partitions.
For example you want to get partition name for USB drive you inserted to format it. You can use this command.

You may use `cat` to create text files.
Type the `cat > file_name.txt` command and then type some lines.
After the last line, hold the Control (Ctrl) key and press d.


`cat` also can be used to copy files:


```bash
cat js.txt
```

type some text, like

```javascript
let life = 21;
let universe = 21;
let answer = life + universe;
```

then you can copy the content fo js.txt to node_js.txt

```bash
cat js.txt > node_js.txt
```


##### tac
If the output of `cat js.txt` is:

```javascript
let life = 21;
let universe = 21;
let answer = life + universe;
```

then the output of `tac js.txt` will be:

```javascript
let answer = life + universe;
let universe = 21;
let life = 21;
```

Just one example will show you the purpose of tac (cat backwards).

##### more and less
The `more` command is used to display files that take up more than one screen showing the content page by page.
For going to the next page use the space bar and q to quit.

`less` command is similar to more, but has the extended capability.
It allows both forward and backward navigation through the file.

##### strings

This command let's you display readable ascii strings found in (binary) files.

Try out `cat /bin/ls` vs `strings /bin/ls/`.

##### Practice

1. Display the first 12 lines of /etc/services
2. Display the last line of /etc/passwd
3. Use cat to create a file named count.txt that looks like this:
    ```txt
    One
    Two
    Three
    Four
    Five
    ```
4. Use cp to make a backup of this file to `cnt.txt`
5. Use cat to make a backup of this file to `catcnt.txt`
6. Display `catcnt.txt`, but with all lines in reverse order
7. Use more to display `/etc/services`
8. Display the readable character strings from the `/usr/bin/passwd` command
9. Read about `echo` and write 'this is the first line' to `tailing.txt` file with it
10. Use cat to create a file named tailing.txt that contains the contents of `tailing.txt` followed
by the contents of `/etc/passwd` (does not overwrite it)


<a name="commands--filetree"></a>
#### File tree

##### the root directory  /

All GNU/Linux systems have a directory structure that starts at the root directory.
The root directory is represented by a forward slash, like this: /.
Everything that exists on your system can be found below this root directory.

```bash
ls /
```

See the content of the root directory.

##### /bin

Binaries are files that contain compiled source code (or machine code).
Binaries can be executed on the computer.
Sometimes binaries are called executables.


The /bin directory contains binaries for use by all users. Let us `ls` its content.

```bash
ls /bin
```

##### /lib

Binaries found in `/bin` and `/sbin` often use shared libraries located in `/lib`.

##### /opt

The purpose of `/opt` is to store optional software.
In many cases this is software from outside the distribution repository.
You may find an empty `/opt` directory on many systems.
A large package can install all its files in `/bin`, `/lib`, `/etc` subdirectories within `/opt/`
$packagename/.

If for example the package is called android_studio, then it installs in `/opt/android_studio`, putting
binaries in `/opt/android_studio/bin` and man-pages in `/opt/android_studio/man`.

##### /boot
The /boot directory contains all files needed to boot the computer.
On GNU/Linux systems you typically find the `/boot/grub` directory here.
`/boot/grub` contains `/boot/grub/grub.cfg` or `/boot/grub/grub.conf` which
defines the boot menu that is displayed before the kernel starts.

##### /etc
All of the machine-specific configuration files should be located in `/etc`.
Many times the name of a configuration files is the same as the application,
daemon, or protocol with `.conf` added as the extension.

```bash
ls /etc/*.conf
```


**/etc/hosts**

Before the advent of a distributed domain name system
networked computers used local files to map hostnames to IP addresses.

```bash
cat /etc/hosts
```

127.0.0.1   localhost

127.0.1.1   user

and some other addresses that you may have added.

##### /media

`/media` directory serves as a mount point for removable media devices such as CD-
ROM's, digital cameras, and various usb-attached devices

##### /tmp

Applications and users should use /tmp to store temporary data when needed.
Data stored in `/tmp` may use either disk space or RAM.
Both of which are managed by the operating system.
Never use `/tmp` to store data that is important or which you wish to archive.

##### /dev
The `/dev` directory is populated with files as the kernel is recognising hardware.

##### /usr  Unix  System  Resources

The `/usr` hierarchy should contain shareable, read only data.

The `/usr/bin` directory contains a lot of commands.

The `/usr/lib` directory contains libraries that are not directly executed by users or scripts.

The `/usr/local` directory can be used by an administrator to install software locally.

The `/usr/src` directory is the recommended location for kernel source files.

##### /var variable data

Files that are unpredictable in size, such as log, cache and spool files, should be located in
`/var`.

The `/var/log` directory serves as a central point to contain all log files.

The `/var/cache` directory can contain cache data for several applications.
     
**[⬆ back to top](#table-of-contents)**


##### Practice

1. Does the file `/bin/cat` exist ? What type is it?
2. Use cat to display /etc/hosts and /etc/resolv.conf.
What is your idea about the purpose of these files ?
3. Display `/proc/cpuinfo`. On what architecture is your Linux running ?
4. Can you enter the `/root` directory ? Are there (hidden) files ?
5. Are ifconfig, fdisk, parted, shutdown and grub-install present in `/sbin`?
Read about `/sbin`. Why are these binaries in `/sbin` and not in `/bin` ?
6. Is `/var/log` a file or a directory ? What about `/var/spool`?
7. Read the man page of random and explain the difference between `/dev/random` and /
`dev/urandom`.

## Users

<a name="users--intro"></a>
#### Intro

##### whoami

The `whoami` command tells you your username.

##### who

The `who` command will give you information about who is logged on the system.

##### w

The `w` command shows you who is logged on and what they are doing.

##### id

The `id` command will give you your user id, primary group id, and a list of the groups that you belong to.

##### su to another user

The  su command allows a user to run a shell as another user.
You can also su to become root, when you know the root password.

```bash
su root
```

##### user management

If you are a novice user, you may use the graphical tools provided by your distribution to manage users.
But you won't learn if you use graphical tool always.


The local user database on GNU/Linux is `/etc/passwd`. We were getting its content many times. Let's do once again.

```bash
tail /etc/passwd
```

The output contains 7 columns.
These columns are:
username, an x, the user id, the primary group id, a description, the name of the home
directory, and the login shell.

On GNU/Linux system the most powerful account is the root user. Let's see in `/etc/passwd`

```bash
sfast@sfast:~$ head -1 /etc/passwd
root:x:0:0:root:/root:/bin/bash
```
The root user has userid 0.


Add user with `useradd` command.
Let's add `marvin` user with the following arguments:

force the creation of the home directory (-m)
set the name of the home directory (-d)
set a description (-c)

```bash
useradd -m -d /home/marvin -c "marvin paranoid android" marvin
tail -1 /etc/passwd
```

We will see tail result

```
marvin:x:1001:1001:marvin paranoid android:/home/marvin:
```

You can delete the user `marvin` with `userde`l. The `-r` option of `userdel` will also remove the
home directory.

User password is set with the `passwd` command. You will need to provide
old password before twice entering the new one.

Passwords are encrypted and kept in `/etc/shadow`. The `/etc/shadow` is read only file and only by root.


<a name="users--groups"></a>
#### Groups
Users can be listed in groups.
Instead of setting permissions for each user, groups allow to set permissions on the group level.

Groups can be created with the `groupadd command`.
The example below shows the creation of a group.

```bash
groupadd nerds
```

Users can be a member of several groups.
Group membership is defined by the `/etc/group` file.

Let's `cat` its content.

Group membership can be modified with the `useradd` or `usermod` command.

Be careful when using `usermod` to add users to groups.
It will will remove the user from every group of which he is a member
if the group is not listed in the command/

Using append option `-a` prevents this.

```bash
usermod -a -G nerds marvin
```

Modify group name with the `groupmod` command.

```bash
groupmod -n new_name old_name
```

To remove a group permanently use `groupdel` command.

You can give control of managing group membership to another user with the `gpasswd` command.

```bash
gpasswd -A user_name group_name
```


##### Practice

1. Create the groups `react`, `node` and `other`
2. Create new user called `intern`
3. In one command, make `intern` a member of `react` and `node`
4. Rename the `other` group to `phaser`
6. Make someone responsible for managing group membership of `react` and `phaser`. Test that
it works.

**[⬆ back to top](#table-of-contents)**

## Permissions

<a name="permissions--fileownership"></a>
##### File ownership

Let us `cd` to a folder where we could find some files.

I'll choose `Downloads` where there is a file called `hitchhikers_guide_to_the_galaxy`.

I want to see whom does this file belong to.

```bash
ls -l hitchhikers_guide_to_the_galaxy
```

The output is `-rw-rw-r-- 1 sfast sfast 8364061 Հնվ 15 12:10 hitchhikers_guide_to_the_galaxy`.

So this file belongs to user `sfast` who is in the group that has the same name.

We can change the group owner of a file using the `chgrp` command.

```bash
chgrp books hitchhikers_guide_to_the_galaxy
```
I changed the group owner of a file to be `books`.

The user owner of a file can be changed with `chown` command.

```bash
chown ford hitchhikers_guide_to_the_galaxy
```

You can also use `chown` to change both the user owner and the group owner.

```bash
chown marvin:group42 hitchhikers_guide_to_the_galaxy
```

<a name="permissions--specialfiles"></a>
##### List of special files

When using `ls -l` the output includes 10 characters before the user and group owner.

This table describes the function of all 10 characters.

character position | function
------------ | -------------
1 | file type
2-4 | permissions for the user owner
5-7 | permissions for the group owner
8-10| permissions for others


The user owner permissions apply to you when you are the user owner of a file.

The group owner permissions apply to you when you are the group owner of a file.

The others permissions apply to you when you are not the user owner of a file and
you do not belong to the group owner.

As we said the first character tells us the type of file and it can be one from the following list:

Character | File type
------------ | -------------
\- | regular file
d | directory
l | symbolic link
p | named pipe
b | block device
c | character device
s | socket


<a name="permissions--permissions"></a>
##### Permissions

The 9 characters following the first one, i.e. the file type, show the permissions of the file.

Permission types are:

permission | for a file | for a directory
------------ | ------------- | -------------
r (read) | read file contents (`cat`)  | read directory contents (`ls`)
w (write) | change file contents (`vi`) | create files in (`touch`)
x (execute) | execute the file | enter the directory (`cd`)


Permissions can be changed with `chmod`. The first example gives the user owner execute
permissions.

```bash
ls -l example.txt
```

Outputs `-rw-r--r-- 1 sfast sfast 0 2018-01-01 22:34 example.txt`.


This command gives the user owner execute permissions.

```bash
chmod u+x example.txt
```

This command removes the others read permission.

```bash
chmod o-r example.txt
```

You may come across the octal permissions when you work with or read about permission.
It is old school way of setting permissions :)

Calculate permission digits by adding numbers below

number | permission
------------ | -------------
4 | read (r)
2 | write (w)
1 | execute (x)

Octal permissions table:

binary | octal | permission
------------ | ------------- | -------------
000 | 0 | \---
001 | 1 | \--x
010 | 2 | \-w-
011 | 3 | \-wx
100 | 4 | r--
101 | 5 | r-x
110 | 6 | rw-
111 | 7 | rwx

Let's transform for example `rwxrwxrwx` to octal.

`rwxrwxrwx` contains 3 `rwx`, one for each: user owner, group owner, other.

If we represent each `rwx` with `7` we will get `777`, which is equal to `rwxrwxrwx`.

The chmod command accepts these numbers.

```bash
chmod 777 example.txt
```

Please note that setting `777` is a bad idea in most cases.

##### Practice

1. Create a directory `~/permissions`. Create a file owned by yourself in there.
2. Copy a file owned by `root` from `/etc/` to your `permissions` directory, who owns this file now ?
3. As root, create a file in the users `~/permissions` directory.
4. As normal user, look at who owns this file created by root.
5. Change the ownership of all files in ~/permissions to yourself.
6. Make sure you have all rights to these files, and others can only read.
7. With chmod, is `770` the same as `rwxrwx---` ?
8. With chmod, is `664` the same as `r-xr-xr--` ?
9. With chmod, is `400 `the same as `r--------` ?
10. With chmod, is `734` the same as `rwxr-xr--` ?
11. Create a file as `root`, give only read to others. Can a normal user read this file? Test
writing to this file.
12. Create a file as normal user, give only read to others. Can another normal user read this
file? Test writing to this file.
13. Can `root` read this file? Can `root` write to this file?
14. Create a directory that belongs to a group, where every member of that group can read
and write to files, and create files. Make sure that people can only delete their own files.


**[⬆ back to top](#table-of-contents)**

## Other

<a name="other--runlevels"></a>
##### Runlevels
A `runlevel` is one of the modes that a Unix-based operating system will run in.
Each `runlevel` has a certain number of services stopped or started.
Seven `runlevels` exist, numbered from `0` to `6`.


run level | mode| action
------------ | ------------- | -------------
0 | halt | shuts down system
1 |	single-user mode | does not configure network interfaces, start daemons, or allow non-root logins
2 | multi-user mode	| does not configure network interfaces or start daemons
3 | multi-user mode with networking	| starts the system normally
4 | undefined | not used/user-definable
5 | X11 | as run level 3 + display manager(X)
6 | reboot | reboots the system

By default GNU/Linux system boots either to runlevel `3` or to runlevel `5`.

The first one permits the system to run all services except for a GUI.
The second one allows all services including a GUI.

Booting into a different runlevel can help solve certain problems.

For example, if a machine will not boot due to a damaged configuration file or will not allow logging in
because of a corrupted `/etc/passwd` file or because of a forgotten password, the problem can solved by first
booting into single-user mode (i.e. runlevel 1).


<a name="other--processmanagement"></a>
##### Process management

`ps` – displays your currently active processes.

`top` – displays all running processes

`kill pid` – kills process id pid

`pkill name` – kills process with name `name`

`killall name` – kills all processes with names beginning `name`

`bg` – lists stopped or background jobs; resume a stopped job in the background

`fg` – brings the most recent job to foreground

`fg n` – brings job n to the foreground

<a name="other--ssh"></a>
##### SSH
All modern Unix-like systems include a command-line ssh client.
To login to your computer from a Unix-like machine, go to a command-line and type:

```bash
ssh <username>@<computer name or IP address>
```

You should get the usual password prompt. You can set ssh key
if you want to authenticate using keys instead of passwords.

[Setting SSH key](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

<a name="other--commands"></a>
##### Useful commands

`grep pattern files` – search for `pattern` in `files`

`grep -r pattern dir` – search recursively for `pattern` in `dir`

`grep -i` – case insensitive search

`grep -r` – recursive search

`grep -v` – inverted search

`grep -o` – show matched part of file only

`locate file` – find all instances of file


`exit` – log out of current session

`Ctrl+C` – halts the current command

`Ctrl+D` – log out of current session, similar to exit

`Ctrl+W` – erases one word in the current line

`Ctrl+U` – erases the whole line

`Ctrl+R` – type to bring up a recent command

`!!` – repeats the last command

`!abc` – Run last command starting with abc



**[⬆ back to top](#table-of-contents)**
