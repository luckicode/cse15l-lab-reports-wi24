# Lab Report 4 #

---
## Step 4: Log into ieng6 ##

We open our terminal in vscode using the shortcut `CTRL + ' `. Now we have to login to the ieng6 machine. There isn't really much shortcuts we can do here just type in the command `ssh isrobles@ieng6-201.ucsd.edu`, in order to login. 
Once I had everything typed in I pressed `<ENTER>`

```
defin@BOOK-NGRBMV3GI4 MINGW64 ~
$ ssh isrobles@ieng6-201.ucsd.edu
Last login: Mon Feb 26 22:23:38 2024 from 128.54.233.2
quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-01-12_0010: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/ieng6/cs120wi24/cs120wi24dx/.snapshot/hourly.2024-01-29_1201: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-02-04_0010: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-02-05_0010: Stale file handle
Hello isrobles, you are currently logged into ieng6-201.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   19:50:01   20  0.48,  0.31,  0.41
ieng6-202   19:50:01   16  0.00,  0.07,  0.12
ieng6-203   19:50:01   6   0.85,  0.32,  0.22

 

To begin work for one of your courses [ cs15lwi24 ], type its name 
at the command prompt.  (For example, "cs15lwi24", without the quotes).

To see all available software packages, type "prep -l" at the command prompt,
or "prep -h" for more options.
```

---

## Step 5: Clone your fork of the repository from your Github account (using the SSH URL) ##

Once again there really isn't any special shortcuts we can, use `git clone` and paste in the SSH URL after to perform the cloning the full command I typed in was `git clone git@github.com:luckicode/lab7.git`. After `git clone` I used `CTRL + V` to paste in the url previously copied from the writeup, which was done using `CTRL + C`. Once you got everything in click `<enter>` 
```
[isrobles@ieng6-201]:~:100$ git clone git@github.com:luckicode/lab7.git
Cloning into 'lab7'...
remote: Enumerating objects: 58, done.
remote: Total 58 (delta 0), reused 0 (delta 0), pack-reused 58
Receiving objects: 100% (58/58), 376.39 KiB | 230.00 KiB/s, done.
Resolving deltas: 100% (21/21), done.
```

---

## Step 6: Run the tests, demonstrating that they fail ##

In order to run the tests, first we want to move into the correct directory. In order to do this I typed in `cd` and then the letter `L` followed by `<TAB>` to autocomplete the rest of the command `lab7`. We have no other folders that started with the letter L so this just autocompletes without any issues and we click `<ENTER>` to run the command. `cd lab7/`.
```
[isrobles@ieng6-201]:~:101$ cd lab7/
[isrobles@ieng6-201]:lab7:102$
```

Next we're gonna have to compile / run the tests. Using the writeup from lab4, we can copy the command needed to compile everything. We copy the command using `CTRL + C` and paste it using `CTRL + V`. (`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` is the command). Once it's pasted in we click `<ENTER>` to run the command. This will then compile everything, the terminal doesn't return anything back after compiling, but it definitely still worked. 
```
[isrobles@ieng6-201]:lab7:102$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
[isrobles@ieng6-201]:lab7:103$
```

Next we're gonna run the file with the tests in it. Once again we can copy the command from the writeup we just need to change a couple things in order to run it on the file we want for this situation. We copy the command using `CTRL + V` and paste it using `CTRL + V` `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore`. After pasting it in, we still need to add a litle bit more to command. Already being at the end of the paste we simply add a space by pressing the spacebar, and then type in the letter L followed by `<TAB>` this will autocomplete and give `ListExamples`, but we want to run it on the test file so we type in a capital T and then click `<TAB>` again to get `ListExamplesTests` autocompleted. This gives us the full command we want and we click `<ENTER>` to run the command. `(java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests)`

```
[isrobles@ieng6-201]:lab7:103$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests 
JUnit version 4.13.2
..E
Time: 0.517
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at ListExamples.merge(ListExamples.java:44)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1
```

This lets us see which tests are failing and how many total.

---

## Step 7: Edit the code file to fix the failing test ## 

To fix this tests we are gonna use `vim` to edit the code directly in the terminal. In order to do so we will type `vim` followed by the letter L and then we can type in the letter L followed by clicking `<TAB>` to autocomplete `ListExamples`. We then type in .java to complete the entire command and so we can just hit `<ENTER>` in order to open the file in vim. `vim ListExamples.java`. 

Once in the file we can see that we need to change line 44. `index1` in that line should be changed to index2. We can use our knowledge of vim to type a command that allows us to quickly do this change. I hold down `SHIFT>` and then hit `:` on my keyboard in order to enter the command line mode. we can then type this command in `:44s/index1/index2/` and hit `<ENTER>` after to run it. We can then see that line 44 was edited and index1 was changed to index2. This is the only edit we need to make so we can save and exit by once again entering the command line mode by holding down `<SHIFT>` and pressing `:`. We then type in `wq` to save and exit.


---

## Step 8: Run the tests, demonstrating that they now succeed ## 

Now we will run the tests again to show that our edit worked. We can go back to the previous compile command we used at the start by pressing the up arrow key twice `<UP>` `<UP>`, and then we click `<ENTER>` to compile. We then go back to the command to run the tests by pressing the up arrow key twice again `<UP>` `<UP>` and then click `<ENTER>` to run the command. This will run the test file `ListExamplesTests` and show us that the tests are now passing.

```
[isrobles@ieng6-201]:lab7:108$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
[isrobles@ieng6-201]:lab7:109$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
JUnit version 4.13.2
..
Time: 0.012

OK (2 tests)
```

---

## Step 9: Commit and push the resulting change to your Github account (you can pick any commit message!) ##

Next we will run the command that directly commits our changes into our forked project. There's not really any shortcuts when typing this command we just have to do it directly. ` git commit -a -m "debugged listexamplestests" `. The `-m` flag is used to add a commit message directly through the terminal. After we type it in we click `<ENTER>` to run it.

```

[isrobles@ieng6-201]:lab7:112$ git commit -a -m "debugged listexamplestests"                    
[main a9f9afa] debugged listexamplestests
 Committer: Isaac Robles <isrobles@ieng6-201.ucsd.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+), 1 deletion(-)


```
Next we will run the command that pushes the commited changes. Once again, there's no shortcuts to do this we just have to type it in and then click `<ENTER>` to run it.
```
[isrobles@ieng6-201]:lab7:113$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 304 bytes | 304.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:luckicode/lab7.git
   327ab1a..a9f9afa  main -> main
```

---

  


