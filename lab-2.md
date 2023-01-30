# Lab 2-3, The Server and others
Okay, it's sorta bad. 

This blog describes instruction for basic usage of the Server and URL Handler class in java
## Part 1 - The String Server
For this lab report, you were required to make a webpage that can add and display messages by URL. 
Of course, tho, you were surely uneducated and unfamilar with the code so you took a bit to understand 
and add comments to understand every part of the code. 

Below is the code of the StringsServer and comments for many lines explaining the purpose of each. There are also 
some imports required for the code to functiona as well as the provided message that handles the server startup. 

```java
//static variables for the server to keep track 
    String messages = ""; //one long string that track all the messages added using the url with /n between each entry 

    public String handleRequest(URI url) {

        //handles if url path has add-message?s=<some string> that adds strings to messages 

        // url.getPath() grabs the data in the url, specifyly the path exluding domain
        // note, the path is everything from / to ?, excluding the end
        if (url.getPath().equals("/add-message")) { //checks url for /add-message
            //creates an array that stores the info into two elements, the stuff before the = and after
            String[] parameters = url.getQuery().split("="); 

            //adds the string parameter to messages
            if (parameters[0].equals("s")) { //checks if before = is a s
                messages += parameters[1]; //adds the second element data to messages
                messages += "\n"; //adds spacing
                return messages;
            }
            return messages;
        }
            //default return messages
            return messages;
    }
```

Here is an example of the webpage after one run of the URL. 

![image](https://user-images.githubusercontent.com/45048652/215360906-df50d6cd-392c-4654-8eab-0f9046a4c885.png)

The methods that are being called by the example is the .getPath() in order to retrieve the path of "/add-message," a 
.equals to check if the path matches "/add-message," and .getQuery() with .split("=") in order to copy down the url information 
that exist between ? and = as the first element in String array parameter and the information that exist between = and the end of 
the URL for the second element in parameter. 

The code then check these elements in the String array if the first is "s" before adding the second element as part of the single 
string called messages. The code also adds a "\n" for formatting the string for the next entry. The code then returns the messages 
string to be displayed on the webpage. The information passed into the URL is "example message first" or with the spaces replaced 
with %20.

![image](https://user-images.githubusercontent.com/45048652/215361294-101a50fc-4b41-4bd4-85ca-09df2f7efc65.png)

This is the second example when another message is added after the first. It is displayed in a new line to distinct it as a new 
entry to the string messages of the code. The code does the same as the first, checking the URL information before copying 
down the information into a String array to be then added to the messages string that is returned to be displayed. Here, the 
string that is passed to the code is "the following second message" or "the%20following%20second%20message" in the URL.

## Part 2 - One Bug from Lab 3

As requested, you are to describe one bug from Lab 3, an exercise to check and find symptoms and bugs. 

The Junit Test

```java
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);

    int[] input2 = { 3, 2, 5 };
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 5, 2, 3 }, input2);
}

```

Junit Running and the Symptom 

![image](https://user-images.githubusercontent.com/45048652/215363386-d41f5cac-6830-43eb-aa6d-31544a7ebb2b.png)


The Before Code (has error)

```java
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

The After Code (fixed)

```java
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i++ ) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i -1];
      arr[arr.length - i -1] = temp;
    }
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }

```
A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
 
# Step 3 - Trying Some Commands (omg this is where pwd works)

Now you're in the terminal, connected to the other computer, you can now do the stuff the professor been describing :D

That is assuming you were paying attention...

Anyways, here is a refresher on some commands you can try!

![image](https://user-images.githubusercontent.com/45048652/214347778-8003fa48-2703-4525-9a89-cb1baa922cc1.png)


* ls - list the files and folders in the current working directory 
* pwd - check where is the current directory currently located at 
* .. - go backword in the directory to the previous folder and can be combined with cd ..<path> for more complicated movement
* cd <path> - go to specified directory using relative or ~/ absolute paths. note that root directories are treated differently
  
Refer to online notes for more commands.
 
 ![image](https://user-images.githubusercontent.com/45048652/212210168-372982ad-d0ba-483b-af62-7a1126a4418d.png)

 Example of pwd. Also use exit or ctrl + D to logout and end session.
