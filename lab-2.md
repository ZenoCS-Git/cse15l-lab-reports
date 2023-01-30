# Lab Report 2, The Server and others from Lab 2 and 3
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

As requested, you are to describe one bug from Lab 3, an exercise to check and find symptoms and bugs. The bug here is if the method properly 
reverses the order of elements in an array.

The Junit Test with Failure-Inducing Input where the data array elements does not equal the reversed order of the array.

```java
@Test 
public void testReverseInPlace2() {
    //yes error
    int[] input2 = { 3, 2, 5 };
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 5, 2, 3 }, input2);
}

```

The Junit Test without Failure-Inducing Input where it does not fail since the reverse order of a 1 element array is the same as the original array.

```java
@Test 
public void testReverseInPlace1() {
    //no error
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}

```

Junit Running and the Symptom that shows an array where the elements do not match indexes. 

![image](https://user-images.githubusercontent.com/45048652/215364671-b4c08ae1-1224-4b39-a178-960e258cbe23.png)


The Before Code (has error located at the for loop and lack of temp variable that help move the elements in the array)

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

The After Code (fixed by adding a /2 in the for loop and a temp variable to help swap element locations)

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
 
# Part 3

I simply was unaware the way in which java can handle hosting a server. The introduction to the server and handler class in lab 2 taught me a great 
deal in which websites work. Specifically, I would like to point out the way the code uses methods that draw and takes in the 
information in the url. It is quite clever in design by which it takes the information and copy it into a string parameter before performing 
operations based on the info. In addition, the way it checks the url also demonstrates how a website can redirect you to a different url if 
you type a certain url.

