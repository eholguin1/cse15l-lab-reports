# Lab Report 1
This tutorial will cover remote access to a course-specific account on `ieng6`.

## Installing VS Code
[Download](https://code.visualstudio.com/download) the correct option for your operation system(Windows, mac, etc). 

Once launched, you should see a screen similar to the one below:
![Image](https://github.com/eholguin1/cse15l-lab-reports/blob/main/Screenshot%202023-04-08%20at%206.16.18%20PM.png)

## Remotely Connecting
In this section, we will learn how to use VSCode to connect to a remote computer.

**Set up your course-specific account**

First step is to look up your course-specific account for CSE15L with this link:[ETS](https://sdacs.ucsd.edu/~icc/index.php)
* There, you will find your username, which should look similar to "cs15sp23ii."

**Using `ssh`**

This step is to open VSCode to connect to the remote computer.
1. Open a terminal in VSCode(on Mac, using the menu at the top(Terminal > New Terminal)
2. Using the following command in the terminal:

* `$ ssh cs15lsp23ii@ieng6.ucsd.edu`
  * >"ii" should be replaced with your specific account's username
3. After running the command, you should see an output that looks like this: ``The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
Password: ``
* Type in "yes" which lets you connect to a new server for the first time. After it should ask you for your password that you created in ETS. 
4. Finally, you should see a output similar to the one below:
![Image](




