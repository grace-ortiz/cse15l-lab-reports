# Lab 1 #
### Grace Ortiz ###
For the command `cd`: 
* With *no* arguments:
  ```
  [user@sahara ~/lecture1/messages]$ cd
  [user@sahara ~]$ 
  ```
  With no arguments `cd` returns to the home directory. If already in the home directory, there will be no changes to working directory. The output is not an error.
* With a path to a *directory* as an argument:
  ```
  [user@sahara ~]$ cd lecture1/messages
  [user@sahara ~/lecture1/messages]$ 
  ```
  With a directory as an argument, `cd` changes the working directory accroding to the specified absolute or relative path. The output is not an error.
* With a path to a *file* as an argument:
  ```
  [user@sahara ~/lecture1]$ cd Hello.java
  bash: cd: Hello.java: Not a directory
  ```
  With a file as an argument, `cd` gives the output that the given file is not a directory, and therefore the change directory command will not change to it. The output is not an error.

For the command `ls`:
* With *no* arguments:
  ```
  [user@sahara ~/lecture1]$ ls
  Hello.class  Hello.java  messages  README
  ```
  With no arguments, `ls` prints a list of the contents of the working directory. The output is not an error.
* With a path to a *directory* as an argument:
  ```
  [user@sahara ~/lecture1]$ ls messages
  de.txt  en-us.txt  es-mx.txt  zh-cn.txt
  ```
  With a directory as an argument, `ls` lists the contents of the specified directory. The output is not an error. 
* With a path to a *file* as an argument:
  ```
  [user@sahara ~/lecture1/messages]$ ls de.txt
  de.txt
  ```
  With a file as an argument, `ls` lists the specified file or file path. This is not an error. 

For the command `cat`:
* With *no* arguments:
  ```
  [user@sahara ~/lecture1/messages]$ cat

  ```
  With no arguments, `cat` returns no output and does not return to a new line.
* With a path to a *directory* as an argument:
  ```
  [user@sahara ~/lecture1]$ cat messages
  cat: messages: Is a directory
  ```
  With a directory as an argument, `cat` 
* With a path to a *file* as an argument:
    ```
    [user@sahara ~/lecture1/messages]$ cat en-us.txt
    Hello World!
    ```
