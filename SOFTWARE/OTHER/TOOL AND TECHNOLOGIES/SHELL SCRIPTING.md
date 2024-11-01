
### Comman commands
- `echo`
- `cat`
- `ls`
- `sleep 3` // terminal sleep for 3 second or pause the process for 3 second
- `cd`
- `man`
- `ping`
- 
1. echo variable ---> use to print
2. ls   --->  show all item in directory
    - ls -a ---> show all item also hidden item.
    - ls -r ---> all item with subitem
    - ls -l ---> show all item with extra information
 
3. **mkdir "name"** --> create folder
4. **start . or open .** ---> open current dir in GUI
5. **cd "location"**  ---> change directory
    - **cd ..**  --->  back to the folder
    - **cd s:** ---> change drive to s
    - **cd hello/** ---> go to hello folder
6. **cat "file name"** --> read file
    - cat > "name" => "write "  ---> create & write
7. pwd ---> show current working directory 
8. touch "file_name"  ---> create file
9. cp "file1" "file2"  --->  copy containt file1 to file2
    - cp -r folder1 folder2  --->  folder1 copy inside folder2
10. mv source target ---> move file
       - mv file1 file2 ----> rename if file2 doesn't exist
 11. rm "filename"  ---> delete file
      - rm -r folder ---> delet folder
      - rmdir folder  ---> delete folder
 12. **df**  ---> disk space and more info
       **df -m** --->  show in mb
13. **du** ---> show folder space
14. head -n num "file" ---> show data of file num line form head
15. tail -n num "file"  ---> show data of file num line from tail
16. diff "file1" "file2"  --->  compare line by line
17. locate "file"  ---> find file
18. find folder ---> find folder

## Environment variable : 
  - environment variable are global system variable accessible by the all the processes/users running under (eg-cmd) operating system (os) , such as window , macos & linux.
  - environment variable are useful to store system wide values for example
      - PATH :
      - OS:
      - COMPUTERNAME ,USERNAME:
      - SystemRoot:
      - HOMEDRIVE , HOMEPATH:
   - In cmd we write any cmd like git or npm or other first check PATH variable 
     content folder content any executable file name the command then run 
	    - eg - cmd git init => find git.exe and run 
	    - echo $PATH ---> use to see PATH variable value & other env var value
##

[link with basic](BASIC)



## redirection, & , pipe 

## What is Shell
 - In shell scripting, A **shell** refers to a command-line interpreter that provides a user interface for interacting with the operating system. It allows users to execute commands, run programs, and manage files. The shell processes the input commands and executes them either directly or by invoking the appropriate programs.
 - There are various types of shells, each with its own scripting language and features. Some popular ones include:
     - **Bash (Bourne Again Shell)**: The most widely used shell in Linux and Unix systems. It is an extension of the original Bourne shell (sh).
	- **Sh (Bourne Shell)**: One of the earliest shells, known for its simplicity and portability.
	- **Zsh (Z Shell)**: Offers additional features like better tab completion, spell-checking, and syntax highlighting.
	- **Ksh (Korn Shell)**: Combines features from the C shell (csh) and Bourne shell, with scripting capabilities.
- cmd: cat  /etc/shells --> to see which shells you have
- cmd : which shellname(eg:bash) --> to see where the shell 

### First script file
- make a file first.sh or first
- `#!/bin/bash
   ` echo "hello world"`
- first give permission `cmd: chmod +x first.sh` then  run by .`cmd : /first.sh `
- run without permission `cmd: bash first.sh `


## comment 
- #this is a comment 
### variable
- **Define**: `VAR_NAME=value`
- **Access**: `echo $VAR_NAME`
- **Export**: `export VAR_NAME` : To make a variable available to child processes or subshells, use the `export` command
- **Read-only**: `readonly VAR_NAME` : If you want to prevent a variable from being changed, you can declare it as read-only using the `readonly` command:
- **Unset**: `unset VAR_NAME` :To remove a variable, you can use the `unset` command: 

### System Variables in Bash
- **Definition**: System (or environment) variables are dynamic values that provide information about the environment and configure the behavior of processes and applications.
-  **Common System Variables**
	1. **`$HOME`**: Current user's home directory.
	2. **`$USER`**: Name of the currently logged-in user.
	3. **`$PATH`**: List of directories for executable files.
	4. **`$SHELL`**: Path of the current shell (e.g., `/bin/bash`).
	5. **`$PWD`**: Current working directory.
	6. **`$OLDPWD`**: Previous working directory.
	7. **`$LANG`**: Current language setting.
	8. **`$EDITOR`**: Default text editor.
	9. **`$UID`**: User ID of the current user.
	10. **`$HOSTNAME`**: Name of the current host.
	11. **`$BASH_VERSION`**: Bash version
	
- **Viewing Environment Variables**
	- **`printenv`**: Lists all environment variables.
	- **`env`**: Displays all environment variables.
	- **`set`**: Shows all variables (environment and shell).
	### Setting and Modifying Environment Variables
**Setting and Modifying Environment Variables**
- **Setting a Variable**: You can define a new variable or modify an existing one by using
    `VARIABLE_NAME=value`
- **Exporting a Variable**: To make a variable available to all child processes or subshells, use the `export` command:      
    `export VARIABLE_NAME`

### Array 
**Declaring an Array**
my_array=("apple" "banana" "cherry")
**Accessing Array Elements**
echo "${my_array[0]}"  # Outputs: apple
**Adding Elements to an Array**
my_array[3]="date"
**Printing All Elements in an Array**
echo "${my_array[@]}"   # Prints all elements
echo "${my_array[\*]}\"   \# Also prints all elements
**Finding Array Length**
echo "${#my_array[@]}"  # Outputs the number of elements in my_array
**Removing an Element from an Array**
unset my_array[1]  # Removes "banana"
**Looping Through an Array**
```bash 
for element in "${my_array[@]}"; do
    echo "$element"
done```

### Readonly variable
- name suggest variable that only use for read purpose , can't be overwrite
- To make variable readonly syntax `readonly var`


### Input form user
- `read name ` OR `read -p "Enter your name : " name`
- for password `read -s pass` OR `read -sp 'Enter your password : ' pass`
- input in as array  `read -a array` And print `echo ${array[0]}`
- input without variable `read` And print `echo $REPLY ` , REPLY is builtin variable .

### Pass Argument
- ./first.sh ahsan ahmad , access by `echo $1 $2` ,// $1= "ahsan" , $2 = "ahmad" {$0 = "./first.sh"}
- `echo $@` // print all the arguments form $1 to all which are passed
- var=("$@") => ${var[0]} =  $1 , ${var[1]} = $2,
- `echo $# ` // print number, how many argument passed


### Conditional statements
 **interger comparison **
- \-eq  -> is equal to - `if [ "$a" -eq "$b" ]`
- \-ne  -> is not equal to - `if [ "$a" -ne "$b" ]`
- \-gt  -> is greater than - `if [ "$a" -gt "$b" ]`
- \-ge  -> is greater than or equal to - `if [ "$a" -ge "$b" ]`
- -lt    -> is less than - `if [ "$a" -lt "$b" ]`
- -le   -> is less than or equal to - `if [ "$a" -le "$b" ]`
-  <=  -> is less than or equal to - `(( "$a" <= "$b" ))`
-  >    -> is greater than - `(( "$a" > "$b" ))`
-  >=  -> is greater than or equal to - `(( "$a" >= "$b" ))`

**String Comparison**
- =    -> is equal to - `if [ "$a" = "$b" ]`
- ==  -> is equal to - `if [ "$a" == "$b" ]`
- !=   -> is not equal to - `if [ "$a" != "$b" ]`
- <    -> is less than, in ASCII alphabetical order - `if [[ "$a" < "$b" ]]`
- \>    -> is greater than, in ASCII alphabetical order - `if [[ "$a" > "$b" ]]`
- -z   -> string is null, that is, has zero length

 **IF Statement Syntax**
```bash
a=1
if [ $a -eq 1 ]
then
#statement if condition is true
fi
```

**IF-else Statement Syntax**
```bash
if [condition]
#statement if condition is true
else
#statement if condition is false
fi # close the if-else statemnet
```
``
**IF-else Ladder Statement Syntax**
```bash
if [condition]
#statement if condition is true
elif [condition]
then
#statement elseif condition istrue
else
#statement if condition is false
fi # close the if-else statemnet
```

**ternary  condition**
[ condition ] && true_stetament || false_statement

**Case Statement**
```bash
case expression in
    pattern1)
        # commands if pattern1 matches
        ;;
    pattern2)
        # commands if pattern2 matches
        ;;
    *)
        # commands if no patterns match (default case)
        ;;
esac

```
- Matching Multiple Patterns
```bash
read -p "Enter a letter (y/n/q): " input
case $input in
    [yY]|[yY][eE][sS])
        echo "You entered Yes."
        ;;
    [nN]|[nN][oO])
        echo "You entered No."
        ;;
    [qQ])
        echo "Quitting..."
        ;;
    *)
        echo "Invalid input, please enter y, n, or q."
        ;;
esac

```
- File Type Checking
```bash

read -p "Enter a filename: " filename

if [ ! -e "$filename" ]; then
    echo "File does not exist."
    exit 1
fi

case $filename in
    *.txt)
        echo "$filename is a text file."
        ;;
    *.jpg|*.png)
        echo "$filename is an image file."
        ;;
    *.sh)
        echo "$filename is a shell script."
        ;;
    *)
        echo "Unknown file type."
        ;;
esac
```


### Loop
**1. while loop**
```bash
#!/bin/bash
counter=1
while [ $counter -le 5 ]
do
    echo "Counter: $counter"
    ((counter++))  # Increment the counter
done
```
**2. Until loop**
loop run unit condition false 
```bash
until [ condition ]
do
#commands
done
```
**3. For loop**
Using C-style Syntax
```bash
for ((i=1; i<=5; i++))
do
    echo "Number $i"
done
```
OR, Looping Through Files
```bash
for file in \*.txt
do
    echo "Found file: $file"
done
```
OR, Iterating Over a Range of Numbers
```bash
for i in {1..5}
do
    echo "Number $i"
done
```
OR, Using "seq" for More Complex Ranges
```bash
for i in $(seq 1 2 10)
do
    echo "Number $i"
done
```
OR, Iterating Over a List of Items
```bash
for item in item1 item2 item3; do
    echo "Processing $item"
done
```
**4. Select loop**
for menu 
```bash
select opt in opt1 opt2 opt3
do
echo "you selected $opt"
done
```

*Note : we can use 'break' and 'continue' for break and skip*

### Logical operator
**logical AND**
Three way to implement it 
- \[ condition 1 ] && \[ condition 2 ] 
- \[ condition1 -a  condition2 ]
- \[\[ condition1 && condition2]]

**logical OR**
Three way to implement it
- \[ condition 1 ] || \[ condition 2 ] 
- \[ condition1 -o  condition2 ]
- \[\[ condition1 || condition2]]

### Arthmetical operator
- $((num1 + num2)) ==> addition
- $((num1 - num2)) ==> subtraction
- $((num1 * num2)) ==> multiplication
- $((num1 / num2)) ==> division
- $((num1 % num2)) ==> modulo
- $((num1 ** num2)) ==> exponantioal

**valid only for integer**
- $( $num1 + $num2) ==> addition
- $( $num1 - $num2) ==> subtraction
- $( $num1 \\* $num2) ==> multiplication
- $( $num1 / $num2) ==> division
- $( $num1 % $num2) ==> modulo

*NOTE:Above both way give error in noninterger calculation so use bc(basic calculator) tool*
**bc tool**: for basic calculator
- eg : echo "1.2+34" | bc


### Function
**Declaration and run**
```bash
function fun () #function declaration  way 1
{
echo "function have been run way1"
}

#OR 
fun ()
{
echo "function have been run way2"
}

fun #function run

```
**pass peramenters , access perameters and return**
```bash
function add ()
{
echo $(($1+$2))
}

add 90 80
```

- In bash all default all variable are global even in funtion , but we can make local variable in  function like this  `local var=value`

- To make readonly (means not can overwrite) use `readonly -f function_name`
- for see all readonly variable use `readonly`
- for see all the readonly function use `readonly -f`

### File classification
1. **Regular Files**
- Description: The most common file type, used to store data such as text, executable code, documents, or images.
- Types : Can be further divided into text files (e.g., `.txt`) and binary files (e.g., executables, images,video).
- Example : `/home/user/document.txt`, `/bin/bash`

2. **Directory Files**
- Description : Special files that act as containers for other files or directories, forming the file system hierarchy.
- Purpose : Organize files into a structured layout.
- Example : `/home`, `/usr/local`

3. **Device Files**
- Description: Files that represent hardware devices, allowing the OS and applications to interact with devices as files.
- Types:
    - **Block Special Files**: Handle data in fixed-size blocks (e.g., hard drives, `/dev/sda`).
    - **Character Special Files**: Handle data as streams of bytes (e.g., terminals, `/dev/tty`).
 
4. **Named Pipes (FIFOs)**
- Description: Special files that enable communication between processes by acting as a one-way data channel.
- Purpose: Primarily used for inter-process communication (IPC).
- Example: A named pipe for logging, `/tmp/logpipe`

5. **Socket Files**
- Description : Special files used for network communication between processes, both local and remote.
- Purpose : Commonly used in network services and server applications.
- Example : `/var/run/docker.sock`

6. **Symbolic (Soft) Links**
- Description: Pointers to other files or directories, allowing shortcuts or references without duplicating data.
- Purpose: Link to other files or directories, making them accessible from multiple locations.
- Example: `/home/user/docs -> /mnt/storage/docs`


###  File test operators
**Check file exist or not**
```bash
if [ -e $filename ]
then
echo "$filename file exist"
else
echo "file doesn't exist"
fi
```

**Check file empty***
```bash
if [ -s $filename ]
then
echo "$filename is not empty"
else
echo "file is empty"
fi
```

**Check file is regular file and exist**
```bash
if [ -f $filename ]
then
echo "$filename  file is regular file and exist"
else
echo "file is not regular file or doesn't exist "
fi

```

**Check file is directory/folder  and exist**
```bash
if [ -e $filename ]
then
echo "$filename  is a folder/directory and exist"
else
echo "file is not a folder/directory or doesn't exist"
fi
```
*NOTE: folder/directory is also a type of file called directory file ,contain references to other files or directories that help organize the file system into a hierarchy.*

**Check file is block special file  and exist**
```bash
if [ -b $filename ]
then
echo "$filename  is a block-special file and exist"
else
echo "file is not block-special file or doesn't exist"
fi
```
**Check file is character special file  and exist**
```bash
if [ -c $filename ]
then
echo "$filename  is a character-special file and exist"
else
echo "file is not a character-special file or doesn't exist"
fi
```

-r , -w , -x for check read , write , exicute permission



### Write in file
**Overwrite**
`cat > hello.txt`

**Append**
``cat >> hello.txt``

*NOTE: crt + d for save and quit, crt + c for quit only not save.

### Read file
**way 1**
```bash
cat file.txt | while read p 
do
  echo $p
done
```
**way2**
```bash
while IFS=' ' read -r line
do
  echo $line
done  < file.txt
```
**good way (using IFS=' ')**
```bash
while IFS=' ' read -r line
do
  echo $line
done  < file.txt
```

**using file descriptor** 





### Processor ID
- `echo $$` => print processor ID
- `kill processor_id` => to kill process


### Signals and Traps
In Bash scripting, **signals** and **traps** are essential tools for handling unexpected events and ensuring script stability. Here’s an overview:
**Signals**
Signals are notifications sent to a process to notify it of specific events, like a request to terminate. Common signals include:
- **SIGINT** (`2`): Triggered when pressing `Ctrl + C`, typically used to interrupt a process.
- **SIGTERM** (`15`): The default signal for terminating a process gracefully.
- **SIGKILL** (`9`): Forces process termination without cleanup.
- **SIGHUP** (`1`): Often sent to a process when its controlling terminal is closed.

**Traps**
A **trap** is a command in a shell script that catches a signal and executes a specific command or set of commands. Traps are useful for handling cleanup tasks, like deleting temporary files, logging, or gracefully shutting down. Here’s the basic syntax:
`trap "commands" SIGNAL`
For example, to trap the SIGINT signal and perform cleanup when a script is interrupted, you could use:
```bash
#!/bin/bash 
trap "echo 'Caught SIGINT signal'; exit" SIGINT 
echo "Press Ctrl+C to interrupt" 
while true;
do
sleep 1
done`
```

- remove trap list 

### Debugging 
THREE WAY
1. **Use `PS4` for Customized Debug Output**
- Set `PS4` to include additional information when debugging. It’s useful for large scripts.
- Example:
   ```bash
   bash -x script.sh
   ```

2. **Using -x with  #!/bin/bash**
```bash
#!bin/bash -x
....
```

3. **Using `set -x` and `set +x`**
- `set -x`: Turns on debugging, showing each command and its expanded arguments as they are executed.
- `set +x`: Turns off debugging.
- Example:
```bash 
set -x
 # Commands to debug
set +x
 ```

OTHER OPTIONS
  **Use the `-v` and `-n` Options**
- `bash -v script.sh`: Prints each line as it reads it (useful to see the structure and flow of your script).
- `bash -n script.sh`: Checks for syntax errors without executing the script.

 **Using the `trap` Command**
- `trap 'commands' SIGNAL`: Executes specified commands when a particular signal is received. For debugging, `trap 'echo "Error at line $LINENO"' ERR` is useful.
- Example:
- `trap 'echo "Error on line $LINENO"' ERR`
    
 **Debugging Functions with `declare -f`**
- Use `declare -f function_name` to display the definition of a function, making it easier to inspect functions without executing them.

 **Using `ERR` Exit Traps**
- Setting `trap` on `ERR` can help catch errors and print messages when the script exits with an error.
- Example:
    `trap 'echo "Error at line $LINENO"; exit 1' ERR`
    

