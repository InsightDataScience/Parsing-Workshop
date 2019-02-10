# Chapter 1: Bash Fundamentals

To get us off the ground, we will review basic bash commands and concepts and practice them with a bunch of small exercises.
This introduction is by no means comprehensive - refer to our [additional resources](#additional-resources) for more information.


## A walk through basic Bash commands

We will get started with a quick review of some of the most important commands. We encourage you to test them out as you read through this your first time, but also use this as a cheat sheet later on.

### File operations
Let us get started with a bunch commands that allow you to work with files.
There is not too much to say about them, so we will keep descriptions short.
#### cp
- Syntax: `copy source destination`
- Description: Allows you to copy a file.
- Example: `copy example.txt other.txt` will create a copy of example.txt named other.txt in this folder.
- Notable Options:
  - `-l`: links files instead of copies them
  - `-n`: no file overwrites
  - `-R`: recursive copy, includes hidden files
#### mv
#### rm
#### touch

### File Examination
#### cat
#### more/less
#### head/tail
#### wc
#### du
#### diff

### File Permissions
#### chmod
#### chown
#### chgrp
#### umask

### Searching and Sorting
#### grep
#### fgrep
#### sort
#### uniq
#### find
#### xargs
#### locate
#### which

### Compression
#### (g)zip/(g)unzip
#### tar

### System Information
#### date
#### cal
#### uname
#### time

### Process Management
#### ps/jobs
#### top
#### kill
#### &


### Users and Groups
#### sudo/su
#### whoami
#### passwd
#### groups

### Network
#### ssh
#### sftp
#### scp
#### wget
#### curl

### RegExp
#### Defining regular expressions
#### egrep
#### sed

### Shell Scripting
#### comments
#### echo
#### printf
#### read
#### set, unset
#### export
#### let
#### if
#### [
#### seq
#### for
#### while
#### mapfile


## Piping
mention <, << etc also

## Variables

## Quoting

## Functions

## Additional exercises

## Additional resources

- [Bash workshop](http://workshop-bash.com/)
- [Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)

## Next Chapter

Let us move on to [chapter 2](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/chapter1).
