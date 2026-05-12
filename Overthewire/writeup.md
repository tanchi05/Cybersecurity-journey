# Level 1
Ssh into `bandit.labs.overthewire.org` as bandit0 and port `2220`

Used `ls` to list all files and directories

Used `cat` to open readme file and get password for level 2

# Level 2
ssh as bandit1 
Goal - get the password from the `-` file

used `./` before the filename to read the contents of the file

# Level 3
Goal - read a file with `--` and spaces in the name

used `./` before the file name 

used `\` before any space characters

# Level 4
Goal - get the password from a hidden file

use `ls -a` to list all files in the directory including the hidden files

# Level 5
Goal - find the human readable file

using `cat` on the files individually was slow

most of the files contained a bunch of gibberish

`find` alone showed all files in the directory

used `less ./*` to eliminate the bin files

# Level 6
Goal - Find a file based on its properties

Lots of directories and files opening each one by one is hectic . Pulled up the find manual

`-size` specifies file size when searching

`find . -size 1033c` - find all files with 1033 bytes (`c` = `bytes`)

# Level 7
Goal - Find a file on the server by user or group or size

Finding by size brought too many results

Try finding by `-user` and `-group` - still too many results with permission denied

Added `2>/dev/null` to the command to ignore the permission denied files

# Level 8
Get password from data.txt

used `cat` to open file - too much data

Pipelined `|` to `grep` and caught the line with `millionth`

# Level 9
Get the password - in the line that appears only once

used `sort` then paired with `uniq -u` to print only the lines that appeared one

# Level 10
Get password hidden in one of the only human readable strings

`strings` command returned all string in each line

used `grep` to get the lines with `=`

# Level 11
Get password from a file that contains base 64 encoded data

use `base64 -d` to decode file data

# Level 12
Get password from a file where all uppercase and lowercase letters have been rotated 

`tr` translates characters - works only with standard input,not files

`cat` the file then pipeline it into `tr 'your-alphabet' 'translation-logic'`

# Level 13
Get the password from a repeatedly compressed file

used `xxd -r` to revert file data back to binary

used `xxd data.txt | head -n 1` to get the file type
* 1f8b - is a gzip file
used `file` command to find the file type

repeatedly decompressed the files based on their file types

- `gunzip` for gzip files (`.gz`)
- `bunzip2` for bzip2 files (`.bz2`)
- `tar` for tar files

# Level 14
Get the private ssh key that can be used to log into the next level















