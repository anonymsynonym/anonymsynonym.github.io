---
layout: default
---

## KIK-LG219

I took the elective online course KIK-LG219 Commandline tools for linguis (5 cd.) as a part of my studies in language technology in autumn 2020. The purpose of the course was to learn basic tools for the Unix command-line. The command-line environment is a quicker and more powerful alternative to graphical interfaces for handling files and directories. It can be used, for example, to run scripts on multiple files, to process and extract corpus data, and to share and work on a project between multiple users. Each of the 7 weeks of the course introduced a new topic and a set of new commands, starting from the very basics.

The course material was quite clear and easy to understand. Practicing through the exercises and testing every command on my own command-line shell helped me understand the topics. The most difficulties that I had were with the setup of different programs. Many of the programs would not work at first and needed additional prerequisite programs or alternative program versions to be installed. These possible problems weren't usually tackled in the course material, but luckily fixes for most of them could be found on Google.

_Here's the local repository of this website on the Unix command-line interface:_

![Command-line interface](\assets\img\bash.jpg)

_Here's the local repository of this website on the Windows 10 visual interface:_

![Visual interface](\assets\img\visual.jpg)

### Week 1: Introduction to Command Line Environments

The introductory lecture described in short the theory behind how information in computers is stored, what programming is, what operating systems are and how they work, and what is the idea behind Unix.

The exercises started with setting up the command-line environment. As I am using Windows 10, I needed to first enable the Windows Subsystem for Linux in my settings and then install a working version of Ubuntu Bash Shell.

This week introduced the most basic commands that are used to rename, copy, remove, fetch, etc. files and directories and to move between them. I also learned how to view text files and how to edit them with `emacs`. As the Emacs text editor is not set up by default, the program first needed to be installed. For this, we were introduced the command `sudo apt-get install`.

Possibly the most useful and eye-opening thing that I learned was how to use tab completion, which massively sped up my process of writing commands.

Here's a made-up example, demonstrating this week's most important commands:

```
$ whoami
$ pwd
$ wget https://www.madeupwebsite.com/1234.txt
$ less 1234.txt
$ mv 1234.txt file.txt
$ cat file.txt
$ mkdir folder
$ cp file.txt folder/copy.txt
$ rm file.txt
$ ls -a
$ cd folder/
```

Here's what the commands above do:

1. Prints username.
2. Prints working directory.
3. Downloads a (plain text) file to your working directory.
4. Views the content of the downloaded file with `less`.
5. Renames the file.
6. Views the content of the file with `cat`.
7. Creates a new subdirectory.
8. Copies the file to the subdirectory.
9. Removes the original file from the working directory.
10. Lists all (including hidden) files and directories in the working directory.
11. Changes into the subdirectory.

### Week 2: Navigating a UNIX System

During the second week we looked a bit more at the file system in Unix – what directories there are, and how directories are copied, moved and deleted if they have files inside them.

Last week we learned to copy files. If I wanted to copy the whole directory that we created in the previous example, including the copy of the text file inside it, we need to add the parameter `-R` to specify that the directory is copied recursively, i.e. together with its contents. This is illustrated in the next example:

```
$ cd ..
$ cp -R folder/ new_folder
```

The first command changes me back into the working directory that I started from. The second command copies the directory and its contents into a new directory. The need for `-R` goes also for removing directories with files inside them. The command `rmdir` can only delete empty directories.

This week's material explained what processes are and how to manage them. I learned how to look up the list of running processes, how to switch between processes and move them to the background, and how to use processes' IDs to kill them.

Lastly, we were taught how we can use remote servers, such as Helsinki University's Puhti server, when working from the command-line shell. I, however, did not find this information very useful, as apart from this week's exercises, we never used the same remote servers again on this course. This didn't really demonstrate the different applications or benefits of remote servers, which made the information that we got appear incomplete. 

### Week 3: Basic Corpus Processing

During the third week we practiced regular expressions. The exercises were about clearing up files and finding simple corpus information with `grep` and `egrep`. This wasn't too difficult, as I had already used regular expressions on a couple of other courses. The formatted cvs text files were also familiar to me from a previous Python programming course.

I learned the commands `sort` and `uniq`. The former sorts lines of text in a file alphabetically, and the latter deletes the extra instances of a line if it appeares multiple times consecutively. These proved to be very useful during the next weeks, as they can be used for example to extract word or phrase frequences from corpus data. The command `tr` is also useful in this, as it allows us to change or delete characters in a string.

I learned more about the Bash shell's syntax as we begun using the characters \| and \> (piping commands and redirecting into a file).

As an example, the following code would search the text file from the previous examples only for whole numbers (consisting of either one or multiple digits), list each of them on its own line, sort the lines of numbers from largest to smallest, remove multiple instances of the same number and redirect the result into a new text file inside the same folder.

```
$ egrep -o '\b[0-9]+\b' folder/copy.txt | sort -nr | uniq > folder/copy_numbers.txt 
```

We also looked into the theory behind different character encoding systems and learned to convert files between them. At first I hade quite a lot of trouble getting the UTF-8 character encoding to work but finally managed to fix the issues with the Finnish ä:s and ö:s. After all that work it was a bit of a shame that the rest of the text files on following weeks only featured text in English.

### Week 4: Advanced Corpus Processing

The fourth week continued where the third week left off as we practiced more regular expressions and text file processing. Most importantly, we were introduced to the command `sed` which can be used to manipulate text even more powerfully than `tr`. With `sed`, we can search for specific pattern of text using regular expressions and manipulate the patters, for exaple removing them, changing their order, multiplying them or substituting them with new strings.

As an example, the following code would search the afformentioned text file for all whole numbers with exactly two digis, flip the order of the digits and write the whole text file, including the changed numbers, into a new text file. 

```
$ sed -E 's/(\b([0-9])([0-9])\b)/\2\1/g' folder/copy.txt > folder/copy_flipped.txt
```

In this week's exercises we created frequency lists of tokens in a text file and looked into data about n-grams. I found this interesting and useful to learn, as I have previously only worked with word frequencies and n-grams in separate programs, namely AntConc. Using these commands together with next weeks' scripts and makefiles seems to be quite an efficient way to collect corpus statistics from a bulk of files. Though, I think that the benefits of these command line tools tend to only appear when operating with a large amount or size of text files, as searching the same corpus information from just one file would probably be done quicker in an existing program than with bash commands. 

### Week 5: Scripting and Configuration Files

During the fifth week we learned to write series of commands (pipelines) into scripts that can then be readily called from different directories to perform the different commands without having to write them out every time. Along with the scripts, we learned to use Bash syntax for for-loops and conditional if-statements. We also learned to use variables: `$#` tells the number of parameters, `$1` and `$2` can be used for the input and output files, and `$?` holds the exit code of of the last process, telling whether it was completed correctly or ended in an error. The `$` sign can also be used to create and refer to our own variables, and those variables are used similarly to other programming languages that I have experience with. 

We also looked into environment variables that affect how the Unix shell works, and Bash configuration files that can be used to set environment variables permanently, and to for example save a variety of settings and customizations. During the exercises I used the `~/.bashrc` configuration file to save shortcuts and to change the visual appearance of my command-line shell. It is easy to imagine how it can be useful and time-saving to be able to decide what information (time, directories, servers, etc.) is presented on the command-line shell and how it is presented (spacing, informative colours, etc.).

Probably the most important command that I learned this week relates to changing the `$PATH` variable that tells the shell which directories it should search through when, for example, running scripts. To permanently add a new path to the variable, a command similar to the following should be added into the `~/.bashrc` configuration file:

```
export PATH=$PATH:/madeupdirectory/folder
```

When the configuration file is sourced, either by running the `source` command or by opening a new shell, this command edits the `$PATH` variable to include the directory `/madeupdirectory/folder/` that can contain, for example, one or multiple shell script files.

### Week 6: Installing and Running Programs

Week 6 started with information about the root user and the root privileges needed to run certain commands. We can switch into and from the root user by using the command `su`. Commands can also be run individually using the `sudo` command that was already introduced and used during previous weeks while installing different programs. We looked into installing programs with `apt-get` and locating their files and directories in the system with `locate` or less ideally with `find` and `grep`. We also experimented with `pip`, a packet manager specifically for installing Python programs, and with Python virtual environments that allow managing different Python installations with their own settings at the same time.

Lastly, we were taught about `make` that can be used to automate the running of multiple scripts or programs in order to build a project such as a more complicated program or a directory containing for example specific data from corpora. Usually this involves a so-called makefile that includes the instructions, written in specific syntax, for `make` to compile the wanted program. If the makefile has been run before and there have been some partial changes to it, make only needs to compile the files and directories that have not yet been created.

A very simple example of makefile syntax:

```
folder/copy_flipped.txt: folder/copy.txt
    sed -E 's/(\b([0-9])([0-9])\b)/\2\1/g' $< > $@
```

This make rule performs the same command as my Week 4 example on flipping two-digit numbers. It has the target (i.e. "output file") `folder/copy_flipped.txt` (also referred to with `$@`) and the dependency (i.e. "input file") `folder/copy.txt` (also referred to with `$<`). The syntax recquires the system command to be indented. In this case, the system command is the previous sed command, and its output is redirected to the target.

To me, `make` seems particularly useful for processing large amounts of corpus data, as that is the kind of information that I will most likely be examining during my studies and possible career in linguistics. I hope that these tools will be of use.

### Week 7: Version Control

The final week, along with the final assignment of the course, had to do with `git`, GitHub and version control. Version control refers to a system where multiple versions of files with different levels of changes are saved so that the user can easily move between the versions, revert to a previous one or replace it with some parallel branch of changes. `git` makes possible the moving and saving of files between a local repository and an online server with the same project. GitHub is a service, available for free, that allows people to share and work on open-source projects over the internet.

A simple example of pushing new local changes (commits) on a remote server:

```
$ git add -A
$ git commit -m 'Some explanatory message'
$ git push
```

Explanation of the commands:

1. Adds the entire working tree (all changed files) to the index, i.e. redies them to be committed.
2. Records the added changes to the repository, along with a short message describing the changes.
3. Uploads the local repository content to a remote repository.

GitHub also offers a possibility to host websites. This was utilised in the final assignment where my job was to create my own website using an existing template on GitHub, customise it with my own information, and write a summary of the contents and coursework of this course (as seen here). The assignment also recquired the use of Jekyll, a tool that allowed me to view and test versions of the website locally without having to push all of the unfinished changes to the remote repository and the actual website.

### Introduced Commands (and Syntax)

The table below is scrollable.

<div class="table-wrapper" markdown="block">

| Week&nbsp;1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Week&nbsp;&nbsp;2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Week&nbsp;3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Week&nbsp;&nbsp;4&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Week&nbsp;5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Week&nbsp;6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Week&nbsp;7&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
| --------------- | -------- | ------------ | -------- | --------- | ------------------ | ------------------------ |
| apt-get install | CTRL+Z   | cut          | diff     | alias     | apt-cache search   | git --version            |
| apt-get update  | chmod    | dos2unix     | sed      | chmod u+x | deactivate         | git add                  |
| cat             | chmod -R | echo $LC_ALL | sed -E   | export    | locate             | git add -A               |
| cat -n          | cp -R    | egrep        | sed -n   | for       | make               | git branch               |
| cd              | fg       | egrep -f     | sed //d  | if        | make all           | git branch --merged      |
| cp              | kill     | egrep -w     | sed //p  | nano      | make clean         | git branch -a            |
| echo            | killall  | file         | sed s//g | printenv  | meld               | git branch -d            |
| emacs           | ls -a    | grep         | sort -n  | source    | passwd             | git checkout             |
| less            | ls -l    | grep -E      | sort -r  | $#        | pip                | git clone                |
| ls              | man      | head         | tr -c    | $?        | pip install        | git commit -m            |
| mkdir           | ps       | head -n      | tr -d    |           | pip install --user | git config               |
| mv              | rm -R    | iconv        | tr -s    |           | pip3 install       | git diff                 |
| mv -n           | rmdir    | locale-gen   | uniq -c  |           | python             | git init                 |
| pwd             | scp      | paste        |          |           | python -m venv     | git log                  |
| rm              | sleep    | tail         |          |           | python3            | git pull                 |
| touch           | sort     | tail -n      |          |           | source             | git push                 |
| tar -czvf       | ssh      | tr           |          |           | su                 | git push -u origin       |
| whoami          | top      | tr -d        |          |           | sudo               | git push origin --delete |
| wget            | which    | uniq         |          |           |                    | git reflog               |
| wget -h         | &        | unix2dos     |          |           |                    | git remote -v            |
| wget -q         |          | wc           |          |           |                    | git reset                |
|                 |          | wc -l        |          |           |                    | git reset --hard         |
|                 |          | \>           |          |           |                    | git status               |
|                 |          | 2\>          |          |           |                    |                          |
|                 |          | \|           |          |           |                    |                          |

</div>
