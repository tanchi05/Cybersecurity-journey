# Linux basics
## Syntax rules
Space is a delimiter in linux terminal 

- Correct way `variable="value"`

- Wrong way  `variable = "value"`
### Operators
`&` allows you to run commands in the background of your terminal

`&&` allows you to combine multiple commands in one line of your terminal

`>` redirects output elsewhere, eg into a file

`>>` redirects output but appends instead of replacing content in the target file

Environment variables are available to all programs that run in your shell
`env` command to view all environment variables
Use the `export` command to set a variable in your shell

## Input/Output
`man` command gets the manual of a program

Flags are options you can pass to a command to change its behaviour

Eg the `ls` command can take the `-l` flag to show a long listing of files

Use `|` to pipe output of program into the input stream of another program

Automate a script by piping it into the shell (`sh`)
### conventions
- single character flags are predixed with a single dash, i.e `-l`
- multi-character flags are prefixed with double dash, i.e `--help`
- sometimes the same flag can be used with single or double dash, i.e `-h` or `--help`

`curl` is a cli tool that lets you make network requests from the commandline

## Permissions
drwxrwxrwx - permission string that shows owner,group and others permissions
* rwx = read,write,execute permissions
```bash
sudo # lets u run commands as superuser

chmod # change the permissions of a file or a directory

chmod +x / chmod -x # add/remove permission to execute a file

chown # changes ownership of a file\

```
### Executables
.sh files are shell scripts - run them by typing their file path

Prefix eg. `./script.sh` to tell the shell to run the file from the active directory

`which` command tells you the location of an installed command line program

Add shebang at the top of a script to tell the shell what program it should use to run the script

Format is `#! interpreter [optional-args]`
- Example shebang
```bash
#!usr/bin/python3   #This tells the shell to use the python3 interpreter located at usr/bin/python3 to run the script
```
`kill PID` command is used to manually kill a process by its ID

`ps` command shows process status
`ps aux` shows all processes and their status
## File systems
```bash
pwd # (print working directory) shows the current directory

cd # change directories/move into a directory

.. # takes you back out of a directory

ls # lists all files and sub-directories

mkdir #  creates a new directory

rm # remove a file or empty directory

rm -r # removes recursively

cat # view the content of a file

touch # create an empty file or,update access and modification time of a file

> # create and empty file an add content to it

>> # append content to an existing file

nano # create a new file and immediately write into it using the nano terminal editor

vim # like nano but use vim terminal editor

head & tail # print a specific number of lines of text from a file strarting from top/bottom respectively

mv # rename a file or move it to a new directory

cp # copy a file to a different directory

grep # use it to search for a string in a file

find # used to search for a file
```
## Other commands
`history` command shows all commands you typed into the terminal

`whoami` shows active user

`clear` clears your terminal

`top` command allows you to see what programs are using the most resources on your computer

### Package managers
Package managers are s/w that help you install other s/w
`apt` is default package manager for ubuntu
```bash
sudo apt update # updates the apt package
```
`webi` lets you download command line tools directly from the internet
