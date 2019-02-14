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

if we use awk on this text document we can mimic the linux command 'cat'
```
awk '{print $0}' FILE // Print each line
```
1 2 3  
4 5 6  
7 8 9  

```
awk '{print $1}' FILE // print the first number of each line
```
1  
4  
7  
The previous examples demonstrate how awk is NOT 0-indexed.  The zero is reserved for the whole line.  Instead indexing starts at 1.  

what about?  
```
awk '{print $4}' FILE // no output
```

In the following example, notice how the BEGIN and END blocks are executed once, while the middle block is executed once per line of FILE:  
```
awk 'BEGIN{print "Hello World"}; {print "awkWard"}; END{print "easy huh?"}' FILE //Print some strings  
```
Hello World  
awkWard  
awkWard  
awkWard  
easy huh?  

```
awk '{x+=$2; print $3, " plus "};END{print "="; print x}' FILE //simple addition 1-liner
```
3 plus   
6 plus  I Honestly dont know why it is bolded   
9 plus   
= 
18  

A Huge reason why awk is very useful is because of what you saw in the previous examples.  90% of use cases are taking one linux command and piping it to awk.  This in turn allows you to select a specific value and print it to your screen.  
With that said, awk can be not only useful, but incredibly powerful.  I used to work in a lab where one of the post-docs used awk instead of python or perl for ALL of his scripting.  
First of all, awk can do c-style for loops: Notice the NF variable, this is Number of Fields, i.e. the length of the array after the split is performed.  
```
awk '{for(i=1; i<=NF; i++){x[i]+=$i}};END{ for (i=1; i<=NF; i++){print x[i]}}' FILE // notice how for loops have () around conditions, and {} around the actual contents.
```
12  
15  
18  
  
In addition, awk can do key value loops as well:
```
awk '{for(i=1; i<=NF; i++){x[i]+=$i}};END{for (i in x){print x[i]}}' FILE //Notice how the order changed!
```
15  
18  
12  


Alright, so we can do some basic math and such with awk.  How about parsing log files?  
As tasks get more complex, awk actually begins to shine.  Consider a regularly recurring task which prints the time of a ping and response from various servers on your network.  
Us-North: 35   
Us-East: 32  
Us-South: 112  
Us-West: 128  
Us-North: 34   
Us-East: 31  
Us-South: 111  
Us-West: 127  
Us-North: 36  
Us-East: 33  
Us-South: 113  
Us-West: 129  

How can we use this log file to get each average latency (or other value) for each server? etc? (Notice the FS, this is the Field separator which defaults to " ")
```
awk 'BEGIN{FS=": "};{x[$1]+=$2}; END{print "Average Latencies:\n------"; for(i in x){print i, " : ", x[i]/3.0}}' FILE2
```
Average Latencies:  
------  
Us-North  :  35  
Us-West  :  128  
Us-East  :  32  
Us-South  :  112  

Well, that is nice and good, but what if we dont know how many of each ping/response there is? what if they're not in order? etc??  Easy, just add a counter.
```
awk 'BEGIN{FS": "};{x[$1]+=$2; y[$1]++}; END{print "Average Latencies:\n------"; for(i in x){print i, " : ", x[i]/y[i]}}' FILE2 // notice different order! (Also note, this is not covering floating point div, just google it)
```
Average Latencies:  
------  
Us-West:  :  128  
Us-East:  :  32  
Us-South:  :  112  
Us-North:  :  35  

A regex example, just so you have some experience with it  
Consider:  
1 2 3  
4 5 6  
a b c  
7 8 9  
```
awk '{if($2~/[0-9]+/){x+=$2; y++};END{print x/y}' FILE3 // the regex causes you to not try to add 'b' to your value of 7
```
5

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
