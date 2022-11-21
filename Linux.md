## echo string
print a string on terminal

## 4 famous shells on linux
zsh, fish, bash, sh

bash is default in ubunto

## echo $SHELL
print active shell on your os

## Directory    
cd = change directory

pwd = print working directroy

cd <absolute_path>

cd <relative_path>

cd /: go to root directory

cd ~: go to /home/username directory

when you open terminal you are in /home/username directory

## Linux command structure
COMMAND [OPTIONS] [ARGUMENTS]

each part is case sensitive // for example ls is different with Ls

pwd --help	// cmd --option

help pwd	// cmd argument

## ls cmd
`ls`: list files and directories

-a show all files include hidden files (like .. .)

-t sort files by <modification_time>

-l show file details

-r change sort direction to desc

-R list recursively (list all files in sub-directories too)

-h show file size in human **readable form**

`ls -ltrh` is very useful

Hard link in linux is like shortcut in windows

How to make hardlink: `ln FILE_PATH NEW_FILE_PATH`

## ubunto terminal tricks
`ctrl + alt + T`: open terminal

`ctrl + shift + T`: open new tab

`ctrl + PgUp` & `ctrl + PgDn`: swith active tabs

`ctrl + L`: clear

`history <count>`: show history commands

`history -c`: delete history

## working with directories
`mkdir a b c` : make 3 directories

`mkdir name{1..5}`: make 5 files from name1 to name5

`mkdir my\ dir` or `mkdir 'my dir'` : make directory **inculding space** in name

`mkdir -p mydir/insideDir` : make **nested** directories

`rmdir a`: remove directory if it is empty

`rmdir -p a/b/c`: if you want to remove a dir and it's content

`rm <dir-name> -r` or `-R` or `--recursiveß` : remove directories and their contents recursively

`rm -f` or `--force`: ignore nonexistent files and arguments, never prompt

## working with files
`touch a.txt b.txt c.txt` : create 3 files

`touch 'a example.txt'` or `a\ example.txt` : create a file with include space in it's name

`cat <file-name.ext>`: show file content

`cat -n`: show line numbers

`cat -b`: show line numbers and remove empty lines

`cat > a.txt` : you can write in a.txt file and `ctrl + d` to save and exit

`cat << EOF > b.txt`: you can write in b.txt file and type EOF and press enter to save and exit

## cp mv rm
`cp <first_path> <second_path>`: copy file

cp -r <first_dir_path> <second_dir_path>`: copy directory with all contents

`cp -v`: show every file copy log

`mv <first_path> <second_path>`: move file or directory, mv also use for **rename**

`rm <file_name>`: remove file

`rm -r <dir_path>`: remove directory with all contents

## command guides
1. `cmd --help`

2. `info cmd`: press q to exit

3. `man cmd`: press q to exit	best choice

options

1. short format like ls -a

2. long format like ls --all

you can use multi short format option in combination like -ltrh

## date & cal
`date`: get current date_time

`date -u`: get current date_time in UTC

Many formats was explained in quera

`date "+%Y-%m-%d"`: date format sample 2022-06-27

get past date_times

`date --date="2 year ago"`: get two years ago date_time

`date --date="5 sec ago"`

`date --date="yesterday"`

`date --date="2 month ago"`

`date --set="Tue Nov 13 15:23:34 PDT 2018"`: set system time **danger**

`cal`: get current month calender

`cal -y`: get current year calender

`cal -A 2 -B 2`: get current month plus 2 months before and 2 months after

`cal 02 2002`: get a specific month

## Standard streams
standard input - stdin - 0

standard output - stdout - 1

standard error - stderr - 2

## Standard streams 2 (redirection)
command > output.txt: redirect a command output to a file (overwrite prev content)

example: echo "Hello from Amir" > file.txt

`command >> output.txt`: append to file

`command > `: stdout

`command 2>` : stderr

`command &>` : stdout & stderr


`command < input.txt`: put a file content as input of a command

example: `wc < file-new.txt` : // example response:  4  4 22

`wc <file_name.ext>`: show lines, words, characters of that file

when you want to use a multi_line input for a command
```
command << MARKER
line 1
line 2
MARKER
```

when you want to add multi_line in a file, you can do this, this way
```
cat <<EOF > data.txt
hello guys
linux is so powerful
goodbye
EOF
```

## Pipelines
cmd 1 - STDOUT -> STDIN cmd 2

`command1 | command2 | command3 | ... | commandn`

example: 
```
cat <<EOF | sort
hello
from
alireza
in quera
to
you
EOF
```

-> sort all words

`whoami`: show username

echo "My account name is $(whoami)." -> My account name is Amir.

## du & file commands
`du <absolute_or_relative_path>`: show all sub **directories** sizes **disk usage** 

`du -h, --human-readable`: **human readable** sizes

`du -s, --summarize`: show only current directory size

`du -a, --all`: show sub **directories and files** sizes

`du -c, --total`: append total size to result

`du --time`: add last-update-time of each directory to result


`file <file_name>`: show **file-type and some file details**

`file <file_name> -b`: show only **file type**

file extention is not important in linux. That is why file command is for.

How you can **put a content in a file with cat** command:

`cat > file_name` -> type content -> press enter -> press `ctrl + d` to save and exit

## vim and nano editor
`vim <file_name>`: open file with vim editor

vim has two mode:

1. press i to active insert mode

2. press ESC to active normal mode

`:w` -> save

`:q` -> quit

`nano <file_name>`: create and open file_name and you can edit file like notepad.

## linux main directories
`which <command_name>`: show executive file path for command_name

## more & less : show long files or show other long command results
`more <file_name>`: show first page of file

press `enter`: show next line

press `space`: show next page

press `b` or `crtl b`: prev page

press `=`: show line number

`more +50 <file_name>`: show file from line 51

`less <file_name>`: show first page of file

press `enter`: show next line

press `space`: show next page

press `b` or `crtl b`: prev page

press `=`: show some file details

press `g`: show first page

press `G`: show last page

`:50` press enter: go to 50 lines later

`:50n` : go to line 50

`/<word>`: find word in file

`less -N`: show file with line numbers

`less -s`: change multi empty line to one empty line

You can redirect an stdout to less command, like below:

`ps aux | less`

one of useful usages is below: for show part of command result instead of all command result

`find / -name "*.log" | less`

## head & tail
`head <file_name>`: show 10 first lines

`head -c 20 <file_name>`: show 20 first characters

`head -n 20 <file_name>` or `head -20 <file_name>`: show 20 first lines

`tail <file_name>`: show 10 last lines

`tail -c 20 <file_name>`: show 20 last characters

`tail -n 20 <file_name>` or `tail -20 <file_name>`: show 20 last characters

`tail +20 <file_name>`: show lines equal & after line 20

How to show lines 21 - 50:

`cat <file_name> | head -50 | tail +21`

or

`cat <file_name> | head -50 | tail -30`

## cut: cut some parts of text from a file

`cut -b 1,2,5 <file_name>`: show only first, second and fifth characters of each line

`cut -b 1-3 <file_name> - cut -b **start-end** <file_name>`: show first to third characters of each line

`cut -b 7- <file_name>`: show seventh character to end of each line

`cut -b -7 <file_name>`: show start of line to seventh character of each line

`cut -d "," -f 1,4 <file_name>`: show only first and fourth column of each line that is seperated with comma

`cut -d "," -f 1,4 --output-delimiter='*' <file_name>`: replace , with * in output

## wc & sort
`wc <file_name>`: show **number of lines, words and characters** of the file

`wc -l`: only lines

`wc -w`: only words

`wc -m`: only characters

`wc -c`: only bytes

sort <file_name>: sort lines of a file

sort command priroity: numbers > small letters > capital letters

sort -r: sort reversly (desc)

sort: **character base** - 05 is prior than 2 - 10 is prior than 8

sort -n: **numeric base** - 2 is prior than 05 - 8 is prior than 10

how to sort with second column:
```
sort -k 2 << EOF
ali 1
reza	8
mammad 5
arshia		7
soltani	10
EOF
```
sort -k: recognizes columnes with white space

## grep
grep string <file_name>: find string in file_name

grep -i: case-insensitive

grep -v string <file_name>: show all lines without string

grep -n: show result with line numbers

grep -c: show count of results

grep -w am <file_name>: shows **am** but does not show **am**ir - shows exactly the word not part of a word

grep -C 2 string <file_name>: shows results with 2 lines up and down

use grep with regex:

`grep -E "l[a-z]*x" <file_name>`

show lines that have string1 **OR** string2

grep 'string1\|string2' <file_name>

grep -e string1 -e string2 <file_name>

grep -E 'string1|string2' <file_name>

grep is available in pipeline

## find
tree <directory>: show tree structure of the directory

find <directory>/ -name <file_name>: find all matching file_names in directory

find <directory>/ **-iname** <file_name>: find **case-insensitive**

find <directory>/ -name <file_name> **-type d**: find only **directroies**

find **-type f**: only **files**

find -empty: only empty files or directories

find -not -empty: only not empty files or directories

find -name "*.txt": find all files that ends with txt

find -maxdepth 2 or -mindepth 2: restrict depth

find **.** -name <file_name>: find from **current_directory**

## Wildcards
you can replace "*" with 0 or more than 0 characters

you can replace "?" with only 1 character

you can replace "[adfm]" with only one character of these

### brace expansion

`touch a{1..200}.txt`: create 200 files with certian range - availble ranges like {a..z} - {A..Z} - {01..20} - {1..20}

## find (part 2)
find . -name <file_name> -size -1M -size +5M: find all files with size between 1 and 5 MB

c: byte k: kilobyte M: megabyte G: gigabyte

find cmd has two part: search & operation - default operation is -print

**exec** option structor: -exec <cmd> <place_holder> {} <separator> \; or +

you can use multi placeholders if needed

You can use special operation on find results with **-exec** option

find and delete some files

find . -name "*.txt" -exec rm -i {} \; executes separate rm cmd for each result

find . -name "*.txt" -exec rm -i {} +  executes all rm operations in one cmd

-i option: ask confirmation before every file rm

more examples for -exec operations

find . -name "*.txt" -exec grep 'hello' {} \;

find . -name "*.txt" -exec cat {} \;

find . -perm 644: find all files with special permission

How to delete find results

find . -name "*.txt" -exec rm -i {} \; executes separate rm cmd for each result

find . -name "*.txt" -delete

How to make a info.txt file in each directories with 'make' name

find . -type d -name make -exec touch **{}/info.txt** \;

## comprss and archive files
cat /dev/random | tr -dc "[:alpha:]" | head -c 100M > largefile: generate a random large file

**gzip** largefile: compress only one file with **.gz** suffix

gunzip largefile.gz: de compress gzip file

**bzip2** largefile: compress only one file with **.bz2** suffix | usually takes more time 
but more compress than gzip

bunzip2 largefile.bz2

**tar** -cvf archive.tar file{3..10} folder{1..2}: **archive** specific files and folders - with .tar suffix

-c: say that we want to archive

-v: print result

-f: choose file_name

tar -tf archive.tar : show archived file content without unarchive that

you can compress archived files, for example with gzip

tar -xvf archive.tar: unarchive .tar file

-x: to say that we want to unarchive file

**tar -zcvf** archive.tar.gz file{3..10} folder{1..2}: **archive and compress** - we add .gz suffix for file name to remember that it is compressed too.

**tar -zxvf** archive.tar.gz: **de-compress and unarchive**

how to attach some files or directories to an archive without urarchive this

tar --append file1 file2 dir1 --file=backup.tar

tar -rf backup.tar file1 file2 dir1


## awk - for table-like files (with free space (tab or space))
awk '{action}' my_file

awk '{print **$1**}' <file_name>: print only **column1** from <file_name>
awk '{print $1, $2}' awk_file.txt: print column1 & column2

awk '{print **$NF**}' awk_file.txt: print **last column**

use regex in awk:

awk '**/regex pattern/**{action}' my_file

awk '/of/{print $1, $3}' awk_file.txt

awk **-F**\- '{print $1" "$2" "$3}' data.txt: separate column with specific character. like '-' | -F option could help us

awk 'BEGIN {print "users \n --------"} {print $1,$2} END {print "finished"}' awk.txt : print words at the begining and end of result

awk '**$3 > 25** {print $1, $2, $3}' awk.txt: show only rows with column3 that is **greater than** 25

awk '**$3 == 25** {print $1, $2, $3}' awk.txt: show only rows with column3 this is **equal** to 25

awk '{print $1,$2,$3} {sum+=$3;} END {print sum}' <file_name>: add **sum** of a column to end of result 

## users & groups in linux
each user has these attributes: Username, User ID (UID), Password, Primary Group (GID), Location of the Home Directory, Default Shell

for each user, we have 1 line is /etc/passwd file

the users password hash exists in etc/shadow/ file

whoami: shows your user_name

id: shows UID, GID & all your groups id

## Add users and groups
How to **Add user**:

1. sudo useradd -m -c "Alireza Temporary User" -s /bin/bash alireza

-m: create home directory for user

-c: add comment for user

-s: set default bash for user

sudo passwd alireza: set password for user

2. sudo adduser alireza: and go on steps (all steps are optional except password)

su - <user_name>: login as user

id <user_name>: show UID, GID and groups for user

how to **add group**:

1. sudo addgroup <group_name>

2. sudo groupadd <group_name>

sudo **usermod**: **modify** a user profile

sudo usermod -a -G <group_name> <user_name>: Append group_name to user's group

-a: append group to user existing, not replace

sudo deluser --remove-home <user_name>: delete user with it's home directory

sudo delgroup <group_name>: delete group

sudo kill -9 <process_number>: **kill a process**

## su & sudo
su - : (substitute user) - login as **root**

su - <user_name>: login as <user_name>

type **exit** or **ctrl + d**: To return to your primary user shell

su options: 

-c --command: execute a command without login

-l --login -: login as user

-s --shell: select custom shell

sudo <cmd>: execute a command with root permission without login

## permissions
-|rwx|rwx|---

First part indecates file or dir: - for file | d for directory

Second part indecates *owner* permission | u (user)

Third part indecates *group* permission | g (group)

Fourth part indecates *all other* permission | o (other)

a means all (ugo)

- r : read : 4
- w : write : 2
- x : executable : 1

## chmod & chown
sudo chown <NEW_USER>:<NEW_GROUP> file : change group & user owner
sudo chown user1:user1 /home/transferred-file : example

sudo chmod <OPTIONS> [ugoa…][-+=]perms…[,…] <file_name> : change permission

how to change file permissions

1. chmod o+w <file_name>: example

    +: add permission to existing permissions

    -: remove permission from existing permissions

    =: update all permissions

2. chmod 666 <file_name>

## apt : Advanced Packaging Tool - apt is a package manager
sudo apt update: updates the list of available packages and their versions, **but it does not install or upgrade any packages.**


sudo apt upgrade: **actually installs newer versions** of the packages you have

apt-get update && apt-get upgrade: to **do both steps** after each other.

sudo apt search <package_name>: search a package

sudo apt install <package_name>: install a package

zsh: you can change shell to zsh

exit: exit from zsh and swith to default shell (bash) again

sudo apt remove <package_name>: remove a package

sudo apt autoremove: remove unuesed dependencies. (it can be useful after remove a package and sometimes it can also be risky!)

## writing script
you can write script in many languages like bash, ruby, python ...

write a hello world! script in 3 steps:

1. Make the script file:
```
cat << EOF > hello.sh
#! /bin/bash
clear
echo hello world!
EOF
```

2. `chmod +x hello.sh`: make it executable

3. `./hello.sh`: execute the script

Shebang: like **#! /usr/bin/python3** or **#! /bin/bash**: indecates script interpreter (shebang must be on first line)

each line in script translates to a process in running time

## Variables in bash
#! /bin/bash

target=quera : **define a variable**

echo hello **$target**: prints hello quera in the terminal

How to pass arguments to bash:

`./hello.sh Ali($1) Amir($2)`
```
#! /bin/bash
echo "$1 says hello to $2."
```
If you don't pass a used argument, you don't get an error. just the variable replace with empty string ""

specific variables:
1. $0: running script name
2. $1-$9: first 9 arguments
3. $#: count of arguments
4. $*: string of all variables separated with space
5. $@: array of all variables
6. $?: exit code or last process result
7. $$: this script process id
8. $!: last process id that is running in the background

example of math operations in bash
```
#!/bin/bash
# gouss law
for i in {0..10}
do
  sum=$((sum+i))
done

echo sum of first 10 integers are: $sum
echo sum of first 10 integers are: $(((10+0)*11/2))
```
You can pass a cmd result as variable to a script like below:

`./hello.sh $(whoami)`

## Arrays & Hashmaps
How to define an array:
1. a1=(1 2 3 4 5 6 7)
2. declare -a a2

a2+=(ArshiA Alireza)

a2+=(SAliB) 

How to define a hashmap: hashmap is like associative array in php
1. declare -A hm

hm=([che]=shekufe [delnavaz]=riz [umadam]=umadam)

hm+=([amma]=amma [ba]=che [naz]=dir [umadam]=umadam)

echo **${a2[@]}**: print the whole array or hashmap

echo **${a2[*]}**: print the whole array or hashmap

a1[0]=tahmures: you can change or append an index value

echo **${#a1[@]}**: print size of array or hashmap (**count**)

echo **${!a1[@]}**: print the **keys**

**unset** a1[1]

## conditions
**if command exit code == 0 -> execute then command**

if then common syntaxes:
1.
```
if command
then
    commands
fi
```
2.
```
if command; then
    commands
fi
```

if then else syntaxes:
1.
```
if command
then
    commands
else
    commands
fi
```

2.
```
if command; then
    commands
else
    commands
fi
```

if elif else syntax:
```
if command-1; then
    commands-1
elif command-2; then
    commands-2
...
elif command-n; then
    commands-n
else (optional)
    commands-else
fi
```

switch case syntax:
```
case variable in
pattern-1) commands-1;;
pattern-2) commands-2;;
...
pattern-n) commands-n;;
*) default-commands;;
esac
```

## test conditions
man **test**

You can execute conditions with a true|false result except exit code checking

you have 3 type conditions:
1. Numeric Comparisons
2. String Comparisons
3. File Comparisons

test syntax examples:

```
if test_condition
then
    command
else
    other command
fi
```
==========================
```
if [ conditions ]
then
    commands
fi
```
==========================
**And** - **Or** condition

```
if [ condition1 ] && [ condition2 ]
then
   command
fi
```
 You can replace **&&** with **||**

How to get a number from user in a script:
```
!# /bin/bash
echo -n "Enter number:"
```
read number	# as a variable that you can get from user!

## Loops (for & while)
for syntax:
```
for var in **list**
do
    commands
done
```
for examples:
```
for word in "linux" "is" "perfect" "and" "windows?" "mmm," "not" "bad."
do
    echo -n "\$word "
done
```
=======================
get list from a file:
```
for word in \$(cat list)
do
    echo \$word
done
```
=======================
get list from a directory content:
```
for word in $(pwd)/folder/* 
do
    if [ -d \$word ]; then
        echo "\$word is a folder"
    elif [ -f \$word ]; then
        echo "\$word is a file"
fi
done
```
=======================
```
for (( i = 1; i <= 10; i++ ))
do
    echo "Round \$i"
done
```
while syntax:
```
while command
do
    commands
done
```

available keywords in loops:

break: exit from loop

continue: go to next item


## bash parameters
some bash operators:

-n: string is **not null**.

-z: string is null, that is, has **zero length**

**exit**: stop running a script

**shift**: $n after shift goes to $n-1 place

example of shift: echo all parameters with $1 only
```
cat <<EOF > shift.sh
#!/bin/bash
count=1
while [ -n "\$1" ]
do
    echo "Parameter #\$count = \$1"
    count=\$[ \$count + 1 ]
    shift
done
EOF
```

make option from parameter with switch-case: example
```
cat <<EOF > options.sh
#! /bin/bash
OPTION1=false # Boolean Option with default value
OPTION2=hello # Parameter Option with default value

while [ -n "\$1" ]
do
    case "\$1" in
        -o1) echo "OPTION1 entered"
             OPTION1=true
             shift ;;

        -o2 | --option2) echo "OPTION2 entered"
             if [ -z \$2 ]; then
                 echo "Option2 needs a parameter"
                 exit 1
             fi
             OPTION2=\$2
             shift
             shift ;;

         --) shift
             break ;;

          *) echo "\$1 is not an Option"
             exit 1 ;;
    esac
done
echo "Option1: \$OPTION1, Option2: \$OPTION2"
count=1
while [ -n "\$1" ]
do
    echo "Parameter #\$count = \$1"
    count=\$[ \$count + 1 ]
    shift
done
EOF
```

output:

OPTION1 entered

OPTION2 entered

Option1: true, Option2: bye

Parameter #1 = Alireza

Parameter #2 = ArshiA

Parameter #3 = SAliB


## Bash Functions
How to define a function:
```
function greet {
  echo "hello $1"
}
```
How to use this function
`greet Amir`

Result: hello Amir

How to define a local variable in bash: with 'local' keyword.
```
target=garshasb
function greet {
  local target=world
  echo "hello $target"
}
```

In bash it is possible to use a function result as a variable like below:
```
function test_function {
  echo 20
}
echo `test_function`
```

## uname
uname: show os name
- -s: kernel name
- -v: kernel version
- -r: kernel release number
- -a: all os & hardware info

## processes
jobs: show all precesses thoes are running in background on a shell

ps: show all precesses in background

bg <job>: move a job to background

fg <job>: move a job to foreground

## processes
`top`: show all processes with details
`
`htop`: show all processes with better & interactive interface (Is not installed on usual linux distributions)

## piriority & niceness
niceness range is from -20 ------------ 19 | High ----------- Low

priority = niceness + 20

you can run a command and set it's niceness with **nice** & **renice** command like below:

nice -n <nice_value> <command>

renice -n <nice_value> -p <pid>

renice -n <nice_value> -u <user>

super admin access (sudo) is required for:

1.Run a command with 0 or less priority.

2.Renice a process to a lower neceness values

## proccess - ps
ps: show processes those are running on **the shell**

ps options:

-e or -A: show **all running** processes

ps aux: a useful command
1. a: **all running** processes
2. u: more info about **resources consumption**
3. x: show processes those are **not running on shell**

ps auxf: show processes with tree structure

some ps columns:

tty: used terminal type

start: start time

**VSZ** : equal to **VIRT** on htop: using memory in byte

**RSS** : equal to **RES** on htop: using RAM in kilobyte

ps xao uid,pid,ppid,pgid,sid,cmd | head -n 5

uid: user's id who started the process

ppid: parent process id

pgid: process group id

sid: session process id

## Process cycle
### process states:

1.R: Running or Runnable

2.D: Uninterruptible Sleep

3.S: Interruptable Sleep

4.T: Stopped

5.Z: Zombie

**A great man once said: "everything is a file"**

Linux process directroy: **/proc**

show a process directory content: ls /proc/<pid>

show a process command: cat /proc/<pid>/cmdline

show a process status: cat /proc/<pid>/status | grep State

use a process exe file example: 
```
/proc/<pid>/exe << EOF
Quera
EOF
```

ls /proc/<pid>/fd : shows 3 files like 0 1 2 (stdin, stdout, stderr)

## Signals
signals are one_side notification to manage processes.

kill -l: show all linux signals (about 30 signals)

4 more common signals:

1. SIGINT: finish process (ctrl + c)
2. SIGKILL: finish process (force)
3. SIGSTOP: stop process (ctrl + z)
4. SIGCONT: continue stopped process


how to send signals:

- kill -<signal_name> <PID>
- kill -<signal_number> <PID>

or

- killall -<signal_name> <process_name>
- killall -<signal_number> <process_name>

## process managment

jobs: show processes that are running on current shell with a <job_number>

bg %<job_number>: move a job to background

fg %<job_number>: move a job to foreground

kill %<job_number>: SIGKILL  the job

Important: **Ctrl + c (SIGING) & Ctrl + z (SIGSTOP) is does not work for process are running in the background**

## Session & Group in processes
You can send signal to several processes by their <group_id> or <session_id>

If the **process_id = group_id** the process is the **group leader**!

If the **process_id = session_id** the process is the **session leader**!

Each tab in your terminal is a session

jobs: show processes of a session

![Group & session image](https://quera.org/qbox/view/fWwTcXjVza/session.png)

Each session can have several groups.

If you move a process to foreground it means that you have make the process the session leader.

**S+** in (ps x) command means this process is in **foreground**

**T** in (ps x) command means this process is **Terminated**

Send a signal to a group or session like below:

kill -SIGNAL -<PGID> or <SID>

## Daemon processes
These processes are not in control of user. and end with (d) like below examples.

- Crond: job management
- Httpd: for webserver


## SSH
ssh <username>@<remote_host>

Primary server configuration tutorial: https://quera.org/college/8903/chapter/32296/lesson/141944/?comments_page=1&comments_filter=ALL

## Service Management

Runlevel: The status of system after boot (There are 7 different Runlevels)

0 Halt (Turning off)

1 Single-user text mode (Single_user status)

2 Not used (user-definable) (Free - Configurable)

3 Full multi-user text mode (Multi_user status without Graphical_user_interface)

4 Not used (user-definable) (Free - Configurable)

5 Full multi-user graphical mode (with an X-based login screen) (Multi_user status with Graphical_user_interface)

6 Reboot (Restart system)

runlevel: show the runlevel number

chkconfig: show services with theirs runlevels

Linux boot or init methods: <Service_Management_Method>
1. System v (SysVinit) | **service**
2. Upstart | **initctl**
3. Systemd | **systemctl**

### common service commands

`sudo <Service_Management_Method> <service_name> start`

`sudo <Service_Management_Method> <service_name> stop`

`sudo <Service_Management_Method> <service_name> restart`