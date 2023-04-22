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
                if (parameters[0].equals("count")) {
                    string += parameters[1] + "/n";
                    return hello + string;
                }
            }
            return "404 Not Found!";
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

If I understand this correctly, whenever we get to this website we use the handle method and then handleRequest, or I could be wrong but from looking at the code that’s my best guess.

As for arguments like I said before it seems complicated. One of the arguments is an url, that passesthrough the handleRequest and then stuff happens that I don't understand.  As for the feilds the only ones that seem relevent to me are the hello and string feild's I implemented, one being the welcome messeaga and the other being a string that get's updated

As for the ones that change well, the thing that changes is the url path and query that are inputted, and the string who gets updated depending on what is in, in this case both are uptated due to the query I have inputed

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

