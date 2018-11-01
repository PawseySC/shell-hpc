---
title: "Extra - Useful things to know"
teaching: 15
exercises: 5
questions:
- "What other useful things should I know?"
objectives:
- "To understand unix permissons."
- "To understand how to move data around"
keypoints:
- "Use *ls -l* to view the permissions for a specific file."
- "Use *chmod* to change permissions on a file or directory."
keypoints:
- "Use *ls -l* to view the permissions for a specific file."
- "Use *chmod* to change permissions on a file or directory."
- "TO DO."
---
### Permissions
Unix controls who can read, modify, and run files using concepts of *file ownership* and *permissions* to provide security at the file system level.  Using Pawsey systems will require knowledge of unix permissions.   

Users can belong to any number of groups, each of which has a unique group name and numeric group ID.* Every file and directory on a Unix computer belongs to one owner and one group. Along with each file’s content, the operating system stores the numeric IDs of the user and group that own it.

The user-and-group model means that for each file every user on the system falls into one of three categories: 1) the owner of the file, 2) someone in the file’s group, and 3) everyone else.

To discover the permissions and associated group for any file / directory use the command "ls -l" 

~~~
$ ls -l
~~~
{: .language-bash}

~~~
drwxrwxr-x 7 lukeedwards lukeedwards   4096 Sep 15  2017 data-shell
~~~
{: .output}


The output above represents:

1) set of ten permission flags
2) link count (irrelevant to this topic)
3) owner
4) associated group
5) size
6) date of last modification
7) name of file

For the ten permission flags

drwxrwxr-x

Position   |   Meaning
----|----
1	        |  "d" if a directory, "-" if a normal file
2, 3, 4	  |  read, write, execute permission for user (owner) of file
5, 6, 7	  |  read, write, execute permission for group
8, 9, 10	 |  read, write, execute permission for other (everyone)


## How do you change permissions?

We use the *chmod* command.  The chmod command specifies read-write-execute permissions for the user, and read-execute permissions for group and other.

It can be applied recusively to directories using the '-R' option.  Octal values or symbolic representations of the flags can be used to change permissions

# Octal

Octal digit | Permission | Binary representation (rwx)
--- | --- | ---
7 | read, write and execute | 111
6 | read and write | 110
5 | read and execute | 101
4 | read only | 100 
3 | write and execute | 011
2 | write only | 010
1 | execute only | 001
0 | none | 000

4 = read | 2 = write | 1 = execute

# Symbolic

| Reference | Class | Description |
| --- | --- | --- | 
| u | user | file's owner |
| g | group | members of the file's group |
| o | others | users who are niether file's owner or members of file's group |
| a | all | all three of the above |

| Operator | Description |
| --- | --- |
| + | adds the specified modes from specific classes |
| - | removes the specified modes from the specified classes |
| = | the modes specified are to be made the exact modes for the specified classes |

e.g. *chmod a-w* 
remove write (w) permissions for all classes (a), preventing anyone from writing to the file

Let's create a file, say permissions.txt and experiment with changing permissions

~~~
$ nano permissions.txt
$ chmod 777 permissions.txt
$ ls -l
~~~
{: .language-bash}

~~~
-rwxrwxrwx 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
~~~
{: .output}

You can see applying *chmod 777* lets everybody do everythng to the file.  Let's try make it more restrictive with *chmod 755* 

~~~
$ chmod 755 permissions.txt
$ ls -l
~~~
{: .language-bash}

~~~
-rwxr-xr-x 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
~~~
{: .output}

chmod 755 ensures files should be readable and executable by others, but only changable by issuing user.  
What happens if we do *chmod 600*?


~~~
$ chmod 600 permissions.txt
$ ls -l
~~~
{: .language-bash}

~~~
-rw------- 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
~~~
{: .output}

You'll see that permissions.txt becomes a private file only changable by the user who entered this command

Examples from another Supercomputing Centre - http://www.nersc.gov/users/storage-and-file-systems/unix-file-permissions/
 
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

## scp

To copy a file, we specify the source and destination paths, either of which may include computer names. If we leave out a computer name, scp assumes we mean the machine we’re running on.

## Wget

Wget is a simple tool developed for the GNU Project that downloads files with the HTTP, HTTPS and FTP protocols. It is widely used by Unix-like users and is available with most Linux distributions.

Further information on transferring files esp. within Pawsey 
[Pawsey video on transferring files](https://youtu.be/3drzw-4aZTg)


