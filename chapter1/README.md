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
In order to quickly find relevant content in messy log files, searching and sorting is absolute key. The commands below will get us started, though we will also have to dive deeper into additional options (such as `awk` and `sed` later on).
#### grep
- Syntax: `grep pattern [file]`
- Description: Prints out every line in `file` that contains `pattern`. We will discuss how to define a pattern more under regular expressions.
- Example 1: `grep '1' lines.txt` will print out the two lines that contain `1`.
- Example 2: `grep '1' *` will print out the lines of any file in the current directory that contain `1`.
- Example 3: `grep '.' lines.txt` will print out all lines in `lines.txt` as they all match the pattern `.`.
- Notable Options:
  - `c`: This prints only a count of the lines that match a pattern
  - `i`: Ignores, case for matching
  - `v`: This prints out all the lines that do not matches the pattern
  - `f`: Takes patterns from file, one per line.
  - `w` : Match whole word
  - `o` : Print only the matched parts of a matching line,
#### fgrep
- Syntax: `grep string [file]`
- Description: Prints out every line in `file` that contains `string`. The main difference to `grep` is that it searches for a string rather than a pattern.
- Example 1: `fgrep '1' lines.txt` works just like the `grep` version.
- Example 2: `fgrep '.' lines.txt` will print nothing, unlike the `grep` version.
#### sort
- Syntax: `sort file`
- Description: Sorts the input file line by line and writes the result to standard output.
- Example 1: `sort lines.txt`. Read the output carefully, you might be surprised!
- Notable Options:
  - `o`: allows you to specify an output file.
  - `r`: sorts in reverse
  - `n`: sort files numerically
#### uniq
- Syntax: `uniq file`
- Description: Removes duplicate lines in text file.
- Example: `uniq lines.txt`. Does not change a thing! How about if you repeat the line `3` twice and then run it?
#### find
- Syntax: `uniq file`
- Description: Removes duplicate lines in text file.
- Example: `uniq lines.txt`. Does not change a thing! How about if you repeat the line `3` twice and then run it?
#### xargs
For the `xargs` command, we recommend first looking into the section about piping below, as it is hard to understand `xargs` without piping.
- Syntax: `xargs [command]`
- Description: xargs reads items from standard input as separated by blanks and executes a command once for each argument. The default command is to print it to standard output.
- Example 1: `ls -1 . | xargs` This prints out the content of the current folder in one line!
- Example 2: `echo 'one two three' | xargs mkdir` will create three folders in the current directory.


### Process Management
These commands are the most basic to get you started understanding what is running on a system.
#### ps
- Syntax: `ps`
- Description: Displays processes currently running (options allow you to toggle what kind of processes will be displayed.)
- Example: `ps`
- Notable Options:
  - `A`: List all processes
  - `au`: List all processes in BSD format
  - `fp`: Display process by process id (PID)
#### top
- Syntax: `top`
- Description: Live display or current processes with PID, %CPU and %Memory. You can quit the view  by typing `q`.
#### kill
- Syntax: `kill PID`
- Description: Kills the process with the given PID.

### Network
#### ssh
- Syntax: `ssh ip-address`
- Description: Attempts to establish an ssh connection to the given ip address.
- Notable Options:
  - `i`: Provide a private key for authentification.
  - `p`: Set port to connect to.
#### sftp
- Syntax: `sftp ip-address`
- Description: Stands for secure FTP. Uses the FTP protocol to transfer files. Starts an interactive session where you can transfer files between your machine and the ip address provided.
#### scp
- Syntax: `scp source destination`
- Description: Stands for secure copy. Allows you to copy files between servers using ssh and has the same options as ssh for authentification.
#### wget
- Syntax: `wget http://website.com/files/file.zip`
- Description: Allows you to download files, `wget` stands for web get.
#### curl
- Syntax: `curl website`
- Description: Allows you to download the content of a webpage, or really, anything accessible on the web. Supports a wide variety of protocols.
- Example: `curl google.com`

### Regular Expressions
Regular expressions are fundamental to efficient parsing. They allow you to define patterns that other tools, such as `grep`, `sed` or `awk` can use to process files.
Explaining regular expressions in detail is beyond the scope of this workshop and, fortunately, there are lots of good resources out there.
- [Action Item]: Read a [Brief Introduction to Regular Expressions](https://www.tldp.org/LDP/abs/html/x17129.html)

#### Exercises:
- Define a regular expression that:
  - Matches `aad` and `aaad` but nothing else.
  - Matches any email address of the shape `something@somethingcom`.
  - Matches any IPv4 address.


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
