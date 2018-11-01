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
# Permissions
Unix controls who can read, modify, and run files using concepts of *file ownership* and *permissions* to provide security at the file system level.  Using Pawsey systems will require knowledge of unix permissions.   

Users can belong to any number of groups, each of which has a unique group name and numeric group ID.* Every file and directory on a Unix computer belongs to one owner and one group. Along with each file’s content, the operating system stores the numeric IDs of the user and group that own it.

The user-and-group model means that for each file every user on the system falls into one of three categories: 1) the owner of the file, 2) someone in the file’s group, and 3) everyone else.

To discover the permissions and associated group for any file / directory use the command 'ls -l' 

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

For the ten permission flags (drwxrwxr-x)

Position   |   Meaning
----|----
1	        |  "d" if a directory, "-" if a normal file
2, 3, 4	  |  read, write, execute permission for user (owner) of file
5, 6, 7	  |  read, write, execute permission for group
8, 9, 10	 |  read, write, execute permission for other (everyone)

* **Read** access would allow you to view a file
- **Write** access would allow you to modify a file (e.g. edit or delete)
+ **Execute** access would allow 'execute' or run code (e.g. scripts) in a file.  For directorues it also allows you enter directory with 'cd' command  


> ## How do you change permissions?
>
> We use the *chmod* command.  The chmod command specifies read-write-execute permissions for the user, and 
> read-execute permissions for group and other.
>
> It can be applied recusively to directories using the '-R' option.  Octal values or symbolic representations of the flags > can be used to change permissions
>
> ### Octal
>
> Octal digit | Permission | Binary representation (rwx)
> --- | --- | ---
> 7 | read, write and execute | 111
> 6 | read and write | 110
> 5 | read and execute | 101
> 4 | read only | 100 
> 3 | write and execute | 011
> 2 | write only | 010
> 1 | execute only | 001
> 0 | none | 000
> 
> 4 = read , 2 = write , 1 = execute
>
> ### Symbolic
>
> | Reference | Class | Description |
> | --- | --- | --- | 
> | u | user | file's owner |
> | g | group | members of the file's group |
> | o | others | users who are niether file's owner or members of file's group |
> | a | all | all three of the above |
>
> | Operator | Description |
> | --- | --- |
> | + | adds the specified modes from specific classes |
> | - | removes the specified modes from the specified classes |
> | = | the modes specified are to be made the exact modes for the specified classes |
>
> e.g. *chmod a-w* 
> remove write (w) permissions for all classes (a), preventing anyone from writing to the file
>
>
> Let's create a file, say permissions.txt and experiment with changing permissions
>
> ~~~
> $ nano permissions.txt
> $ chmod 777 permissions.txt
> $ ls -l
> ~~~
> {: .language-bash}
>
>
> ~~~
> -rwxrwxrwx 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
> ~~~
> {: .output}
>
> ***
>
> You can see applying *chmod 777* lets everybody do everythng to the file.  
> Let's try make it more restrictive with *chmod 755* 
> ~~~
> $ chmod 755 permissions.txt
> $ ls -l
> ~~~
> {: .language-bash}
>
>
> ~~~
> -rwxr-xr-x 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
> ~~~
> {: .output}
>
> ***
>
> chmod 755 ensures files should be readable and executable by others, but only changable by issuing user.  
> What happens if we do *chmod 600*?
> ~~~
> $ chmod 600 permissions.txt
> $ ls -l
> ~~~
> {: .language-bash}
>
> 
> ~~~
> -rw------- 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
> ~~~
> {: .output}
>
> ***
>
> You'll see that permissions.txt becomes a private file only changable by the user who entered this command.  
> Finally let's try the example  *chmod a-w* that uses symbols rather than octals
> ~~~
> $ chmod a-w permissions.txt
> $ ls -l
> ~~~
> {: .language-bash}
>
> 
> ~~~
> -r-------- 1 lukeedwards lukeedwards      6 Oct 31 06:20 permissions.txt
> ~~~
> {: .output}
> 
> Examples from another Supercomputing Centre - [NERSC unix permisssions](http://www.nersc.gov/users/storage-and-file-systems/unix-file-permissions/)
> 
{: .callout}



# Transferring files

### scp

To copy a file, we specify the source and destination paths, either of which may include computer names. If we leave out a computer name, scp assumes we mean the machine we’re running on.

### Wget

Wget is a simple tool developed for the GNU Project that downloads files with the HTTP, HTTPS and FTP protocols. It is widely used by Unix-like users and is available with most Linux distributions.

Further information on transferring files esp. within Pawsey 
[Transferring files within Pawsey](https://youtu.be/3drzw-4aZTg)

 
# Other useful information

### SSH

If we want to run some commands on another machine, such as a Pawsey supercomputer or virtual machine? To do this, we have to first log into that machine. We call this a remote login.

In order for us to be able to login, the remote computer must be runing a remote login server and we will run a client program that can talk to that server. The client program passes our login credentials to the remote login server and, if we are allowed to login, that server then runs a shell for us on the remote computer.

Once our local client is connected to the remote server, everything we type into the client is passed on, by the server, to the shell running on the remote computer. That remote shell runs those commands on our behalf, just as a local shell would.

To make a remote login, we issue use the followeing syntax 'ssh username@remote_host' 

The remote host is the IP address or domain name that you are trying to connect to 

~~~
bash-3.2$ 
bash-3.2$ ssh bob@magnus.pawsey.org.au
Password: ********
~~~
{: .language-bash}

Mention SSH keys?

### Sudo

'sudo' is a program that allows users to run programs with the security privilages of another user, usually 'superuser' with 'root' access.  Short for 'superuser do' or 'substitute user do'  

This is useful for when you temporarily want elevated privilages such as running a virtual machine.  See more at [Using Nimbus: Cloud computing at Pawsey](https://pawseysc.github.io/using-nimbus/) 

### Awk

others?


The awk command is a powerful method for processing or analyzing text files—in particular, data files that are organized by lines (rows) and columns. 


The basic format of an awk command looks like this:
~~~
awk 'pattern {action}' input-file > output-file
~~~
{: .language-bash}




