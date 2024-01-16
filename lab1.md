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

In this example I provided, I start off by changing the directory using the `cd` command to `lecture1`. I then ran the `cd` without an argument/path followed by the `pwd` command. This would then show that the directory was changed to the orignal home one after being switched to lecture1.

---
By executing `cd` with a specified path when you run the command in the terminal, you are simply switching from the current directory you are in to the one specifiied. 
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
In this example I provide, we switch the directoy from the home directory to lecture1. We can see that this actually happens by running the `pwd` command after `cd lecture1` as it shows the current directory we are in being `lecture1`
