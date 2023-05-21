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

![Image]()

**Step 4: Edit the code file to fix the failing test**

1. To inspect the code, we need to go into `vim` 
 
  * `vim ListExamples.java`
 
  ![Image]()
  
2. To reach the bottom of the file without having to click `<j>` to move down and `<l>` to move to the right
 
  * Do the command `?index` which will put the cursor at the last time "index" is shown in the code file.
  * Then click `enter`

  ![Image]()
  
3. To get to the last letter of "index" 

  * Type `e` which will put you at the end of the word 

  ![Image]()
  
4. To change `index1` to `index2`
 
  * Type `r2` which will change the 1 to 2 

  ![Image]()

5. To save and quit the code file with the new change

  * Type `:wq` which will save the changes and exit vim
  * Then click `enter`

  ![Image]()
  
**Step 5: Run the tests, deonstrating that they now succeed**

* Rerun the tests 
  * `bash test.sh`

![Image]()

**Step 6: Commit and push the resulting change to your Github account**

* Copy and paste these commands into the terminal

```
git remote set-url origin git@github.com:eholguin1/lab7.git
git add *
git commit -m "message"
git push -u origin main
```

![Image]()





