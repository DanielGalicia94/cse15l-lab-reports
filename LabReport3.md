
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

Here we have ```grep -v "a" technical/911report/*.txt > vEX1.txt``` which will find all lines in the text files in file ```/911report``` and store it in ```vEX1.txt``` and here are a few lines of the absolute mostroncity that is the test file:
```
technical/911report/chapter-1.txt:
technical/911report/chapter-1.txt:	
technical/911report/chapter-1.txt:		
technical/911report/chapter-1.txt:"WE HAVE SOME PLANES"
technical/911report/chapter-1.txt:
technical/911report/chapter-1.txt:
technical/911report/chapter-1.txt:
technical/911report/chapter-1.txt:INSIDE THE FOUR FLIGHTS
```

Moving on to our second example ```grep -v "at" technical/911report/chapter-1.txt > vEX2.txt``` will find all lines not containing at and store it in a text file,
again I won't put the absolute monstroncity of the file but here are a few lines that were given.

```

	
		
"WE HAVE SOME PLANES"



INSIDE THE FOUR FLIGHTS

Boarding the Flights






    In another Logan terminal, Shehhi, joined by Fayez Banihammad, Mohand al Shehri, Ahmed al Ghamdi, and Hamza al Ghamdi, checked in for United Airlines Flight 175, also bound for Los Angeles. A couple of Shehhi's colleagues were obviously unused to travel; according to the United ticket agent, they had trouble understanding the standard security questions, and she had to go over them slowly until they gave the routine, reassuring answers.




    None of the checkpoint supervisors recalled the hijackers or reported anything suspicious regarding their screening.





    All five hijackers passed through the Main Terminal's west security screening checkpoint; United Airlines, which was the responsible air carrier, had contracted out the work to Argenbright Security.

```

---

## ```grep -i```

This command is interesting because again it’s similar to ```r``` as it prints out matching lines but the key difference is that it ignores cases, such as uppercase and lowercase. This is useful as it will print out the lines with the different cases and not ignore a line if it has an uppercase in one letter as opposed to a lowercase.

We have ```$ grep -i "TraDe cenTeR" technical/911report/chapter-1.txt > iEX1.txt``` This should hopefully take all the lines in ```chapter-1.txt``` that include the words Trade Center and as you can read I purposesly exaggerated the cases in each letter to emphasize how it obtained all the lines that include those characters. Same as last time Im putting some of it's output

```
Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
At 8:46:40, American 11 crashed into the North Tower of the World Trade Center in New York City.
The call ended abruptly. Lee Hanson had heard a woman scream just before it cut off. He turned on a television, and in her home so did Louise Sweeney. Both then saw the second aircraft hit the World Trade Center.
At 9:03:11, United Airlines Flight 175 struck the South Tower of the World Trade Center.
```

Moving to the second example we got ```$ grep -i "AlPhA" technical/biomed/*.txt > iEX2.txt``` which should look for all the lines containing the word alpha regardless of cases and store it in a file. Usually this comand is bettered used with a single file.
Here are the results:

```
technical/biomed/1468-6708-3-10.txt:        or an alpha-adrenergic blocker (doxazosin). An open-label
technical/biomed/1468-6708-3-7.txt:        (ALLHAT), the role of peripheral alpha-1 antagonists in the
technical/biomed/1468-6708-3-7.txt:        alpha-1 antagonists in general or doxazosin in particular
technical/biomed/1468-6708-3-7.txt:        positive effects of peripheral alpha-1 antagonists on
technical/biomed/1468-6708-3-7.txt:        English-language papers on peripheral alpha-1 antagonists
technical/biomed/1468-6708-3-7.txt:        "terazosin," "adrenergic alpha-antagonists," or "alpha
technical/biomed/1468-6708-3-7.txt:          Evidence suggests that alpha-1 antagonists are
technical/biomed/1468-6708-3-7.txt:          use of peripheral alpha-1 antagonists, the prevalence
technical/biomed/1468-6708-3-7.txt:          Blood Pressure (JNC VI), peripheral alpha-1 antagonists
technical/biomed/1468-6708-3-7.txt:          hypertension and prostatism [ 2 ] . Alpha-1 antagonists
```

---

## ```grep -rl```

This command over here I used quite a lot when practicing for the skill demo 1. It takes a word as its input and a directory and searches for all files containing the specific word and prints out their name. Mighty useful if, let's say, looking at the files given to practice your skill demo there are a bunch of files. By the sheer amount of those files you might think that the hidden task might be to search for a file containing a certain key word or phrase. But that’s just me 

First example ```grep -rl "alpha" technical/ > rlEX1.txt``` this is searching for all the file names in the directory that contain the word alpha and then storing it into a text file.
Output sample is the following:
```
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/biomed/1468-6708-3-10.txt
technical/biomed/1468-6708-3-7.txt
technical/biomed/1471-2091-3-14.txt
technical/biomed/1471-2105-3-12.txt
technical/biomed/1471-2105-3-14.txt
technical/biomed/1471-2105-3-18.txt
technical/biomed/1471-2105-3-2.txt
technical/biomed/1471-2105-3-24.txt
technical/biomed/1471-2105-3-26.txt
technical/biomed/1471-2105-3-28.txt
technical/biomed/1471-2105-3-34.txt
technical/biomed/1471-2105-3-6.txt
technical/biomed/1471-2121-3-13.txt
```

Second example ```grep -rl "fire" technical/plos/ > rlEX2.txt ``` you can see that we can narrow down the scope as we need it. Doing the exact same things as described above but on a smaller scope

Full output:
```
technical/plos/journal.pbio.0020047.txt
technical/plos/journal.pbio.0020054.txt
technical/plos/journal.pbio.0020105.txt
technical/plos/journal.pbio.0020146.txt
technical/plos/journal.pbio.0020267.txt
technical/plos/journal.pbio.0020302.txt
technical/plos/journal.pbio.0020346.txt
technical/plos/journal.pbio.0020400.txt
technical/plos/pmed.0020208.txt
technical/plos/pmed.0020209.txt
```

---

## ```grep -<some param> "<someword>$"```

What I’m focusing on here is the ```$``` as this makes an interesting pattern as it does whatever you put it to do except that the only difference is that the word is at the end. For example if searching for lines, then it will print out the lines that end with the word rather than outright contain it. Useful when you want to narrow down your search for the line.

For the examples I'm going to recreate the ```-r``` comands we used for the lab

Remexing to our needs example 1 is ```grep -r "base pair$" technical/biomed > endEX1.txt``` Which will give you all the lines in ```technical/biomed``` that end with base pair

Output: 
```
technical/biomed/1471-2105-4-27.txt:          to, and interrogates the expression of a 25 base pair
technical/biomed/1471-213X-1-4.txt:          the bpA. These two enzymes are rare eight base pair
technical/biomed/1471-2164-2-4.txt:        this assay to genotype any SNP regardless of the base pair
technical/biomed/1471-2180-3-13.txt:          loop a and stem 2 (Figure 12). Compensatory base pair
technical/biomed/1471-2202-3-7.txt:        complex process that involves generating a 9 base pair
technical/biomed/1471-2229-2-3.txt:        conducted at high stringency with a 1700 base pair
technical/biomed/1472-6750-1-13.txt:        748 were screened along with all possible single base pair
```

Now we for example 2, which is ```grep -r "base pair$" technical/plos > endEX2.txt``` Which will give you all the lines in ```technical/plos``` that end with base pair

And our grand output is:
```

```
Yeah apperently there are no files in plos that end with base pair, but we can now safely say that biomed contains the most lines that end with "base pair"

---

## With that everything comes to an end 

Thank you for reading my report and ramblings

and until next time

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/53ae602a-2a5e-4f52-93fa-11188752be37)
