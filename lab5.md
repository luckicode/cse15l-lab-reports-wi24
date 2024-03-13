# Lab Report 5 #

---


### Help with lab!!!! <span style="color:gray; font-size:small;">#420</span> ###

Anonymous  
*Posted 2 hours ago in Lab Reports*

I need some help with this lab, I made the script as said in the lab that is supposed to take github links and check if a certain file is contained and if it compiles correctly, but it seems like the file checking part isn't working. The github link I'm checking using my bash script is saying that the file isn't being found, but I know it should be finding it, here's what is happening in the terminal.

```
$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3
Finished cloning
File ListExamples.java not found
```

### 1 Answer ###
Isaac Robles <span style="background-color: yellow; font-size: 70%;">STAFF</span>  
<span style="color: gray; font-style: italic;">2 minutes ago</span>

It seems like there might be a problem with how you wrote the part of the script that is supposed to clone files. Aren't you missing information that should show up when something is successfully cloned?

---

```
defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/list-examples-grader (main)
$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3
Cloning into 'student-submission'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
Finished cloning
File found
Program compiled sucessfully!
```

Previous Buggy Code: 
```
git clone student-submission
```

It seems like the bug here was that `student-submission` was beign interpreted as the repository URL, and so nothing was actually being cloned. In order to fix this we have to add a `$1` that will take the link as an input correctly and clone correctly.

---

Corrected Code Down Below:
```
git clone $1 student-submission
```
---

Contents of file before fixing bug:
```
CPATH=".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar"

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone student-submission

echo 'Finished cloning'
if [[ -f "student-submission/ListExamples.java" ]]; then
    echo "File found"
else 
    echo "File ListExamples.java not found"
    exit 1
fi 

cp student-submission/ListExamples.java grading-area/
cp TestListExamples.java grading-area/
cp -r lib grading-area

cd grading-area
javac -cp $CPATH *.java

if [ $? -ne 0 ]; then
    echo "Compilation error!"
    exit 1
fi

echo "Program compiled sucessfully!"





# what if theres a 

# Draw a picture/take notes on the directory structure that's set up after
# getting to this point

# Then, add here code to compile and run, and do any post-processing of the
# tests
```
Contents after fixing bug:
```
CPATH=".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar"

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission

echo 'Finished cloning'
if [[ -f "student-submission/ListExamples.java" ]]; then
    echo "File found"
else 
    echo "File ListExamples.java not found"
    exit 1
fi 

cp student-submission/ListExamples.java grading-area/
cp TestListExamples.java grading-area/
cp -r lib grading-area

cd grading-area
javac -cp $CPATH *.java

if [ $? -ne 0 ]; then
    echo "Compilation error!"
    exit 1
fi

echo "Program compiled sucessfully!"





# what if theres a 

# Draw a picture/take notes on the directory structure that's set up after
# getting to this point

# Then, add here code to compile and run, and do any post-processing of the
# tests
```

The main folder we were in for all this was List-Examples-Grader. When bashing our grade.sh script our directory should be `defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/list-examples-grader`

The command that triggered the bug was `$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3`.


---

# Part 2:

I'd say what we were learned about VIM was extremely helpful for this second half of the quarter. Prior to this class I had no idea what VIM was and being introduced to it I feel like will be important in my career as a computer scientist. I can imagine myself really getting down those shortcuts that exist when using VIM and being able to improve my producvity when coding by a lot. 

