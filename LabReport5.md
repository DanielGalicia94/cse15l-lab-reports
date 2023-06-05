# Hello there
## Welcome to my last lab report 

We are going to today cover how to:
1. Act like a TA and help a fellow student find what's going on with their code
2. A reflection for the last half of this class

So without any further ado, let us begin one final time:

Meme of the day:

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/971b3c6b-b12f-41ca-bed3-cc8d3a75ff63)
> Quite apt for what we are doing
---

## The excahnge

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/03488f27-ba30-46da-9e4a-b56cc46dfad8)

Here we have a student having an issue with their autograder, with his problem that it says that the files can't be found, very interesting

So seeing how he is struggling I decided to help, also because it's my job as a TA. Anyways I see in his code that he has done almost everything correctly. My next comment would be 

# After running the script try checking which files are inside your current directory. Hint, try using ls

After that our good freind will receive this.

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/5b0f3d52-466e-4e3e-8a70-c9617261cc37)

The bug being that they forgot to change their working directory, meaning that all the files he wants to compile are not available until he changes directories.

---

## For the third and final step

We need to show:
1. The file & directory structure needed
    
    This wasn't the problem but here is a screen schot of the needed strcuture
    
    ![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/679c3c41-7e76-4004-966b-ed14fa3d1ddb)

    
2. The contents of each file before fixing the bug

    Same image her before fixing the bug:
    
    ![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/6e7b2abe-c456-4b42-8841-cc9cc929782b)


3. The full command line (or lines) you ran to trigger the bug

    Here it is:
    ```bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3```

4. A description of what to edit to fix the bug

    In the sh file before the code tries to compile we need to add a line into the script that will
    change the current directory like this:
    
    ![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/89a898c7-3493-4c1f-875b-70c3c7d6043f)
    

This should be your files final result:

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/bd861d4f-ba2c-4a7e-a7f3-42fc3d1d06eb)

As you can see all the files have compiled but unfortunatly for out freind one bug is fixed but there apear to be a lot more in store for him.

---

## Reflection

One of the things that	I learned this latter half of the quarter was how to use vim. While vhs code is all well and good, it appears that in future classes I'll have to edit from a remote server, so that will be fun. While vim can be frustrating sometimes it is a useful tool that I will probably use in my later classes. 

---

# With all of that

I thank all of you for reading my lab reports and the rambling of a mad student, and I wish luck to all of your future endeavors to whoever is reading this last lab report.

![image](https://github.com/DanielGalicia94/cse15l-lab-reports/assets/56609916/c1c83bbe-4767-4100-b519-dd09dab470cd)


