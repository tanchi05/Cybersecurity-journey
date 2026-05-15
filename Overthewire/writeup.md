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



















































