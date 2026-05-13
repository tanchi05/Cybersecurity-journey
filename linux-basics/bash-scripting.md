# Bash scripting
Writing many commands in one executable file to execute them at once - useful for automation

First line should tell the computer what program it should use to execute the file
- Often looks like `#!/bin/bash` ,which uses the bash interpreter

Use `echo` to print out to the terminal

Variable assignment = `variable = variable_name`

To print out the variable, `$variable_name`

Variables are tied to that particular session,get erased after terminal is closed

`files=$(ls)` runs the `ls` command in the background and stores the output in the newly created files variable
# If statement
```bash
if [ condition ]
then
    [process]
else
   [ alternative process]
fi # come out of the if block
```
