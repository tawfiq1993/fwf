fwf
===


still to do: create, example files and finish writeup

Some people have trouble coming to grips with what the widths element does when reading in fixed width files in R. This is a walk through you can follow along to get the hang of them.

The first file we are playing with, simple.txt, consists of three rows of the numerals 1 to 9 and the letter A.


```
123456789A
123456789A
123456789A
```

So the first character in each line is the 1, the second is the 2, the tenth is the A.

if you have not forked this repo, the file should be able to be downloaded to your working directory with the commands:


```
To be worked out
```

first lets just try read.table and confirm we get three lines that R reads in as text and converts to factors.


```
e <- read.table("simple.txt")
str(e)
```

now let's abandon that command and look at the results for various width options when using the command for reading in fixed width files.

__widths=c(9,1)__

This choice reads inn the first nine characters (the numbers) into one variable, then reads the next character in as a second letter, in this case the letter A. because the data in the first column consists only of numerals, R has assigned it to a numeric type. the letter A in the second variable has been assigned character and converted to factor.

__widths=c(2,-2,2)__


This choice reads in the first two characters as the first variable, then skips two characters using the -2, then reads in the two characters after that as the second variable, then ignores the rest of the line as there is no width information about the remaining settings. so the result is two variables, one made from the 12 and one made from the 56

So R is reading in the file working across from the left hand end of each line, grouping the parts of the line together as variables.

* each positive number is a group of characters to put together into as variable.
* each negative number is a group of characters to skip
* characters in the line beyond those listed in the widths are ignored
* variable type gets assigned by the contents of the variable (as normal)

__trimming__

One more thing before the challenge example you can try out on your own, if there is extra space before and after an entry R will trim it in this case, so the values you use should include the widest entries and don't worry about extra spacing in the smaller entries.
