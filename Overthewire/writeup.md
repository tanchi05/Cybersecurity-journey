# Level 0
Ssh into `bandit.labs.overthewire.org` as bandit0 and port `2220`

Used `ls` to list all files and directories

Used `cat` to open readme file and get password for level 2

# Level 1
ssh as bandit1 
Goal - get the password from the `-` file

used `./` before the filename to read the contents of the file

# Level 2
Goal - read a file with `--` and spaces in the name

used `./` before the file name 

used `\` before any space characters

# Level 3
Goal - get the password from a hidden file

use `ls -a` to list all files in the directory including the hidden files

# Level 4
Goal - find the human readable file

using `cat` on the files individually was slow

most of the files contained a bunch of gibberish

`find` alone showed all files in the directory

used `less ./*` to eliminate the bin files

# Level 5
Goal - Find a file based on its properties

Lots of directories and files opening each one by one is hectic . Pulled up the find manual

`-size` specifies file size when searching

`find . -size 1033c` - find all files with 1033 bytes (`c` = `bytes`)

# Level 6
Goal - Find a file on the server by user or group or size

Finding by size brought too many results

Try finding by `-user` and `-group` - still too many results with permission denied

Added `2>/dev/null` to the command to ignore the permission denied files

# Level 7
Get password from data.txt

used `cat` to open file - too much data

Pipelined `|` to `grep` and caught the line with `millionth`

# Level 8
Get the password - in the line that appears only once

used `sort` then paired with `uniq -u` to print only the lines that appeared one

# Level 9
Get password hidden in one of the only human readable strings

`strings` command returned all string in each line

used `grep` to get the lines with `=`

# Level 10
Get password from a file that contains base 64 encoded data

use `base64 -d` to decode file data

# Level 11
Get password from a file where all uppercase and lowercase letters have been rotated 

`tr` translates characters - works only with standard input,not files

`cat` the file then pipeline it into `tr 'your-alphabet' 'translation-logic'`

# Level 12
Get the password from a repeatedly compressed file

used `xxd -r` to revert file data back to binary

used `xxd data.txt | head -n 1` to get the file type
* 1f8b - is a gzip file
used `file` command to find the file type

repeatedly decompressed the files based on their file types

- `gunzip` for gzip files (`.gz`)
- `bunzip2` for bzip2 files (`.bz2`)
- `tar` for tar files

# Level 13
Get the private ssh key that can be used to log into the next level

Got the RSA private key & copied to local file

Tried logging in using the local file with key but file ignored due to too many open permissions,changed permissions to 700 

# Level  14
Submit current level password to port 30000 for next password

Used telnet to connect to localhost port 30000

# Level 15
Submit the password to a port using ssl/tls encryption

Used `openssl`....`openssl s_client -connect host:port`

# Level 16
Scanning for listening ports

Used `nmap -p31000-32000 localhost` to scan for listening ports

Added -sV in the options and scanned the resulting ports manually to get the service

Used openssl to send current password to the port

# Level 17
Used `diff` to compare 2 files line by line 

# Level 18
Should read a file immediately after logging in

Appended a cat command to the ssh command

# Level 19
Use the binary file to run a command as a different user

use `./` just in case the pasth is not set

# Level 20 
Took me sometime to figure out what i was supposed to do

Created 2 terminals each connected to bandit

used `nc` to set up a listener on a port and sent the password - ` echo password | nc -l -p port`

ran suconnect on the other terminal with the port i created

# Level 21
Checking what cron job is being executed

Cd into `/etc/cron.d/` and list items

cat cronjob_bandit22 and found the location of the script scheduled to run

cat the script to get the location of the file in the tmp dir where the password is stored

# Level 22
Checking the cronjob script

read line by line to understand the logic

uses md5sum encryption to create filename for next level password

modify the echo line to bandit23 to see the filename in the /tmp dir

cat the file

# Level 23
We're supposed to create a script which will be executed by the system as scheduled

Script to be executed should be in the /var /spool.... as per the the crontab

first created a script to read bandit24 pass in the /tmp/myfolder

gave everyone execute permissions to the script

created a blank password file in the /tmp/myfolder and gave everyone write permissions to it (use `chmod` to change permissions)

modified the script so the read bandit24 password is sent to my password file in the /tmp/myfolder

transferred the script to the /var/spool... dir that is scheduled by cron to be executed

script executed and password sent to my password file

# Level 24
Supposed to connect to the daemon on port 30002 then send password with a pin

first connected to it using `nc` to see how it looks

it expects a bandit24 password and a 4 digit pin

too many options,so i write a script that uses a for loop to write the bandit24 password and a 4 digit pin separated by a space

4 digit pins from 1000 - 9999.....too many trials

run the script and pipe it into the `nc` command so nc brute forces all possible combinations of password and 4 digit pin until match is found

process stopped immediately password was found..but could have used `grep -v` to only display the line without the error message

# Level 25
log in and copy the bandit26 private key

# Level 26
Connection closes immediately after connecting

log in as bandit25 and check out how bandit logs in ,in the /etc/pass 

Minimise terminal to break out of the shoetext script with the more command

use the vim to type external commands

set shell to the normal `/bin/bash`

launch the shell from vim and use the `bandit27-do` binary to extract bandit27 password from bandit26 connection

use `./` since bandit27-do is not a command

# Level 27
have git on my local machine

access the git repo at bandit27

clone the repo to my local machine (use port 2220 while cloning )

# Level 28
clone the bandit 28 repo just as in previous step

password looks weird

use `git-log` to check the commit history - password was changed

used `git checkout` with the commit hash to go back to the initial state of the readme file

# Level 29
clone repo as in previous level

no password in the readme

pull the log and jump to the initial commit but still no pass

checkout back to master and check for any branches

jump to the dev branch and get the pass

# Level 30
clone the repo

the readme has nothing

check the logs for commit timeline but none

check all branches but still no branches

check tags.Use `git show` to see the tag

# Level 31
clone the repo

task is to create and push a file

used `-f` from the hint when adding so the .txt file is not ignored 

commit then push

# Level 32
gets logged into an uppercase shell

trick is escaping from the uppercase shell into a normal shell

use a command that works in uppercase and doesnt change meaning - `$SHELL`




























































