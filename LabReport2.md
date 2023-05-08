# Hello there
## Welcome back to my Lab Reports 

Today I am presenting the second report which will cover the following:
1. Creating a Webserver that can update
2. Debugging 101
3. Somethings that I learned from lab 2 and lab 3

So without any further ado:
![image](https://pbs.twimg.com/media/Frl-nVoWcAI6lPF.jpg)

---
## The Webserver
Normally creating a web server from scratch is a bit difficult as a beginner to coding is pretty difficult as I have no idea how to even start one.

Fortunately there is code for a web server in Lab 2 so, time to commandeer some code.
I created a new file called StringServer and then modified the code from the NumberServer file in order to create my web server. Besides the name of the file and the code presented everything else is pretty much the same.

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String hello = "Welcome to my website for the lab report\n";
    String string = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return hello + string;
        } else if (url.getPath().equals("/increment")) {
            string = string + string;
            return hello + string;
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    string += parameters[1] + "\n";
                    return hello + string;
                }
            }
            return "404 Not Found!";
        }
    }
}

public class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
With that here we go here is my default page:
![image](https://user-images.githubusercontent.com/56609916/233745834-a51ff56f-ba67-4fa8-a612-87f9d20519de.png)

As you can see a very nice message to bring it allong but let's a few words.
Im going to add:
```
/add-message?s=Hello
```
![image](https://user-images.githubusercontent.com/56609916/233746151-01821313-ee85-4e2c-830e-a56d9604d0d3.png)
You know what let's also add:
```
/add-message?s=How are you
```
![image](https://user-images.githubusercontent.com/56609916/233746584-7d900c20-eb9d-460f-8218-9d06d7dd7cce.png)

If I understand this correctly, whenever we get to this website we use the handle method which in turn uses thr handleRequest inside the string server in order to update the server depending on the url.

As for argument, focusing on the StringServer file, one of the arguments is an url that passes through the handleRequest. When someone, note I don’t say me as I could run this on a server and have someone else access it. The other one is the url that you type in, but I will talk about that later. As for the fields the only ones that seem relevant to me are the hello and stringfield's I implemented, one being the welcome message and the other being a string that gets updated. The other ones that are important but are not used specifically in the StringServer file but are used in the Server file are, the field handler which is the one that starts everything and is the one updated every time somebody visits the page and the port number, which is the one that decides where in the server this website shall be run.

Anyways moving on to the url, which is the one that updates the web server. Whenever we access the webpage we call the good ol handle method which in turn uses the handleRequest in order to update the server. From there the handleRequest, hR in short, uses the getPath method which get’s the path of the url, see picture below.

![image](https://user-images.githubusercontent.com/56609916/236732766-64e00864-3ebf-4c53-90a0-b07d062adcc7.png)

Afterwards depending on the path it does a few things. 

1. If the path is empty then it will just display the whatever words where stored in the string field
2. If the path is ```/increment``` then the whatever contents on the string are doubled and then displayed 
3. If the path is ```/add-message``` the it will add the string in the query and display the screen with the new words, again I will focus on this more later
4. Finally if the path aren’t any of these it will display the classic error of 404 not found

Alright back on track with possibility 3, when the add message path is found things get a bit complicated, first it now has a query, look at the picture above for a reference. The url after the question mark should contain an ```s=<whatever string you want to insert here>``` first this part is divided into 2 parts with the equals sign being the separation point. From there the code checks that the first of the 2 parts is an ```s``` After it confirms that the first part is indeed an s it will add the second part as a new line to the string field. This part won’t need to be parsed as it is already a String, if we needed an int then we would need to parse it. This is what happens when the path is the add-message one.  

---
## Debugging 101

For debugging 101 I'm simply going to focus on the array methods and specifically the reverseInPlace method:
This one here:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
With this in mind we must realize that this program in it's current form, as the cool hip kids will say, is very scuffed. 
> I have already figured out so the screenshot might have some extra code than was shown here as I had to suppress all the corrections I did with comments

The top test will work the bottom one shall not work
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
        @Test 
	public void testReverseInPlace() {
                // This one will work
                int[] input1 = { 3 };
                ArrayExamples.reverseInPlace(input1);
                assertArrayEquals(new int[]{ 3 }, input1);
                // This one will fail the test
                int[] input2 = {1,2,3,4,5};
                ArrayExamples.reverseInPlace(input2);
                assertArrayEquals( new int[]{5,4,3,2,1}, input2);
}
```
This is the picture of the error, as you can see there appears to be a 4 when a 2 was expected meaning that the list wasn't reversed correctly
![image](https://user-images.githubusercontent.com/56609916/233751700-1e0e1ac5-e813-42e4-a2c7-b9049c225349.png)
> Ignore the other 2 tests they are for a different part of the lab

So what happened?

What happened was that the code we have:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

While it has good starting point it has some fundamental flaws:

First of all, for what it's trying to do, it needs a placeholder that will take the earlier object and store it, because as it stands now when the top of the list gets moved in the bottom counterpart the bottom part disappears forever, which is not good.

Second of all it needs a second function that will copy the placeholder value to it’s respective part of the array.

Lastly we need to half the length of the for loop as if we put the arrays length it will first reverse the array and then just flip it back.

With all of those corrections the code looks like this:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int placeHolder = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = placeHolder;
    }
  }
```
Testing the code one more time yields this result:
![image](https://user-images.githubusercontent.com/56609916/233812032-88be8a5b-1dbb-46c1-b979-91a56bd63c17.png)

> Once again I must ask you to ignore the other 2 tests that were successful

---
## Things I learned

Compared to the other parts of this lab report this one will be short and sweet:

There are 2 things that I stood out to me on lab 3:
1. Test small
2. Test everything

What I mean by test small is that test on small data sets as if something doesn't work out when it's small it's most likely not going to work when it's a big data set.
The second one of testing everything means that in some of the things such as linked lists, there are several components that are updated when you use a method, so in those cases tests that everything gets updated. 

With all of that this lab report has come to an end, stay hydrated and good luck with whatever you are currently doing.
