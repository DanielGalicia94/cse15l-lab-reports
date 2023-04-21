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




