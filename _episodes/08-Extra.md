---
title: "Extra - Useful things to know"
teaching: 15
exercises: 5
questions:
- "What other useful things should I know?"
objectives:
- "TO DO."
- "TO DO."
keypoints:
- "TO DO"
- "TO DO"
keypoints:
- "Use ls -l to view the permissions for a specific file."
- "Use chmod to change permissions on a file or directory."
- "TO DO."
---
### Permissions
Unix controls who can read, modify, and run files using concepts of *file ownership* and *permissions* to provide security at the file system level.


Users can belong to any number of groups, each of which has a unique group name and numeric group ID. The list of who’s in what group is usually stored in the file /etc/group. (If you’re in front of a Unix machine right now, try running cat /etc/group to look at that file.)

Now let’s look at files and directories. Every file and directory on a Unix computer belongs to one owner and one group. Along with each file’s content, the operating system stores the numeric IDs of the user and group that own it.

The user-and-group model means that for each file every user on the system falls into one of three categories: the owner of the file, someone in the file’s group, and everyone else.

Let's run ls -l

Let's run chmod
 
## Sudo

Add sudo info here

## What is SSH?

To make a remote login, we issue the command ssh username@computer (intro to supercomputing)

~~~
bash-3.2$ 
bash-3.2$ ssh username@computer
Password: ********
~~~
{: .language-bash}



### Transferring files

##scp

To copy a file, we specify the source and destination paths, either of which may include computer names. If we leave out a computer name, scp assumes we mean the machine we’re running on.

##Wget

Wget is a simple tool developed for the GNU Project that downloads files with the HTTP, HTTPS and FTP protocols. It is widely used by Unix-like users and is available with most Linux distributions.

Further information on transferring files esp. within Pawsey 
[Pawsey video on transferring files](https://youtu.be/3drzw-4aZTg)


