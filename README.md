# Implementing basic shell commands in C

#### Description:


### HOW TO RUN:

```
gcc shell.c -o shell

./shell
```

### COMMANDS IMPLEMENTED:
```
(file_path)$ cd <directory_name>
```
changes the current directory to the specific directory
<directory_name> can be absolute or relative path w.r.t currrent directory

```
(file_path)$ ls <directory_name>
```
lists information about files in the given directory
if no <directory_name> is provided, lists files in the present directory
<directory_name> can be absolute or relative path w.r.t currrent directory

```
(file_path)$ rm [-f -r -v] <files/directories> ...
```
-v  print the name of the deleted files
-r  recursively deletes the contents of the directory
-f  forcibly deletes the files without prompt

```
(file_path)$ rmexcept <list_of_files>
```
deletes all the contents of the current directory except the specified files.
(does not remove directories if they are not empty)

```
(file_path)$ <program_name> < <input_file> > <output_file> m
```
<input_file>, <output_file>, m are optional
takes input from <input_file>
takes output from <output_file>
stops the execution on <program_name> if time exceeds 'm' seconds.

```
(file_path)$ history n
```
lists the previous n recent number of commands
if no n is provided prints whole history

```
(file_path)$ issue n
```
runs the nth command in the history

```
(file_path)$ clear
```
clears the terminal screen

```
(file_path)$ exit
```
exits the shell

## Implementation Details

shell.c has three functions and a main function

is_directory(): tells whether a path is a directory or not
recu_del(): deletes all contents of a directory in depth first search pattern
kill_child(): kills the child if time limit exceeds
every command is executed by a child process except 'cd' and 'issue n'

## Lesson taken from this Project

A shell does three main things in its lifetime.

Initialize: In this step, a typical shell would read and execute its configuration files. These change aspects of the shell’s behavior.
Interpret: Next, the shell reads commands from stdin (which could be interactive, or a file) and executes them.
Terminate: After its commands are executed, the shell executes any shutdown commands, frees up any memory, and terminates.

By executing the program via ./shell we Initialize the shell. In the main() function we have a infinite while loop where user input is expected in every iteration. This cmd supplied by the user is then Interpreted, If the command is to terminate the program i.e exit/quit we break the while loop and return.
If command is valid, then we parse the command for any additional args and use a switch/if-else condition block to execute the intentions of the command.
