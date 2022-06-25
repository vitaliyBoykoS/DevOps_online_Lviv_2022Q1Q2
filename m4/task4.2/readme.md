/etc/passwd file stores essential information required during login
It have userId, groupId, home directory, shell and etc.

From the above image:
    Username
    Password
    User ID (UID)
    Group ID (GID)
    Home directory
    Command/shell


 /etc/group is a text file which defines the groups to which users belong under Linux and UNIX operating system. It have three clases grop, user,others
File has group_name, password, Gid, group list. 

Systemd defines a number of special UID range:
    60001-60513: UIDs for home directories managed by systemd-homed
    61184-65519 (0xef00-0xffef): UIDs for dynamic users

UID - user identifier or user ID. Its number for identify user or groups(GID)

The POSIX standard introduced three different UID fields into the process descriptor table, to allow privileged processes to take on different roles dynamically: Effective user ID,Saved user ID,Real user ID

GID its like UID but for groups.
Open terminal
Type the command su to become the root user
Type the command id -u to find the UID for a particular user.
Type the command id -g to find the primary GID for a particular user
Type the command id -G to list all the GIDs for a particular user
Type the command exit to close the root user session.

Enter the following command in order to see which group the current user belongs to:

1.groups

This command lists all the groups that you belong to.

Enter the following command to check which group a certain user belongs to:

2.groups username

You can also use the following command to list the group members along with their GIDs.

3.id username

For add user using command useradd [] Username.
When you create you must get username, password, permissions

First get user identity using the id command:
id tom

Next use the grep command to grab login info about user named tom from the /etc/passwd file
grep '^tom:' /etc/passwd

See group info about user named tom using the groups command:
grep 'tom' /etc/group
groups tom

Find home directory permissions for user named tom, run the following ls command:
ls -ld /home/tom/

Finally, see all Linux process owned by user and group named tom using the ps command:
ps aux | grep tom
ps -u tom

The /etc/skel directory contains files and directories that are automatically copied over to a new user’s home directory when such a user is created by the useradd program. skel is derived from the “skeleton”.
Structure:
permisions 
owners
date
time

You can use comand userdel

Tou can use same diferend command
 For lock
Use the command “passwd -l username”.
Use the command “usermod -l username”.

Unlock
Use the command “passwd -u username”.
Use the command “usermod -U username”.

Delete the password for your user by running this command:

sudo passwd -d username

In columns we see permissions, date, time,  bytes, owners, name, uid, gid

In linux has a three  access rights exist read, writes and execute. And tree groups its owner, group and all. And we can take permission for owner, group and all separate.

It means:

    user linuxsir is owner and can read and write on test.txt
    group root can only read
    Anyone else can only read

It doesn't say that group rootis owner of the file, it is only saying which permissions group roothas over the file.

By default, the owner of a file is the user who created it and the group assigned to a file is the primary group of the user. However, you can change the group of a file using chgrp.

 If you want change permissions use chmode
For change owner use chown

There are three digits in a chmod permission. The first digit represents the permissions of the user, the second represents the group, and the third represents global permissions. So if a file has permissions 754, the user can read, write, and execute; the group can read and execute, while all other users can only read.

Umask, or the user file-creation mode, is a Linux command that is used to assign the default file permission sets for newly created folders and files. The term mask references the grouping of the permission bits, each of which defines how its corresponding permission is set for newly created files. The bits in the mask may be changed by invoking the umask command.

Setuid, setgid, and the sticky bit can be tough for new and aspiring Linux admins to understand. It's easy enough to do a web search for the basic definitions:

    setuid: a bit that makes an executable run with the privileges of the owner of the file
    setgid: a bit that makes an executable run with the privileges of the group of the file
    sticky bit: a bit set on directories that allows only the owner or root can delete files and subdirectories

Use the following command to run the script:
bash main.sh

The built-in bash source command reads and executes the content of a file. If the sourced file is a bash script, the overall effect comes down to running it. We may use this command either in a terminal or inside a bash script.

To obtain documentation concerning this command, we should type help source in the terminal. We assume that Bash (Bourne again shell) is not in POSIX mode is through the whole tutorial.
