# Chapter 3: SED and AWK

The two tools `sed` and `awk` are essential to write powerful and efficient scripts. Both `sed` and `awk` are text processing utilities that work on a line by line basis. Typically, `sed` is preferable for character-based processing whereas `awk` is the tool of choice for delimited field processing.

We will really only discuss a glimpse of what `awk` and `sed` do in this chapter. We highly recommend working through the additional resources as well.

## awk

- Syntax: `awk [options] 'program text' file`
- Description: Works through `file` line by line according to `program text`. `program text` can access each line in a field delimited way. See the example for illustration.
- Example: `ls -l | awk ‘{print $1}’`. This will print the first column of `ls -l`. With respect to our syntax, `file` is `ls -l`. Our program text can access the columns of each line via `$1, $2, etc`. The variable `$0` contains the whole file.
- Notable Options:
  - `F`: Specify delimiter, whitespace is default.

### Exercises

- Before you run it, what does
```
echo "Have a bad day!" | awk '{$3="good"; print $0}'
```
do?
- You can use the option `-v` to declare a variable. Replace `MODIFY` in the following snippet so that it outputs the user's home directory: `echo | awk -v home=MODIFY '{print "My home is " home}'`.

## sed

Sed is a powerful stream editor with a plethora of options. For this workshop, we will first focus on its substitution capabilities. However, make sure to read the additional resources to learn more.


- Syntax: `sed [options] file`
- Description: Reads through the file one line at a time and performs processing on it based on options.
- Example: `sed ‘s/old/NEW/’ file` This command will substitute `old` with `NEW` everywhere in the file.

In general, options given to `sed` starting with `s/` will form some sort of substitution on the file.

### Exercises
- What does `sed -n "/test/p" example.txt` do?

## Additional Resources

As mentioned above, we highly recommend working through those tutorials carefully before proceeding.

- For `sed`: [Sed - An Introduction and Tutorial](http://www.grymoire.com/Unix/Sed.html)
- For `awk`: [Awk Tutorial](http://www.grymoire.com/Unix/Awk.html)

## Additional Exercises

We can now tackle some of the exercises in the exercises folder!
Remember to work on solutions for Python and Bash.



## Next Chapter
