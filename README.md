# **Bash Lanugage**

> **some basic commands:**
```bash\
  #1. aliasing
  $ alias rm='rm -i # i refers interactiveness  
   ```
Any file starts with ***'.'*** that file is considered as **hidden file**. inorder to find the hidden file in the terminal, we need to use **-a** in **ls** command
```bash
   $ ls -a
```
Pattern Matching and searching in the command-Line
```bash
    $ grep "word" "location"
```
writing to the file
```bash
    $ echo hello > file.txt # > override the file 
    $ echo hello >> file.text # append the file 
```
**grep** command:
```bash
    $ grep bat file.txt # finding the bat in the file
    $ grep -A1 bat file.txt # return one line after 'bat' and 'B' represents before line
    $ grep -i bat file.txt # -i : case-insensitive and -o prints only that matches 
```

**paging files**
```bash
    $ less  filename # use q for quit and / for searching in the collon at the end 
    $ more filename
    $ cat filename | less
    $ cat filename | grep bat | less
```

**man** command
man command allow us to read the mannual pages of particual command
```bash
    $ man ls
```

**help** command is man equilvalent for man for ***shell built-in command***
```bash
    $ help history
```

**which, type** commands
***which*** only helps to find out the external commands where ***which*** helps to find out internal as well external commands
```bash
    $ which cd # gives the location
    $ type history # tells weater commands belongs to shell or not
    $ type -a ls # tells everyting from a-z
```

**compgen -b** will list-out all the built in commands
```bash
    $ campgen -b # list out all the shell built-in commands
```
 
***data redirection*** in the command:
we can use **'>'** to redirect the ouput of the command into the file
```bash
    $ history > file.txt
```

**file** command:
file command tells which type of file the given arugment or file is
```bash
    $ file file1.txt
```

**tr[translate] command**
tr command will translate the given argument to specifed argument
```bash
    $ echo $PATH | tr : '\n'
    $ history | tr 'abc' 'def' # a -> d, b -> e, c -> f
```

***user and system*** related commands
```bash
    $ whoami
    $ uname # -a will show all the details of the system
    $ echo "$USER"
    $ echo "$MACHTYPE"
    $ echo "$HOSTNAME"
    $ echo "$SHELL"

    #setting our own envionment variable
    $ session=afternoon # echo "$session"

    #modern way of adding with shell commands
    $ session=$(uname -a)

    #unset env variables
    unset session # variable will vanish 
```
 
