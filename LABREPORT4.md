# Lab Report 4 - Week 7 (Vim)

## Doing it All From the Command Line

**Step 1: Log into ieng6**

* In the bash terminal, enter `ssh cs15lsp23__@ieng6.ucsd.edu`
  *  `__` is your unquie two letters 
* Since the bash credential is already set up in the remote server, entering a password should not be necessary

![Image]()

**Step 2: Clone your fock of the respositroy from your Github account**

* Clone the repository from remote
  * Copy the ssh link of the remove repository from the your Github account
  * Type `git clone` into the terminal with the copied link after it (`git clone <right click>`)

![Image]()

**Step 3: Run the tests, Demonstrating that they fail**

* cd into the lab7 folder (`cd lab7`)
* Run the tests (two different ways both give the same result)
 
  1. Copy and paste these commands
 
     ```
     javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
     java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
     ```
  
  2. Type this command `bash test.sh`




