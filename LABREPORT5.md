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




