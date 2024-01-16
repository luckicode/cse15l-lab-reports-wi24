# Lab Report 1 - Isaac Robles
![Image](cat.png)


# cd <path>

By executing cd without a specified path the directory returns to the orignal directory, in this case that original directory.
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd
[user@sahara ~]$ pwd
/home 
```

In this example I provided, I start off by changing the directory using the `cd` command to `lecture1`. I then ran the `cd` without an argument/path followed by the `pwd` command. This would then show that the directory was changed to the orignal working directory `\home` one after being switched to lecture1.

---
When executing `cd` with a specified path when you run the command in the terminal, you are simply switching from the current directory you are in to the one specifiied. 
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
In this example I provided, we switch the directoy from the home directory to lecture1. We can see that this actually happens by running the `pwd` command after `cd lecture1` as it shows the current directory we are in being `lecture1`

---
By executing the `cd` command to a file we will see an error as the command is not meant to be used on files (quite literally in the full name of the command itself "change directory")
```
[user@sahara ~]$ cd Hello.java
bash: cd: Hello.java: No such file or directory
```

---
---
# ls <path>
By executing the `ls` command on a folder the contents of that folder will be returned back.
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
As we can see the multiples files and folders contained inside lecture1 are returned to us (alphabetical order).

--- 
When executing the `ls` command by itself the active directory will have it's contents listed.
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
```
In this example we had set the active directory to lecture1 and we can then see that what is returned is the same as what we saw earlier when specifying that we wanted to execute the command on the lectur1 folder.

---
When executing the `ls` command on a file the command will not work as intended. The file can't have folders/files contained inside of it and so the only thing returned will be the file specified as an argument.
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
That being said attempting to execute the `ls` command on a folder that is not in the current active directory will also not work.
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls Hello.java
ls: cannot access 'Hello.java': No such file or directory
```

