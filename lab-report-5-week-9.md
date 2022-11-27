# Advaith Modali - Lab Report 5 Week 9 (Grade Script)

## Script Code

`grade.sh`

```
rm -rf student-submission

git clone $1 student-submission

cd student-submission/

if [[ -f "ListExamples.java" ]] 
then
    echo "File was found."
else 
    echo "FAIL"
    echo "File was not found in directory"
    echo "Grade: 0"
    exit
fi

cd ..

cp TestListExamples.java student-submission/

cd student-submission/
javac -cp .:/users/advaith/Documents/GitHub/list-examples-grader/lib/hamcrest-core-1.3.jar:/users/advaith/Documents/GitHub/list-examples-grader/lib/junit-4.13.2.jar *.java 2> error.txt

if [[ $? -eq 0 ]]
then
    echo "COMPILE SUCCESSFUL"
else
    echo "COMPILE ERROR"
    echo "$(cat error.txt)"
    echo "Grade: 0"
    exit
fi

java -cp .:/users/advaith/Documents/GitHub/list-examples-grader/lib/hamcrest-core-1.3.jar:/users/advaith/Documents/GitHub/list-examples-grader/lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > junit.txt

cat junit.txt

echo "$(grep -c "Failures:" junit.txt) points lost"

```

## Submission Screenshots

1. Submission for repository https://github.com/ucsd-cse15l-f22/list-methods-corrected

![Image](submission2.png)


2. Submission for repository https://github.com/ucsd-cse15l-f22/list-methods-signature

![Image](submission1.png)

3. Submission for repository https://github.com/ucsd-cse15l-f22/list-methods-lab3

![Image](submission3.png)


## Script Tracing

We will be performing script tracing on the first submission for the repository with the link https://github.com/ucsd-cse15l-f22/list-methods-corrected.

Line By Line Analysis:

For this specific repository, the lines that don't run are the following:
```
else 
    echo "FAIL"
    echo "File was not found in directory"
    echo "Grade: 0"
    exit
else
    echo "COMPILE ERROR"
    echo "$(cat error.txt)"
    echo "Grade: 0"
    exit
```

Such lines do not run because for the provided repository, it passes every one of our checks and does not need to exit the script at any point due to this. 


Lines that do run: 

`rm -rf student-submission`

For this, the standard output and error are both empty because this command is known as 'silent.' What this means is that it performs its operation without yielding stdout and stderr. Its purpose is to remove by force a directory called student-submission, thereby deleting all of its contents and its presence in a file system as well. 

The return code would be 0 for this command. 

`git clone $1 student-submission`

For this, the return code was zero since for this specific repository, there were no errors in running the command.

Standard Output: `Cloning into 'student-submission'...`
Standard Error: None

`cd student-submission/`

This command is similar to the first line in that it is silent. The purpose of this command is to change the working directory to student-submission. No output is given when executing this command, and we are simply taken to that directory. The return code would be 0 for this command. 

`if [[ -f "ListExamples.java" ]]`

For this line, there is an if statement and for the repository we are working with, the condition is true because there does indeed exist a file with the name ListExamples.java inside the student-submission directory we are working within. 

```
then
    echo "File was found."
```

In this segment, it is based on the if statement above. For our case, since the condition is true, we will execute the echo command. 

Standard Output: `File was found.`
Standard Error: None

The return code would be 0 for this command. 

```
cd ..

cp TestListExamples.java student-submission/

cd student-submission/

```

All three of these commands are silent and have neither standard output nor standard input due to their silent nature. The first command just takes you one directory backwards. The second command takes the TestListExamples.java file and copies it into the student-submission directory. The final command changes the working directory to student-submission. For all three of these commands, the return code is 0.

`javac -cp .:/users/advaith/Documents/GitHub/list-examples-grader/lib/hamcrest-core-1.3.jar:/users/advaith/Documents/GitHub/list-examples-grader/lib/junit-4.13.2.jar *.java 2> error.txt`

This command has no standard output nor standard error because it serves to redirect a command into a file called error. For the purposes of this repository it compiles and copies files in a lib folder to import necessary files to run JUnit tests on the student's submission. The stderr from this is then redirected into error.txt. We do not get any output from this, as we merely are redirecting the output of one file into another. The same works for standard error as well since there is no problem in executing the command. The return code is 0 here. 

`if [[ $? -eq 0 ]]`

For this if statement, the condition is true, since we mentioned above, the return code is 0 and that is precisely what is being checked here. Therefore, only the command under the `then` keyword and above the `else` keyword will run. 

```
then
    echo "COMPILE SUCCESSFUL"
```

This must run since the condition in the if statement is true. 

Standard Output: `COMPILE SUCCESSFUL`
Standard Error: None

The return code is 0 here as well. 

`java -cp .:/users/advaith/Documents/GitHub/list-examples-grader/lib/hamcrest-core-1.3.jar:/users/advaith/Documents/GitHub/list-examples-grader/lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > junit.txt`

This command has no standard output nor standard error because it serves to redirect a command into a file called junit.txt. For the purposes of this repository it uses files in a lib folder to import necessary files to run JUnit tests on the student's submission. We do not get any output from this, as we merely are redirecting the output of one file into another. The same works for standard error as well since there is no problem in executing the command. The return code is 0 here. 

`cat junit.txt`

Standard Output:
```
JUnit version 4.13.2
..
Time: 0.006

OK (2 tests)
```
Standard Error: None

The return code is 0.

`echo "$(grep -c "Failures:" junit.txt) points lost"`

Standard Output: `O points lost`

Standard Error: None

The return code is 0.





