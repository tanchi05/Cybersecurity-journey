# Bash scripting
Writing many commands in one executable file to execute them at once - useful for automation

First line should tell the computer what program it should use to execute the file (`shebang`)
- Often looks like `#!/bin/bash` ,which uses the bash interpreter

Use `echo` to print out to the terminal

Variable assignment = `variable = variable_name`

To print out the variable, `$variable_name`

Variables are tied to that particular session,get erased after terminal is closed

`files=$(ls)` runs the `ls` command in the background and stores the output in the newly created files variable
# Control Statements
## If statement
Executes a command as per the given conditions / Execute different statements based on the given criteria

```bash
if [ condition ]
then
    [process]
else
   [ alternative process]
fi # come out of the if block
```
### Exit codes
Used to show successful or failed execution

Code `0` means successful execution

Any other status code means execution did not complete successfully

`exit` on a script terminates execution of the script immediately and forces it to exit with whatever exit code was assigned
## While loop
Executes a block repeatedly until the base case is satisfied
```bash
#Syntax
while [ base case ]
do
    [ block of code ]
done
```









