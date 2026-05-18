# 🐚 Bash Language Cheat Sheet & Notes

Welcome to your Bash scripting reference! This guide covers essential Bash commands, scripting techniques, file operations, and handy tips for both beginners and advanced users.

---

## 📁 Table of Contents

- [🐚 Bash Language Cheat Sheet \& Notes](#-bash-language-cheat-sheet--notes)
  - [📁 Table of Contents](#-table-of-contents)
  - [Basic Commands](#basic-commands)
  - [File Operations](#file-operations)
  - [Pattern Matching \& Searching](#pattern-matching--searching)
  - [Redirection \& Pipes](#redirection--pipes)
  - [Variables \& Parameters](#variables--parameters)
  - [Functions](#functions)
  - [Conditionals \& Loops](#conditionals--loops)
  - [Arrays \& Associative Arrays](#arrays--associative-arrays)
  - [Process Substitution \& Expansion](#process-substitution--expansion)
  - [Error Handling \& Exit Codes](#error-handling--exit-codes)
  - [Debugging \& Shell Options](#debugging--shell-options)
  - [String Manipulation](#string-manipulation)
  - [Advanced Tools: cut, tr, sed, awk, grep](#advanced-tools-cut-tr-sed-awk-grep)
  - [Vim Editor Cheat Sheet](#vim-editor-cheat-sheet)
  - [Miscellaneous Tips](#miscellaneous-tips)
  - [📚 References](#-references)

---

## Basic Commands

- **Aliasing:**  
  ```bash
  alias rm='rm -i' # -i for interactive mode
  ```
- **Hidden Files:**  
  Files starting with `.` are hidden.  
  ```bash
  ls -a
  ```

---

## File Operations

- **Check file type:**  
  ```bash
  file file1.txt
  ```
- **Find files/directories:**  
  ```bash
  find . -type d         # directories
  find . -type f -name "*.txt"
  find /usr/share -type f -name '*.txt' -exec echo "Found: {}" ';'
  ```

---

## Pattern Matching & Searching

- **grep:**  
  ```bash
  grep "word" file.txt
  grep -A1 bat file.txt   # 1 line after match
  grep -B1 bat file.txt   # 1 line before match
  grep -i bat file.txt    # case-insensitive
  grep -o bat file.txt    # only matching part
  ```
- **which, type:**  
  ```bash
  which cd
  type history
  type -a ls
  ```
- **compgen:**  
  ```bash
  compgen -b   # list built-in commands
  ```

---

## Redirection & Pipes

- **Redirect output:**  
  ```bash
  echo hello > file.txt   # overwrite
  echo hello >> file.txt  # append
  ```
- **Pipe status:**  
  ```bash
  cat file.txt | grep "pattern" | sort
  echo "${PIPESTATUS[@]}"   # exit codes of each command in pipeline
  set -o pipefail           # pipeline fails if any command fails
  ```

---

## Variables & Parameters

- **Declare variables:**  
  ```bash
  name='Harsha'
  uname=$(uname)
  echo "hello $name"
  ```
- **Special parameters:**  
  ```bash
  $0  # script name
  $1  # first argument
  $@  # all arguments (as separate words)
  $*  # all arguments (as single word)
  $#  # number of arguments
  $$  # PID of current shell
  $!  # PID of last background process
  $?  # exit code of last command
  $-  # current shell option flags
  ```
- **Parameter expansion:**  
  ```bash
  echo "${name:-default}"   # default if unset
  echo "${name:?error}"     # error if unset
  echo "${#name}"           # length
  echo "${name:1:3}"        # substring
  ```

---

## Functions

- **Define and use functions:**  
  ```bash
  greet() {
    echo "Hello $1"
  }
  greet "Harsha"
  ```
- **Return codes:**  
  ```bash
  my_func() {
    echo "I am output"
    return 42
  }
  my_func
  echo $?   # 42
  ```

---

## Conditionals & Loops

- **If statements:**  
  ```bash
  if [[ -f greet ]]; then
    echo "File exists"
  fi
  ```
- **For loop:**  
  ```bash
  for name in "$@"; do
    echo "Hello $name"
  done
  ```
- **While loop:**  
  ```bash
  while read -r data || [[ -n "$data" ]]; do
    echo "$data"
  done
  ```

---

## Arrays & Associative Arrays

- **Indexed array:**  
  ```bash
  array=(foo bar baz)
  echo "${array[@]}"
  echo "${#array[@]}"
  ```
- **Associative array:**  
  ```bash
  declare -A arr
  arr[1]="item1"
  arr[2]="item2"
  echo "${arr[1]}"
  echo "${!arr[@]}"   # keys
  ```

---

## Process Substitution & Expansion

- **Command substitution:**  
  ```bash
  thing=$(whoami)
  ```
- **Process substitution:**  
  ```bash
  while read -r word; do
    echo $word
  done < <(grep d /usr/share/dict/words)
  ```
- **Brace expansion:**  
  ```bash
  echo "filename."{txt,mov,jpeg}
  ```

---

## Error Handling & Exit Codes

- **Exit codes:**  
  - `0` = success, non-zero = failure
  - Use `set -e` to exit on any error
- **Redirect stderr:**  
  ```bash
  command 2> error.log
  ```
- **Return vs output:**  
  Output is printed, return code is for control flow.

---

## Debugging & Shell Options

- **Debug mode:**  
  ```bash
  set -x   # enable
  set +x   # disable
  bash -x script.sh
  ```
- **Check syntax:**  
  ```bash
  bash -n script.sh
  ```
- **ShellCheck:**  
  ```bash
  shellcheck script.sh
  ```

---

## String Manipulation

- **Case conversion:**  
  ```bash
  s="Harsha"
  echo "${s^^}"   # uppercase
  echo "${s,,}"   # lowercase
  ```
- **Replace:**  
  ```bash
  echo "${s/a/o}"    # first a → o
  echo "${s//a/o}"   # all a → o
  ```
- **Substring:**  
  ```bash
  echo "${s:1:5}"
  ```

---

## Advanced Tools: cut, tr, sed, awk, grep

- **tr:**  
  ```bash
  echo $PATH | tr : '\n'
  ```
- **cut:**  
  ```bash
  cut -d , -f 2 file.csv
  ```
- **sed:**  
  ```bash
  sed 's/old/new/' file.txt
  ```
- **awk:**  
  ```bash
  awk -F: '{ print $1 }' /etc/passwd
  ```
- **grep:**  
  See [Pattern Matching & Searching](#pattern-matching--searching)

---

## Vim Editor Cheat Sheet

> Run `vimtutor` for an interactive tutorial.

| Command | Usage |
|---------|-------|
| `:w`    | Save file |
| `:q`    | Quit |
| `:wq`   | Save and quit |
| `i`     | Insert mode |
| `Esc`   | Normal mode |
| `dd`    | Delete line |
| `yy`    | Copy line |
| `p`     | Paste |
| `/pattern` | Search forward |
| `n`     | Next match |

See full Vim cheat sheet in the original notes above.

---

## Miscellaneous Tips

- **Sourcing files:**  
  ```bash
  source ./helpers.sh
  . ./helpers.sh
  ```
- **Globbing:**  
  ```bash
  ls *.txt
  ```
- **Extended globbing:**  
  ```bash
  ls ?(name1|name2).txt
  ```
- **Named pipes:**  
  ```bash
  mkfifo mypipe
  ```

---

## 📚 References

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)
- [ShellCheck](https://www.shellcheck.net/)
- [Vim Documentation](https://www.vim.org/docs.php)

---

Happy scripting! 🚀
