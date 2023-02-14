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

 Example 1 using -name. This is useful to find certain files or directories named a specific string.
 
    $ find -name "Cuba-History.txt"
    ./travel_guides/berlitz2/Cuba-History.txt
 
 
Example 2 using -iname and *. This is useful to find files or directories with a specific string but you can't recall the case of each letter or the entire string.

```
$ find -iname "Cuba-**.txt"
./travel_guides/berlitz2/Cuba-History.txt
./travel_guides/berlitz2/Cuba-WhatToDo.txt
./travel_guides/berlitz2/Cuba-WhereToGo.txt
 ```
 
## Find -type

The -type filters by type depending on the type. Use -type d for directory results or -type f for file results. 
The syntax is usually comes after the specificed string, such as find "example" -type d

Note: Use * in the string search in combination with -name unless you know exactly the string

Example 1 using -type d. This is useful if you only want directories in your search results.
```
$ find -name "berlitz*" -type d
./travel_guides/berlitz1
./travel_guides/berlitz2
```
 
Example 2 using -type f. This is useful if you only want files in your search results.

```
$ find -name "Bahamas*" -type f
./travel_guides/berlitz2/Bahamas-History.txt
./travel_guides/berlitz2/Bahamas-Intro.txt
./travel_guides/berlitz2/Bahamas-WhatToDo.txt
./travel_guides/berlitz2/Bahamas-WhereToGo.txt
```

Side note: The operator -and can also be used to combine -name and -type. 

## Find -or

Bash also uses Operators to perform actions such as combining filters or allowing two search conditions. With this, 
you can find two things at once. 

Example 1 using -or. This is helpful if you need to find all files named either one string or another string.
```
$ find -name "Bahamas*" -or -name "*HongKong*"
./travel_guides/berlitz1/HandRHongKong.txt
./travel_guides/berlitz1/HistoryHongKong.txt
./travel_guides/berlitz1/IntroHongKong.txt
./travel_guides/berlitz1/WhatToHongKong.txt
./travel_guides/berlitz1/WhereToHongKong.txt
./travel_guides/berlitz2/Bahamas-History.txt
./travel_guides/berlitz2/Bahamas-Intro.txt
./travel_guides/berlitz2/Bahamas-WhatToDo.txt
./travel_guides/berlitz2/Bahamas-WhereToGo.txt
```
 
Example 2 using -or with -type d. This is useful if I wanted the files named Hawaii but also the directory of Berk but not all the 
files in the Berk files at the same time.
```
$ find -name "*Hawaii*" -or -name "Berk" -type d
./non-fiction/OUP/Berk
./travel_guides/berlitz1/HandRHawaii.txt
./travel_guides/berlitz1/HistoryHawaii.txt
./travel_guides/berlitz1/WhatToHawaii.txt
./travel_guides/berlitz1/WhereToHawaii.txt
```

## Find -not

Bash also supports a -not which excludes certain files or directories you don't want.

Example 1 using -not. This is helpful if you want all files and directories that doesn't contain 
Bahamas* but usually is better for smaller datasets or combined with -and. 
```
$ find -not -name "Bahamas*"
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Abernathy/ch1.txt
./non-fiction/OUP/Abernathy/ch14.txt
./non-fiction/OUP/Abernathy/ch15.txt
... (goes on for 30 more lines)
```
 
Example 2 using -not with -and. This is useful if you want all files/directories named Bahamas* but none of the files with History string 
in the name.
```
$ find -name "Bahamas*" -and -not -name "*History*"
./travel_guides/berlitz2/Bahamas-Intro.txt
./travel_guides/berlitz2/Bahamas-WhatToDo.txt
./travel_guides/berlitz2/Bahamas-WhereToGo.txt
```
