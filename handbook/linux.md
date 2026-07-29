# Linux Basics

## Commands Learned

### pwd
Shows the current directory I am working in.

### ls
Shows the files and folders inside the current directory.

### cd
Changes the current directory.

### cd ~
Takes me to my personal Linux home directory: /home/juan.

### cd ..
Takes me one level up to the parent directory.

### mkdir
Creates a new folder.

### touch
Creates a new empty file.

## Important Concepts

### Home Directory
My personal folder inside Linux.

Example:

/home/juan

### Absolute Path
A complete path starting from the root of the system.

Example:

/home/juan/sdet-academy

### Relative Path
A path based on where I am currently located.

Example:

If I am inside:

/home/juan/sdet-academy

Then:

cd journal

takes me to:

/home/juan/sdet-academy/journal

### Parent Directory
The folder that contains the folder I am currently inside.

It is represented by:

..

## Mistakes I Made

- I typed 1s instead of ls.
- I used cd - before having a previous directory.
- I tried to enter projects from inside journal, but projects was not inside journal.
- I accidentally created notes and projects inside /home/juan instead of inside cloud-engineer-academy.

## Lesson of the Day

Before running commands, I should ask myself:

1. Where am I?
2. What is inside this directory?

Useful commands:

pwd
ls

## File Commands

### touch
Creates a new empty file.

Example: touch notes.txt

### cat
displays the content of a file in the terminal.

Example: cat notes.txt

### echo
Prints text to the terminal. It can also write text into a file.

Example: echo "Hello Linux" > notes.txt

### >
Writes output into a file and overwrites the previous content.

### >>
Adds output to the end of a file without deleting the previous content.

### cp
Copies a file.

Example: cp notes.txt notes-backup.txt

### mv
Moves or renames a file.

Example: mv notes-backup.txt backup-notes.txt

### rm
Deletes a file

Example: rm delete-me.txt
Important: rm can permanently delete files, so I should use it carefully

### nano
A terminal-based text editor.

Save in nano: 
Ctrl + O
Enter

Exit nano:
Ctrl + X

test for day 006 - edited locally