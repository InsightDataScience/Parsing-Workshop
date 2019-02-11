# Parsing .ini files

In this exercise, we will take a look at ini or config files of the shape

```
home=$TOOL_HOME
# comment
[memory]

base  = 5g
gc= advanced

[logs]
   # what is this?
loc=/somewhere/in/the/middle/of/nowhere/   
```

where

- comments start with #
- sections start with [section_name]

It is our goal to parse this and return a dictionary of dictionaries (or hash of hashes). For your bash solution, note that you need Bash version at least 4 for hash of hashes support.
The dictionary should assign to each section a dictionary where key value pairs correspond to the assignments made in the corresponding section. Any assignments made before the first section should belong the section `_`.

For the specific example above, the Python solution would be a dictionary
of the shape

```Python
{
"_": {
  "home": "$TOOL_HOME"
},
"memory": {
  "base": "5g",
  "gc": "advanced"
},
"logs": {
  "loc": "/somewhere/in/the/middle/of/nowhere/"
}
}
```

## Exercises

Before you get started, make sure you review [hashes in Bash](https://lzone.de/cheat-sheet/Bash%20Associative%20Array).

1. Write a script implementing the function outline above and test it on example.ini!
2. Why would such a script be useful?
