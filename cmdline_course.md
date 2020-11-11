---
layout: default
---

## KIK-LG219

I took the elective online course KIK-LG219 Commandline tools for linguis (5 cd.) as a part of my studies in language technology in autumn 2020. The purpose of the course was to learn basic tools for the Unix command-line. The command-line environment is a quicker and more powerful alternative to graphical interfaces for handling files and directories. It can be used, for example, to run scripts on multiple files, to process and extract corpus data, and to share and work on a project between multiple users. Each of the 7 weeks of the course introduced a new topic and a set of new commands, starting from the very basics.

The course material was quite clear and easy to understand. Practicing through exercises and testing every command on my own command-line shell helped me understand the topics. The most difficulties that I had were with the setup of different programs. Many of the programs would not work at first and needed additional prerequisite programs or alternative program versions to be installed. These possible problems weren't usually tackled in the course material, but luckily fixes for most of them could be found on Google.

### Week 1: Introduction to Command Line Environments

The introductory lecture described in short the theory behind how information in computers is stored, what programming is, what operating systems are and how they work, and what is the idea behind Unix.

The exercises started with setting up the command-line environment. As I am using Windows 10, I needed to first enable the Windows Subsystem for Linux in my settings and then install a working version of Ubuntu Bash Shell.

This week introduced the most basic commands used to rename, copy, remove, fetch, etc. files and directories and to move between them. I also learned how to view text files and how to edit them with **emacs**. For this, the editor needed first to be installed with `sudo apt-get install emacs25`, which introduced the command for installing programs.

Possibly the most useful and eye-opening thing that I learned was how to use tab completion, which massively speeds up the process of writing commands.

Here's a made-up scenario, demonstrating this week's most important commands:

```
whoami
pwd
wget https://www.madeupwebsite.com/1234.txt
less 1234.txt
mv 1234.txt file.txt
cat file.txt
mkdir folder
cp file.txt folder/copy.txt
rm file.txt
ls -a
cd folder/
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

During the second week we looked a bit more at the file system in Unix – what directories there are and how directories are copied, moved and deleted if they have files inside them. I learned how to look up the list of running processes, how to switch between processes and move them to the background, and how to use processes' IDs to kill them.

Last week we learned to copy files. If I wanted to copy the whole directory that we created in the previous example, including the copy of the text file, we need to add the parameter `-R` to specify that the directory is copied recursively, i.e. together with its contents. This is illustrated in the next example (after moving back to the directory that we started from in the previous example):

```
cd ..
cp -R folder/ new_folder
```

The same also goes for removing directories with files inside them. The command `rmdir` can only delete empty directories.

This week also taught about using remote servers, such as Helsinki University's Puhti server, when working from the commandline-shell. I, however, did not find this information very useful, as apart from this week's exercises, we never used the same remote server again on this course. This didn't really demonstrate the different applications or benefits of remote servers. 

### Week 3: Basic Corpus Processing

During the third week we practiced regular expressions. The exercises were about clearing up files and finding simple corpus information with `grep` and `egrep`. This wasn't too difficult, as I had already used regular expressions on a couple of other courses. The formatted cvs text files were also familiar to me from a previous Python programming course.

During the following weeks, the commands `sort` and `uniq` that sort lines alphabetically and count the instances of unique lines proved to be useful for examining corpus data. 

```
cat folder/text.txt cat li | sed -E 's/.* //' | tr -cd "A-Za-z0-9\n'" | sort | uniq -c | sort -nr | head -1
We also looked into the theory behind different character encoding systems and learned to convert files between them. At first I hade quite a lot of trouble getting the UTF-8 character encoding to work but finally managed to fix the issues with the Finnish ä:s and ö:s. It was a bit shame that the rest of the text files that we used on this course only featured text in English. 

### Week 4: Advanced Corpus Processing

4

### Week 5: Scripting and Configuration Files

5

### Week 6: Installing and Running Programs

6

### Week 7: Version Control

7

### Final Assignment: Building Webpages using GitHub Pages

F
