# Bash scripting
Writing many commands in one executable file to execute them at once - useful for automation

Use `#` for comments

First line should tell the computer what program it should use to execute the file (`shebang`)
- Often looks like `#!/bin/bash` ,which uses the bash interpreter

Use `echo` to print out to the terminal (Standard output)

Use `read` to take input from the user

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
    process
else
    alternative process
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
     block of code 
done
```
## For loop
Allows the system to do a task repeatedly for items in a set
```bash
#Syntax
for variable_name in {range} # range e.g - {1..10}
do
    block of code
done
```
## Case Statements
use `;;` to show end of a case statement line
```bash
#Syntax

#Call to action statement(s)
read variable_name; #take user input and store it in variable_name
case $variable_name in 
     1) case statement ;; #case statements
    .
    .
    .
    *) #kinda like a catch-all,executes when user didnt select option from provided range
esac # exit the case statement block
```
# Functions
Useful for repetitive blocks of code
```bash
#Syntax
#Function declaration
function_name () {
    block of code
}

#Function call
#code
function_name
```
# Scheduling jobs
Use `at` command to make a script or command run at a specific time







