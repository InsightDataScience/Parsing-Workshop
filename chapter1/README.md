# Chapter 1: Bash Fundamentals

To get us off the ground, we will review basic bash commands and concepts and practice them with a bunch of small exercises.
This introduction is by no means comprehensive - refer to our [additional resources](#additional-resources) for more information.


## A walk through basic Bash commands

We will get started with a quick review of some of the most important commands. We encourage you to test them out as you read through this your first time, but also use this as a cheat sheet later on.
Note that you can execute all examples given in this subsection to try them out.

### File operations
Let us get started with a bunch commands that allow you to work with files.
There is not too much to say about them, so we will keep descriptions short.
#### cp
- Syntax: `copy source destination`
- Description: Allows you to copy a file.
- Example: `copy example.txt other.txt` will create a copy of example.txt named other.txt in this folder.
- Notable Options:
  - `l`: links files instead of copies them
  - `n`: no file overwrites
  - `R`: recursive copy, includes hidden files
#### mv
- Syntax: `mv source destination`
- Description: Allows you to move a file.
- Example 1: `mv example.txt other.txt` move example.txt to other.txt in the same folder. Therefore, `mv` can be used to rename a file.
- Example 2: `mv example.txt ..` will move the file in the parent folder, but keep the name of the file.
#### touch
- Syntax: `touch file/directory`
- Description: Updates access date of file/directory as well as creates new files if `file` does not exist
- Example 1: `touch example.txt` will update the access date of `example.txt`
- Example 2: `touch test.txt` will create a file `test.txt`.


### File Examination
The following commands are used for examining files and are often used when parsing log files.
#### cat
- Syntax: `cat file1 file2 ...`
- Description: Reads files sequentially and writes them to standard output.
- Example: `cat example.txt other.txt` will print both `example.txt` and `other.txt` to the console.
#### more/less
- Syntax: `more file`, `less file`
- Description:
    - `more`: Allows you to  view a text file one page at a time. Press spacebar to go to the next page.
    - `less`: A much more advanced pager (>27000 lines of source code), allows you to walk through the file in pretty much any way you want.
- Example: Try `less example.txt`!
- Action item: Read this [article](https://www.lifewire.com/what-to-know-less-command-4051972).
#### head/tail
- Syntax: `less file`, `more file`
- Description: Reads files sequentially and writes them to standard output.
- Example: `cat example.txt other.txt` will print both `example.txt` and `other.txt` to the console.
#### wc
- Syntax: `wc file1 file2 ..`
- Description: `wc`, short for "word count," prints a count of newlines, words, and bytes for each input file.
- Example: `wc lines.txt`
- Notable Options:
  - `c`: prints the byte counts
  - `w`: prints the word counts
  - `l`: prints the newline counts
#### du
- Syntax: `du directory`
- Description: Outputs disk usage of directory.
- Example: `du .`
#### diff
- Syntax: `diff file1 file2`
- Description: Outputs differences of `file1` and `file2` line by line.
- Example: `diff lines.txt example.txt`


### Searching and Sorting
#### grep
#### fgrep
#### sort
#### uniq
#### find
#### xargs
#### locate
#### which



### Process Management
#### ps/jobs
#### top
#### kill
#### &


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

### Exercises
- Write a short script that, given two text files, concatenates them and writes the output to a file `merged.txt` in the working directory.
- Given the files `lines.txt` in this directory, print out the 5th line using head and tail.

## Variables

## Quoting

## Functions

## Additional exercises

## Additional resources

- [Bash workshop](http://workshop-bash.com/)
- [Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)

## Next Chapter

Let us move on to [chapter 2](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/chapter1).
