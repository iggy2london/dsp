# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

*command --help = help with that command
* show current working directory path
pwd
* move to directory 
cd ../folder (has to be only 1 up)
* creating a directory
mkdir
* deleting a directory
rm -r or rm dir/* (deletes directory and all subfolders)
* creating a file using `touch` command
touch + file name (can create in dir your not in by using touch dirname/filename.txt)
* deleting a file
rm
* renaming a file
* listing hidden files
ls -a (shows files with dots which are otherwise hidden)
ls -t ordered by time modified
ls -l written in long format
* copying a file from one directory to another
cp file_name directory
cp file_name1 file_name2 = overwrite filename2 with filename1
cp * = copy all
CP m* copying everything starting with m
mv file folder = moving file to folder
mv filename1 filename2 = replace name of filename1 with filename2

ls - l header meanings
Access rights. These are actions that are permitted on a file or directory.
Number of hard links. This number counts the number of child directories and files. This number includes the parent directory link (..) and current directory link (.).
The username of the file's owner. Here the username is cc.
The name of the group that owns the file. Here the group name is eng.
The size of the file in bytes.
The date & time that the file was last modified.
The name of the file or directory.

standard input, abbreviated as stdin, is information inputted into the terminal through the keyboard or input device.
standard output, abbreviated as stdout, is the information outputted after a process is run.
standard error, abbreviated as stderr, is an error message outputted by a failed process.

echo "word" > file.txt = redirect word to file
cat file.txt = read string

cat file1.txt > file2.txt copy output of cat file1.txt to overwrite file2.txt
cat file1.txt >> file2.txt ADD rather than overwrite
| pipe standard output to something
> redirect

wc = word count (lines words charachters)

cat < filename.txt = redirect filname as standard input for cat

by default, programs get assigned stdin, stdout, stderr streams.

stdin is the standard input stream. When you do anycommand < x.txt , that attaches x.txt to the stdin stream. It sends everything in x.txt to anycommand as if you were typing it at the terminal, with stdin attached to the terminal.

stdout is the standard output stream. When you do anycommand > y.txt, it attaches y.txt to stdout, sends all the output from anycommand to y.txt .

(we'll skip stderr for now).

When you do command1 | command2 , it attaches the output stream from command1 to the input stream for command2.

cat just sends its input stream unchanged to its output stream. So wc < x.txt does exactly the same as  cat x.txt | wc  …just a case of, there is more than one way to do it!

unique - sorts adjacent duplicates therefore sort first then find unique

grep is case sensitive
grep -i non case sensitive

searching
R - filenames and lines in file
Rl - only filenames
. = current directory

history = history of commands

stream editor = find and replace = sed 's/find/replace/g'

g means replace globally otherwise only first instance


nano(or vim whatever) ~/.bash_profile open your environment which is in ~ = user's home directory and . = hidden directory
source nano ~/.bash_profile (saved changes to environment and insttantly appies w/o needing restart)

save alias ... alias = "string for command"
enviromental variable e.g

export USER = "Your Name"
echo $USER will export your name numst use $ for variables

PS1=">> " changes command prompt
The HOME variable is an environment variable that displays the path of the home directory. Here by typing echo $HOME
echo $PATH shows directories with scripts in them separated by semi colon
when you run a command it usuallt comes from a script which comes from bin directory
cd ~ = cd to home directory

env lists enviromental variables
can grep env 


### Q2.  List Files in Unix   

What do the following commands do:  
`ls`
list contents of directory
`ls -a`
include hidden
`ls -l`
detailed list with other info
`ls -lh`
human readable format
`ls -lah`
`ls -t`
list by order modified
`ls -r`
reverse
`ls -Glp` 
-g means same as -l w/o the name of the owner


### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

ls -l
ls -a
ls -c
ls -m
ls -t

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

xargs converts input from standard input into arguments to a command.

Some commands such as grep and awk can take input either as command-line arguments or from the standard input. However, others such as cp and echo can only take input as arguments, which is why xargs is necessary.

Example
One use case of the xargs command is to remove a list of files using the rm command

rm /path/*
or

rm $(find /path -type f)
This can be rewritten using the xargs command to break the list of arguments into sublists small enough to be acceptable:

find /path -type f -print | xargs rm

