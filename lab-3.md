# Lab Report 3, Research on Find Command (a report even tho we didn't have lab during skill demo)
Okay, it's actually bad.

This blog describes the research learned from this [website](https://adamtheautomator.com/bash-find/#:~:text=The%20Bash%20find%20Command%20101,-Finding%20a%20file&text=The%20find%20command%20allows%20you,a%20folder%20on%20your%20computer.)

## Find -name

Despite having already seen this, -name wasn't really explained at all so here is what I gathered it does. 

Bash uses "tests" to filter the find command. Therefore, -name filters by name, and -type filters by type and so on. 
For the -name test, the find command will attempt to find a file or directory by the matching names. Note, this is 
specifically different from something like -type since this find option looks for matching strings and not types.

You can use * to fill in gaps such as finding apple* can also give you applepie in the find results. 

You can also use i in -name to ignore case-sensitivity in the results (-iname). 

For each of those options, give 2 examples of using it on files and directories from ./written_2. Show each example as a code block that shows the command and its output, and write a sentence or two about what it’s doing and why it’s useful. 

 Example 1 using -name
 
    $ find -name "Cuba-History.txt"
    ./travel_guides/berlitz2/Cuba-History.txt
 
 
Example 2 using -iname and * 

```
$ find -iname "Cuba-**.txt"
./travel_guides/berlitz2/Cuba-History.txt
./travel_guides/berlitz2/Cuba-WhatToDo.txt
./travel_guides/berlitz2/Cuba-WhereToGo.txt
 ```
 
 ## Find -type

The -type filters by type depending on the type. Use -type d for directory results or -type f for file results. 
The syntax is usually comes after the specificed string, such as find "example" -type d

Example 1 using -type d
```

```
 
Example 2 using -type f

```
$ find -name "Bahamas*" -type f
./travel_guides/berlitz2/Bahamas-History.txt
./travel_guides/berlitz2/Bahamas-Intro.txt
./travel_guides/berlitz2/Bahamas-WhatToDo.txt
./travel_guides/berlitz2/Bahamas-WhereToGo.txt
```

