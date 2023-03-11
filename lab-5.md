# Lab Report 5, A blast from the past
Okay, it's back to being bad.

This entry deals with Week 9's "For lab report 4 (about doing commands quickly), how could you have done the task very quickly by writing a bash script (even if that was against the rules)"

## Speeding with Bash Script

You first, obviously, want to create a .sh file in the same working directory as the rest of the java and tester files. This means loginning into ieng6 and running the following command 

`touch 1.sh` 

Then you want to `nano dofast1.sh` in order to edit the file and type in the commands for the tasks. You want to include the following lines of code which goes through the steps of [Lab Report 4](lab-4.md) 

```
rm -rf lab7/

git clone git@github.com:ZenoCS-Git/lab7.git

cd lab7/

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

nano ListExamples.java
```

Due to the limitations of nano and bash, you have to manually do the arrows with the keystrokes from lab report 4. There is also the option of simply having a copy of the correct file and copying over the .java file with the error. You can do this by having a corrected version alongside your scripts and include a `cp` command that copies over the file. Though, that seems too much against the rules. If done this way, only one script would be needed. Otherwise, we can run another bash script to the rest of the step. Use `touch 2.sh` to create another .sh file and nano into it. Include these commands that accomplishes the rest of the task. 

```
cd lab7/

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

git add ListExamplesTests.java

git commit -m "updated"

git push
```

Some things to note from this experience. When you run a bash script with a cd into a different directory, your current working directory does not change after the script finishes. Hence why you need to cd into lab7/ again in the second script. 


