# Lab Report 4, Speeding from step 4 to 9
Okay, it's back to being not bad.

This entry deals with the steps of doing the tasks on Week 7's page after the timer started.

## Step 4 - Log into ieng6

`<up><enter>` 
  
Using the history of the terminal, you can easily access your previous ssh command into the ieng6 server. `ssh cs15lwi23atx@ieng.ucsd.edu` is the command to login with the ieng6 part to specify the server. 
  
  ![image](https://user-images.githubusercontent.com/45048652/221386304-935ddd8e-6073-4071-9caf-b5120fc03f10.png)

## Step 5 - Clone your fork of the repository from your Github account 

`<up><up><up><up><up><up><enter>` 

Again, through the use of the terminal, access the command `git clone git@github.com:ZenoCS-Git/lab7.git` to clone the repository for lab 7 using the ssh link. You can also use `rm -rf lab7/` to remove the previous attempt and make sure you forked the respository. 

![image](https://user-images.githubusercontent.com/45048652/221387396-1b05e5c7-3135-4981-9556-828c9e893079.png)

## Step 6 - Run the tests, demonstrating that they fail 

`cd la<tab><enter>`

`<up><up><up><up><up><up><up><enter>`

`<up><up><up><up><up><up><up><enter>`

Run `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` from the history to compile the java files and `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` from the history to run the tests. Use `<tab>` to autofill the path of cd into the folder.

![image](https://user-images.githubusercontent.com/45048652/221388003-e66f8d04-1167-4977-9785-16e32c249b3f.png)

## Step 7 - Edit the code file to fix the failing test

`nano Lis<tab>.java<enter>` 

`<ctrl>w index1 +=<enter><ctrl>w<enter><ctrl>w<enter><right><right><right><right><right><right><delete>2<ctrl>O<enter><ctrl>x`

Using `nano ListExamples.java`, we open up the nano text editor. By repeating `<ctrl>w<enter>`, we get to the error and change the 1 to a 2. `<ctrl>o<enter>` saves the changes made and `<ctrl>x` exits the nano editor.

![image](https://user-images.githubusercontent.com/45048652/221388226-9421dc8c-5cf0-47c8-8c5d-7fca0a88b55d.png)

## Step 8 - Run the tests, demonstrating that they now succeed 

`<up><up><up><enter>`

`<up><up><up><enter>`

Use the same `javac` and `java` command form step 6 to run the tests and see that they passed.

![image](https://user-images.githubusercontent.com/45048652/221388296-9cb7fb98-13f1-474e-8d97-3f2fee48f2bd.png) 

## Step 9 - Commit and push the resulting change to your Github account 

`git add List<tab>.java<enter>` 

`git commit -m "updated"<enter>`

`git push<enter>` 

Using `git add` we add the changes made to the java file, `git commit` with `-m  "updated"` to setup the commit with a message, and `git push` to save these changes to the repository on git. 

![image](https://user-images.githubusercontent.com/45048652/221388417-6a194fbc-e0ce-441e-bf2c-d7c24efc1794.png)

