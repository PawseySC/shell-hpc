---
title: "Extra useful things to know"
teaching: 15
exercises: 5
questions:
- "What other useful things should I know?"
objectives:
- "Explain how the shell relates to the keyboard, the screen, the operating system, and users' programs."
- "Explain when and why command-line interfaces should be used instead of graphical interfaces."
keypoints:
- "Explain the steps in the shell's read-run-print cycle."
- "Most commands take flags (options) which begin with a `-`."
- "Identify the actual command, flags, and filenames in a command-line call."
- "Explain the steps in the shell's read-run-print cycle."
- "Demonstrate the use of tab completion and explain its advantages."
keypoints:
- "A shell is a program whose primary purpose is to read commands and run other programs."
- "The shell's main advantages are its high action-to-keystroke ratio, its support for automating repetitive tasks, and its capacity to access networked machines."
- "The shell's main disadvantages are its primarily textual nature and how cryptic its commands and operation can be."
- "Shell tips a) **CTRL+C:** to kill / exit current process b) **Tab autocomplete:** esp. useful to enter long complex filenames c) **UP arrow:** gives you previous commands entered"
---
### Permissions
Linux is a multi-user OS that is based on the Unix concepts of file ownership and permissions to provide security at the file system level.

Add more here
 
### Sudo

Add sudo info here

### What does it look like?

A typical shell command and output looks something like this:

~~~
bash-3.2$ 
bash-3.2$ ls -F / 
Applications/         System/
Library/              Users/
Network/              Volumes/
bash-3.2$ 
~~~
{: .language-bash}

The first line shows only a **prompt**, indicating that the shell is waiting
for input. Your shell may use different text for the prompt. Most importantly: 
when typing commands, either from these lessons or from other sources,
*do not type the prompt*, only the commands that follow it.

The part that you type (in this example `ls -F /`)
typically has the following structure: a **command**,
some **flags** (also called **options** or **switches**) and an **argument**.
Flags start with a dash (`-`), and change the behaviour of a command.
Arguments tell the command what to operate on (e.g. files and directories).
Sometimes flags and arguments are referred to as parameters.
A command can be called with more than one flag and more than one argument: but a
command doesn't always require an argument or a flag.

In the example above, our **command** is `ls`, with a **flag** `-F` and an
**argument** `/`. Each part is separated by spaces: if you omit the space 
between `ls` and `-F` the shell will look for a command called `ls-F`, which 
doesn't exist. Also, capitalization matters: `LS` is different to `ls`. 

Next we see the output that our command produced. In this case it is a listing 
of files and folders in a location called `/` - we'll cover what all these mean 
later today. Those with a Mac might recognize the output in this example.

Finally, the shell again prints the prompt and waits for you to type the next 
command.

Open a shell window and try entering `ls -F /` for yourself (don't forget that spaces
and capitalization are important!). 

### How does the shell know what `ls` and its flags mean?

Every command is a program stored somewhere on the computer, and the shell keeps a
list of places to search for commands (the list is in a **variable** called `$PATH`, 
but those are concepts we'll meet later and not too important at the moment). Recall
that commands, flags and arguments are separated by spaces.

So let's look at the REPL (read-evaluate-print loop) in more detail. Notice that the
"evaluate" step is made of two parts:

1. Read what was typed (`ls -F /` in our example)  
    The shell uses the spaces to split the line into the command, flags, and arguments
2. Evaluate:  
    a. Find a program called `ls`  
    b. Execute it, passing it the flags and arguments (`-F` and `/`) to 
       interpret as the program sees fit 
3. Print the output produced by the program

and then print the prompt and wait for you to enter another command.

> ## Command not found 
> If the shell can't find a program whose name is the command you typed, it 
> will print an erorr message like:
> 
> ~~~
> $ ls-F
> -bash: ls-F: command not found
> ~~~
> {: .language-bash}
> 
> Usually this means that you have mis-typed the command - in this case we omitted
> the space between `ls` and `-F`. 
{: .callout}

### Is it difficult?

It isn't difficult, but it is a different model of interacting than a GUI, and that 
will take some effort - and some time - to learn. A GUI 
presents you with choices and you select one. With a CLI the choices are combinations 
of commands and parameters, more like words in a language than buttons on a screen. They
are not presented to you so
you must learn a few, like learning some vocabulary in a new language. But a small 
number of commands gets you a long way, and we'll cover those essential few today.


