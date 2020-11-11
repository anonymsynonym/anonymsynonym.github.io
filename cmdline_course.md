---
layout: default
---

## KIK-LG219

I took the elective online course KIK-LG219 Commandline tools for linguis (5 cd.) as a part of my studies in language technology in autumn 2020. The purpose of the course was to learn basic tools for the Unix command-line. The command-line environment is a quicker and more powerful alternative to graphical interfaces for handling files and directories. It can be used, for example, to run scripts on multiple files, to process and extract corpus data, and to share and work on a project between multiple users. Each of the 7 weeks of the course introduced a new topic and a set of new commands, starting from the very basics.

The course material was quite clear and easy to understand. Practicing through exercises and testing every command on my own command-line shell helped me understand the topics. The most difficulties that I had were with the setup of different programs. Many of the programs would not work at first and needed additional prerequisite programs or alternative program versions to be installed. These possible problems weren't usually tackled in the course material, but luckily fixes for most of them could be found on Google.

### Week 1: Introduction to Command Line Environments

The first week started with setting up the command-line environment. As I am using Windows 10, I needed to first enable the Windows Subsystem for Linux in my settings and then install a working version of Ubuntu Bash Shell.

For example

Here's what the following set of commands does, illustrating  important commands and what they do:

1. Prints your username.
2. Prints your working directory.
3. Downloads a (plain text) file to your working directory.
4. Views the content of the downloaded file with *less*.
5. Renames the file.
6. Views the content of the file with *cat*.
7. Creates a new subdirectory.
8. Copies the file to the subdirectory.
9. Removes the original file from the working directory.
10. Lists all (including hidden) files and directories in the working directory.
11. Changes into the subdirectory.

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

### Week 2: Navigating a UNIX System

2

### Week 3: Basic Corpus Processing

3

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
