# Hello there
## Welcome back to my fourth lab report 

We are going to today the exact keystrokes to do the following 

1. Log into ieng6
2. Clone your fork of the repository from your Github account
3. Run the tests, demonstrating that they fail
4. Edit the code file to fix the failing test
5. Run the tests, demonstrating that they now succeed
6. Commit and push the resulting change to your Github account (you can pick any commit message!)


> This is probably the most time consuming and tedious thing I’ll have to do right now but it is what it is.

Anyways here is the meme of the day:
![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/8e597b78-ebe4-4683-8a96-24e6b13bade1)

---

## Step 1: Log into ieng6

Since I had already logged in the ing6 before because it was acting kind of weird I ended up doing the following

```<up><enter> ```

Since my log in command was up once in my history of my terminal I simply hit the up key and enter to log in once again, Which, inturn leads me to to this point in my terminal.

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/51faf359-aa56-49f8-80c4-3e3d4af31ac7)

With that step one is done

---

## Step 2: Clone your fork of the repository from your Github account

Another easy step, I already have copied the link from the github repository meaning that in order to clone it I simply needed to paste in the clone command which I did by typing in the terminal:

Inside the ```<Ctrl>v``` is ```git@github.com:DanielGalicia94/lab7.git``` 

```git clone <Ctrl>v<enter>```

Doing that we get to this point: 
![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/4eb4a25c-5670-4ca3-816c-1f4db342b90a)

With that step 2 is done

---

# Step 3: Run the tests, demonstrating that they fail

Here I will divide the entire command in lines meaning that each line is its own separate input that happen in order:

```
cd l<tab><enter>
bash t<tab><enter>
```

What the first line did was change my directory into the file just copied, using the tab in order to autofill, and enter to push the command, the other one is to run a sh file that contained the files to test the java script. SO with that we get to this point that tells us that the test ain't working:
![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/c49182c5-b95f-4b0e-8c31-d7d274f4e895)

---

# Step 4: Edit the code file to fix the failing test

Now we have the most complicated part of this whole section but anyways here we go:

```
vim L<tab>.<tab><enter>
43j  
9l 
xi2<ESC>
<shift>;wq
```
The vim command is what will allow me to edit this whole thing, again using the tab to autocomplete, and that leads to this picture of us in vim's main mode:
![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/7a0a4e4c-7f97-4d5a-91e2-728a238e84f7)

The next 4 lines are technically typed together but in order for easy visualization I kept them separate but now first we got the ```43j```, the j button in vim, when in main mode, moves our cursor down once, and by typing 43 before it it tell’s vim to move 43 lines down or where our problem is, not the most effective or accurate, but we can always brute force our way through it.

The ```11l``` is similar to the above, except the l means move the cursor one character to the right, and, like the command before, putting a number before it will cause it to jump that many spaces to the desired position.

Now we have the ```xi2<ESC>```, since we now have the cursor in the desired position, the ```x``` command in vim, in its main mode, will delete the character that it’s currently on, so the 1 gets erased. Then the ```i``` will make vim enter its insert mode meaning that we can now edit it, which is where the 2 comes in, after the 2 we press ```<ESC>``` to return to the main mode.

Which leads us to this image: 
![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/0d104c51-2578-45b3-b8ad-4f4d214c8c28)

Finally we get to the last line ```<shift>;wq``` which is the command in order to save and quit vim mode. After all of this we are left with this screen:
![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/b4d9713c-6f94-45eb-aaf4-b2e3aaf91626)
