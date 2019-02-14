# Chapter 3: SED and AWK

The two tools `sed` and `awk` are essential to write powerful and efficient scripts. Both `sed` and `awk` are text processing utilities that work on a line by line basis. Typically, `sed` is preferable for character-based processing whereas `awk` is the tool of choice for delimited field processing.

We will really only discuss a glimpse of what `awk` and `sed` do in this chapter. We highly recommend working through the additional resources as well.

## awk

- Syntax: `awk [options] 'BEGIN{}; {}; END{}' file`
-- The BEGIN block is executed before processing the first line.
-- The MIDDLE block is executed on every line.
-- The END block is executed after the EOF signal.
- Description: Works through `file` line by line according to `program text`. `program text` can access each line in a field delimited way.  This is very similar to the Split() function, found in many languagues, being run on each line of a file.

### Exercises
Our First Awk
consider the file:
1 2 3  
4 5 6  
7 8 9  

if we use awk on this text document we can
```
awk '{print $0}' FILE // Print each line
```
1 2 3  
4 5 6  
7 8 9  




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
Remember to work on solutions for Python and Bash. It is also worth thinking about a solution with `awk` and a different one with `sed` whenever possible.

Note that this is a long list of exercises and many of them are signifcantly more involved than what we discussed so far. We recommend working on one exercise per day in the order listed here.

- [Regular Expressions](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/reg_ex)
- [Analyzing Apache Logs](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/analyzing_apache-logs).
- [Ini Files](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/ini_files).
- [Reports](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/reports)
- [Traceroutes](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/traceroutes)
- [Analyzing video log files](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/video_log_files)

## Next Chapter

Let us move on to [chapter 4](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/chapter4).
