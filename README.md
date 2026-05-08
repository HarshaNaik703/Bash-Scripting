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

**yes command**
```bash
    $ yes #unlimited y!!!
```
# 📝 Vim Editor Cheat Sheet

> **Vim Editor** (Vi IMproved), often invoked as `vi`, is a powerful text editor.  
> Run `vimtutor` in your terminal for a beginner-friendly interactive tutorial.

---

## 🚀 Basic Commands (Start, Save, Exit)

| Command        | Usage |
|----------------|------|
| `vi myfile`     | Open file for editing |
| `vi -r myfile`  | Recover file after crash |
| `:r file2`      | Insert contents of file2 at cursor |
| `:w`            | Save file |
| `:w myfile`     | Save as new file |
| `:w! file2`     | Force overwrite file2 |
| `:x` or `:wq`   | Save and exit |
| `:q`            | Quit |
| `:q!`           | Quit without saving |

---

## ⌨️ Insert & Editing

| Key | Usage |
|-----|------|
| `a` | Append after cursor |
| `A` | Append at end of line |
| `i` | Insert before cursor |
| `I` | Insert at beginning of line |
| `o` | New line below and insert |
| `O` | New line above and insert |
| `r` | Replace single character |
| `R` | Replace multiple characters |

---

## ✂️ Delete, Copy, Paste, Undo

| Key | Usage |
|-----|------|
| `x` | Delete character |
| `Nx` | Delete N characters |
| `dw` | Delete word |
| `D` | Delete till end of line |
| `dd` | Delete current line |
| `Ndd` or `dNd` | Delete N lines |
| `yy` | Copy (yank) line |
| `Nyy` or `yNy` | Copy N lines |
| `p` | Paste |
| `u` | Undo |

---

## 🧭 Cursor Movement

| Key | Usage |
|-----|------|
| Arrow keys | Move cursor |
| `j` or `Enter` | Move down |
| `0` | Beginning of line |
| `$` | End of line |
| `w` | Next word |
| `:0` or `1G` | Start of file |
| `:n` or `nG` | Go to line n |
| `G` | End of file |
| `Ctrl + F` | Page down |
| `Ctrl + B` | Page up |
| `Ctrl + L` | Refresh screen |

---

## 🔍 Searching

- `/pattern` → Search forward  
- `?pattern` → Search backward  
- `n` → Next occurrence  
- `N` → Previous occurrence  

---

## ⚡ Must-Know Essentials

- `i`, `a`, `Esc`
- `:w`, `:q`, `:wq`
- `dd`, `yy`, `p`
- `/search`, `n`
- `h j k l` (better than arrow keys)

---
# Bash Programming 

> Must start with shebang!!! notation  
> ```bash
> #!/usr/bin/env bash 
>```  
> ```bash
> bash -n filename #for debugging
> echo $? #which used to get to know the previous command executed successfully or not
>```
> Since we already mentioned in the starting of the file, it's not necessary to use `filename.sh` the extension for the file.  
We can execute bash scripts file in 2 ways:  
    1.` bash filename`  
    2. `./filename` (if the file has permission to execute)  `chmod +x filename`  
   for viewing the file, we can use `cat` or `bat` commands
   
---

# File related Commands  
File related commands help in file operations in the file
```bash
    $ help test
    # for example
    # -f checks file exist or not
    # -N checks if file is modified after last read or not
```

# New line and number notation in the terminal
```bash
    $ echo "hello" | xxd
```
# Reading and Redirecting The Data:

```bash
    $ cat file | bash file
    $ bash file < path  # given the path of the file
    $ < path | bash file # can put syntax anywhere
```

# $ related thing
```bash
    #!/urs/bash/env bash
    # $# tells the number of arguments
    # $@ executes the arguments
    # $1 indicates 1 argument
    # 
```

# File Descriptor  
A file descriptor is an integer that uniquely identifies an open file, socket, or other I/O resource within a process. It abstracts the underlying file system, providing a consistent interface for reading from and writing to resources.

Here some of the common file descriptor  

File Descriptor 0 : Standard Input (stdin)

File Descriptor 1 : Standard Output (stdout)

File Descriptor 2 : Standard Error (stderr)
>This is the exact answer given for file descriptor in "stack overflow"
>>"In simple words, when you open a file, the operating system creates an entry to represent that file and store the information about that opened file. So if there are 100 files opened in your OS then there will be 100 entries in OS (somewhere in kernel). These entries are represented by integers like (...100, 101, 102....). This entry number is the file descriptor. So it is just an integer number that uniquely represents an opened file for the process. If your process opens 10 files then your Process table will have 10 entries for file descriptors."


#### executing or using the command in the program
```bash
    #!/usr/bin/env bash
    thing=`whoami` # use backquote(`) to write the command
    # below command will execute command too
    whoami #!!!
    #this will print the string
    echo `echo `whoami``
```

##### Dollor-parent Notation
```bash
    #!/usr/bin/env bash

    thing=$(whoami)
    echo $(echo $(whoami))
```

# Function
```bash
    #!/usr/bin/env bash
    i=5
    fun() {
        i=10
    }

    var={ fun; } # can modify the global scope, basically `{}` creating the subshell
    fun # fun can amodify the global scope!!!
    # var=$(fun)

    echo "$i" #10
```
# Some important Rules while Programming

1. Leading 0's represent the hexadecimal notation and `10#$a` where a=10 treated as decimal notationn
2. Expressions must write in the `(())` and conidting write in `[[]]`
3. Anything in the right of the pipe is considered as subshell.
4. `<` expects file.
5. `shift` does same job as pop_front
6. If you don't specify the iterable in the for loop , it will loop over the arguments, ` $1, $2, $3....$n`.
7. Scopes in the function, instead of `{}` we can use `()` to avoid scope issues.  
8. `{}` used to pipe the things inside. 


# Process Substitution
Process Substitution executes a command and puts the output into file temporarily

### Points to rem:
1. Process Substitution doesn't have exit code, it will maks the errors
```bash
    while read -r word; do
    echo $word
    done < <(grep d /usr/share/dict/words)
```

# cut and tr

### tr translate one character to another character
```bash 
    $ cat sample.csv | tr , '\t'
```

### cut command used to cut the output to our desire
```bash
    $ cat sample.csv | cut -d , -f 2 # here -d is delimiter and -f is files and numbers are index
    $ cat sample.csv | cut -d , -f 1-4
    $ cat sample.csv | cut -d , -f 1,3,4
    $ cat sample.csv | cut -d , -f 2,3 | tr , '\t'

    $ cut -d : -f 1 /etc/passwd
``` 

# sed , awk and grep

### stream editor is used to edit the string.
```bash
    $ cut -d : -f 1-4 /etc/passwd | sed 's/harsha/buddy/' # we can use '#' to replace '/'
    $ grep harsha /etc/passwd | sed -e 's#harsha#buddy#' -e 's#/bin/bash#/tin/tash#'
```

### awk is a powerful tool for string manipulation 
```bash
    $ cat /etc/passwd | awk '{ print $0 }' # have default delimiter as white space
    $ cat /etc/passwd | awk -F : '{ print $0 }'
    $ cat /etc/passwd | awk -F: '$1=="harsha-naik"{ print $1,$5 }'
    $ < /etc/passwd awk -F: '$1=="harsha-naik"{ print $1, $5 }' # input redirectin
    $ < /etc/passwd awk -F: '{ print $7 }' | sort | uniq 

```

# word count
```bash
    $ man ls | grep file | wc # give output containing word coung , character count and line count
    $ man ls | grep file | wc -l #(-c -w)
```

# find command

### find cmd list out all the files and folders by default 
```bash
    $ find . -type d #for directory d for dir and f for plane files
    $ find . -type f -name "*.txt"
    # exec
    $ find /usr/share -type f -name '*.txt' -exec echo hi I found a file {} hurry ';' # must escape using ';' or '\'  
```

# Bash Arguments

```bash
    $ bash -x file # this puts bash file in debug mode
    $ PS4='[debug]: ' bash file 
    $ bash -n file # gives syntax errors in the file
    $ bash -u file # undefined files
    $ bash -nu file
```
we can also do this by writing `set -x` on top of the bash script.   
we can put `set -x` -> some code -> `set +x` which executes only specified codes.

# shellcheck
shellcheck is used to find the errors in the script
```bash
    $ shellcheck bashfile
```

# pipe status


# time 
### time command used to calculate the time spend to execute the command by the user, system and real


# sourcing (importin) the files

refer 14sourcing and 15importing files

# Curlies and Params

# Return vs Output
Return codes are 8-bit characters in the linux.


