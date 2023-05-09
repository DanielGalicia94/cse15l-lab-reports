
# Hello there
## Welcome back to my Lab Reports 

Today I am presenting the third report which will cover the following:
1. 4 interesting command-line options or alternate ways to use the command grep

> I must thank the 15L overlords for giving us a pretty simple task 

With that out of the once again:
## Let us begin

The joke of the day:
> painfull because how true it is

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/a17e9ec5-7929-40e2-8f23-2081fd2c8a30)

---

## Using Grep

From the intro at this point I'm assuming you know that I'm going to be exploring the grep command, so here are my four ways I'm going to exploring:

1. ```grep -v```
2. ```grep -i```
3. ```grep -rl```
4. ```grep -<some param> "<someword>$"```

So let's move on tp the examples:

> Note: how I found about these examples is that I googled "interesting command-line options or alternate ways to use the command grep"

> Also the documentaion that I used for each example can be found in this [link](https://www.gnu.org/savannah-checkouts/gnu/grep/manual/grep.html)

---
## ```grep -v```

This command over here is pretty much the opposite of ```-r``` as it prints out all the lines in a text file, important here the input must be files not a directory, that do not contain the input. Very useful when trying to only find parts that don’t include a certain key word or phrase.



---

## ```grep -i```

This command is interesting because again it’s similar to ```r``` as it prints out matching lines but the key difference is that it ignores cases, such as uppercase and lowercase. This is useful as it will print out the lines with the different cases and not ignore a line if it has an uppercase in one letter as opposed to a lowercase.

---

## ```grep -rl```

This command over here I used quite a lot when practicing for the skill demo 1. It takes a word as its input and a directory and searches for all files containing the specific word and prints out their name. Mighty useful if, let's say, looking at the files given to practice your skill demo there are a bunch of files. By the sheer amount of those files you might think that the hidden task might be to search for a file containing a certain key word or phrase. But that’s just me 


---

## ```grep -<some param> "<someword>$"```

What I’m focusing on here is the ```$``` as this makes an interesting pattern as it does whatever you put it to do except that the only difference is that the word is at the end. For example if searching for lines, then it will print out the lines that end with the word rather than outright contain it. Useful when you want to narrow down your search for the line.
