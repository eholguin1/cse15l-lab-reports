# Lab Report 5 - Week 9 (Putting It All Together)

## Debugging Scenario 

A student getting errors on an assignmnet in 15L and needs help with debugging the errors and posted a post on EdStem asking for help:

**What enviornment are you using (computer, operating system, web browser, terminal/editor, and so on)?**

> Mac (operating system), VSCode (terminal/editor)

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. 
Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**

> As I was working on the grade.sh file for lab6 with the new modified code from the [Skill Demo 2](https://github.com/ucsd-cse15l-s23/grader-skill-demo2) repository, when I tried to run the bash script from the repository [list-examples-duplicates](https://github.com/ucsd-cse15l-s23/list-examples-duplicates) the results was that my code was successfull in cloning and finding ListExamples.java in the student-submission. In the terminal, it displayed that *Finished cloning* and *ListExamples.java found* after running the bash script.

> The error that I faced was when running grade.sh output syntax errors for TestListExamples.java which was a file that was cloned before in the skill demo 2. As the results displaced the score of '/' at the end. The correct output of the script is that it should successfully run for the test in TestListExamples.java to test the ListExamples.java file and for all the test to be successful. 

![Image]()
![Image]()

**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, 
command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**

> The command that I am using is `bash grade.sh https://github.com/ucsd-cse15l-s23/list-examples-duplicates` as the output should be that all the test passed. With bad implementation the test should fail in the TestListExamples.java if it was checking for two letters that are same in two lists that are being put together. 

## TA response: 
This is a very interesting error. The first thing to try is using grade.sh with a reposiity that does not have ListExamples.java at all and see what the output would be. As well as make sure the echos statements are correct in the first place. One error that could be causing this issue is how you are checking if ListExamples.java is contained in student-submission. Usually, students mix up `-f` and `find` commands that could be causing this error. So make sure you know the differences between these commands. 

## Student's response and Using advice: 
Thank you for the advice as the error was about the mix up with `-f` and `find` command as I was using the `find` command which results in the paths of the file we are searching for. While `-f` command will return a boolean which is what we need of the if statment to work correctly. I did try with another responsity that did not have ListExamples.java and the output was that *ListExample.java found* which is not true. With chaning the command to `-f` my code results in the correct output shown below. 

![Image]()

## Setup:
* File & Directory needed
  * [Grader-skill-demo2 repository](https://github.com/ucsd-cse15l-s23/grader-skill-demo2)
  * [List-examples-duplicates file](https://github.com/ucsd-cse15l-s23/list-examples-duplicates) (used for testing)
  * [List-examples-no-file file](https://github.com/ucsd-cse15l-s23/list-examples-no-file) (used for testing)
* Contents of each file *before* fixing the bug
  *  Modifed `grade.sh`

```
    CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'
rm -rf student-submission
rm -rf grading-area
 mkdir grading-area
git clone $1 student-submission
echo 'Finished cloning'
if [[ `find student-submission/ListExamples.java` ]]
then
  echo 'ListExamples.java found'
else
  echo 'ListExamples.java not found'
  echo 'Score: 0/4'
  exit 1
fi
cp student-submission/ListExamples.java ./grading-area
cp TestListExamples.java grading-area/
cp -r lib grading-area/
cd grading-area
javac -cp $CPATH *.java
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > junit-output.txt
# The strategy used here relies on the last few lines of JUnit output, which
# looks like:
# FAILURES!!!
# Tests run: 4,  Failures: 2
# We check for "FAILURES!!!" and then do a bit of parsing of the last line to
# get the count
FAILURES=`grep -c FAILURES!!! junit-output.txt`
if [[ $FAILURES -eq 0 ]]
then
  RESULT_LINE=`grep "OK " junit-output.txt`
  PASSED=${RESULT_LINE:4:1}
  TOTAL=$PASSED
else
  # The ${VAR:N:M} syntax gets a substring of length M starting at index N
  # Note that since this is a precise character count into the "Tests run:..."
  # string, we'd need to update it if, say, we had a double-digit number of
  # tests. But it's nice and simple for the purposes of this script.
# See, for example:

# https://stackoverflow.com/questions/16484972/how-to-extract-a-substring-in-bash
  # https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Shell-Parameter-Expansi
  RESULT_LINE=`grep "Tests run:" junit-output.txt`
  COUNT=${RESULT_LINE:25:1}
  TOTAL=${RESULT_LINE:11:1}
  PASSED=$(echo "($TOTAL-$COUNT)" | bc)
  echo "JUnit output was:"
  cat junit-output.txt
fi
echo ""
echo "--------------"
echo "| Score: $PASSED/$TOTAL |"
echo "--------------"
echo ""
```

  * No changes to the other files as they were kept the same
* Full Command Lines, you ran to trigger the bug
  * `bash grade.sh https://github.com/ucsd-cse15l-s23/list-examples-duplicates`
* Description of what to edit to fix the bug
  * Rewrote the if statement condition to use the `-f` command and not the `find` command 
  * `find student-submission/ListExamples.java` changed to `-f student-submission/ListExamples.java`

## Reflection 
One thing that I learned in the second half of the quarter was the test editor Vim as I have never heard about it before and after using it, it seems like it can be very helpful in the future to edit files. As it is kind of shocking that you can edit a file in the command line and not having to open anything else. I like how there are many differnt shortcut in Vim to make editing faster and not having to leave the keyboard. 
