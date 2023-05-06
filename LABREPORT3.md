# Lab Report 3 - Week 5 (Researching Commands)

## *Others ways to use 'find' command*

> **less -p[string] [file path]**
___
This alternate way of the 'find' command will highlight any occurance of the string that was passed in the given file. When this command is use, it will go to the first occurence of the string in the file. 

**Example 1:**

Input: 

```
emilyholguin@Emilys-MacBook-Pro-7 docsearch % less -pPresident technical/911reports/chapter-1.txt
```

Output:

![Image](labreport3-find1.png)
  
The output shows that we are searching for "President" in the file. As it highlights the word throughout the file. 

**Example 2:**

Input: 

```
emilyholguin@Emilys-MacBook-Pro-7 docsearch % less -pEmily technical/government/About_LSC/Progress_report.txt
```

Output:

![Image](labreport3-find2.png)

This command was found using `man find` in the terminal.

In this example, we are searching for "Emily" in the file. However it did not find any occurences of the string which is why we got the above output. 

