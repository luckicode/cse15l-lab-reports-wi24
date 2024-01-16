# Lab Report 1 - Isaac Robles
![Image](cat.png)


# `cd <path>` (Change Directory)

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
# `ls <path>` (List)
By executing the `ls` command on a folder the contents of that folder will be returned back.
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
As we can see the multiples files and folders contained inside lecture1 are returned to us (alphabetical order).

--- 
When executing the `ls` command without providing an argument, the active directory will have it's contents listed.
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
# `cat <path1> <path2>` (Concatenate)
When executing the `cat` command without providing an argument we run into a problem because the command is meant to be used on a file, when we don't specifiy that said file it is assumed we are using it on the directory which just won't work. The program will then repeatedly ask for a user input and will only be exited by doing `Ctrl + C`.
```
[user@sahara ~/lecture1]$ cat
test
test
test
^C
```
---
When executing the `cat` coommand and providing the name of a folder, we will run into a problem once again because the commoand is meant to be used on files. Terminal will let that be known by telling us that what we attempting to call the `cat` command on was a folder. *In order to use folder names when using the cat command you have to be more specific and specify the name of file in the folder you want to concatenate*
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
// other example
[user@sahara ~]$ cat lecture1/Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
```
---
When executing the `cat` command and providin specific file paths the contents of the file will be returned. *You are able to do this on multiple files, it's not limited to a singular file*
```
[user@sahara ~/lecture1/messages]$ cat en-us.txt ru.txt zh-cn.txt
Hello World!
Привет, мир!
你好世界
[user@sahara ~/lecture1/messages]$ cat en-us.txt ru.txt
Hello World!
Привет, мир!
[user@sahara ~/lecture1/messages]$ cat en-us.txt
Hello World!
```
*As you can see we were able to use the cat command on up to 3 files*

