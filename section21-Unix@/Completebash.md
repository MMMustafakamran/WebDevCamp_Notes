# Bash Learning Notes

## 1. What is Bash and the Terminal?

*   **Shell:** A program that takes your commands and tells the operating system what to do. Bash (Bourne Again SHell) is one type of shell, very common on Linux and macOS.
*   **Terminal (or Console/Command Prompt):** The window or interface where you type commands and see output. It runs the shell (like Bash).
*   **Prompt:** The text displayed by the shell indicating it's ready for a command. It often looks like `user@hostname:~/current/directory$` or just `$`. If it's `#`, you're likely logged in as the superuser (root) - **be careful!**

## 2. Core Commands Summary Table

| Command                         | Description                                                  | Common Usage / Options                                       |
| :------------------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **Navigation & Listing**        |                                                              |                                                              |
| `pwd`                           | **P**rint **W**orking **D**irectory (shows your current location). | `pwd`                                                        |
| `ls`                            | **L**i**s**t directory contents.                             | `ls`, `ls -l` (long), `ls -a` (all), `ls -lh` (human-readable) |
| `cd`                            | **C**hange **D**irectory.                                    | `cd <dir>`, `cd ..` (up), `cd ~` (home), `cd -` (previous)   |
| **File & Directory Management** |                                                              |                                                              |
| `mkdir`                         | **M**a**k**e **Dir**ectory (create a new folder).            | `mkdir <directory_name>`                                     |
| `touch`                         | Create an empty file or update its access/modification timestamp. | `touch <filename>`                                           |
| `cp`                            | **C**o**p**y files or directories.                           | `cp <source> <dest>`, `cp -r <dir_source> <dir_dest>` (recursive) |
| `mv`                            | **M**o**v**e or rename files or directories.                 | `mv <source> <dest>`                                         |
| `rm`                            | **R**e**m**ove files. **(Caution: No undo/trash bin!)**      | `rm <filename>`                                              |
| `rmdir`                         | **R**e**m**ove **Dir**ectory (only works if the directory is empty). | `rmdir <directory_name>`                                     |
| `rm -r`                         | **R**e**m**ove directory and its contents recursively. **(Use Extreme Caution!)** | `rm -r <dir_name>`, `rm -rf <dir>` (force - **VERY DANGEROUS**) |
| **Viewing File Contents**       |                                                              |                                                              |
| `cat`                           | Con**cat**enate and display entire file content. Ideal for short files. | `cat <filename>`                                             |
| `less`                          | Display file content one screenful at a time (interactive pager). | `less <filename>` (use arrow keys, PgUp/Dn; `q` to quit)     |
| `head`                          | Display the first few lines of a file (default is 10 lines). | `head <filename>`, `head -n 5 <filename>` (show first 5)     |
| `tail`                          | Display the last few lines of a file (default is 10 lines).  | `tail <filename>`, `tail -n 3 <filename>`, `tail -f <filename>` (follow) |
| **Executing & Scripting**       |                                                              |                                                              |
| `echo`                          | Display text or variable values to standard output.          | `echo "Some text"`, `echo $VARIABLE`                         |
| `chmod`                         | **Ch**ange file **mod**e (permissions).                      | `chmod +x <script_name>` (add execute permission)            |
| **Getting Help**                |                                                              |                                                              |
| `man`                           | Display the **man**ual page for a command.                   | `man <command>` (use `q` to quit)                            |
| `help`                          | Display help information for Bash built-in commands.         | `help cd`, `help echo`                                       |
| `type`                          | Indicate how a command name would be interpreted (builtin, alias, file path). | `type ls`, `type cd`                                         |
| `printenv`                      | **Print** **Env**ironment variables.                         | `printenv`, `printenv HOME`                                  |

## 3. Input/Output Redirection & Pipes (Operators)

These symbols control where input comes from and where output goes.

| Operator    | Name                          | Description                                                  | Example                                    |
| :---------- | :---------------------------- | :----------------------------------------------------------- | :----------------------------------------- |
| `>`         | Redirect `stdout`             | Send standard output (stdout) to a file, **overwriting** the file. | `ls -l > file_list.txt`                    |
| `>>`        | Append `stdout`               | Send standard output (stdout) to a file, **appending** to the end. | `date >> activity_log.txt`                 |
| `<`         | Redirect `stdin`              | Read standard input (stdin) from a file instead of the keyboard. | `sort < unsorted_list.txt`                 |
| `|`         | Pipe                          | Send stdout of the command on the left to the stdin of the command on the right. | `ls -l | grep "\.txt$"`                    |
| `2>`        | Redirect `stderr`             | Send standard error (stderr) messages to a file.             | `find / -name "secret" 2> find_errors.log` |
| `&>`        | Redirect `stdout`/`stderr`    | Send both stdout and stderr to the same file (Bash 4+).      | `./my_script.sh &> script_output.log`      |
| `2>&1`      | Redirect `stderr` to `stdout` | Send stderr to the same destination as stdout (often used with `>`). | `./my_script.sh > script_output.log 2>&1`  |
| `$(...)`    | Command Substitution          | Substitute the output of a command. Preferred modern syntax. | `current_dir=$(pwd)`                       |
| `` `...` `` | Command Substitution          | Substitute the output of a command. Older syntax (avoid if possible). | `current_dir=\`pwd\``                      |

## 4. Variables

You can store data in variables for later use.

*   **Creating/Assignment:** Use `VARIABLE_NAME="value"`.
    *   **Important:** No spaces around the `=` sign.
    *   Convention: Uppercase for environment/global variables (`MY_VAR`), lowercase for script-local variables (`my_var`).
    ```bash
    my_name="Alice"
    file_count=10
    greeting="Hello there, $my_name" # Variables expanded in double quotes
    literal_greeting='Hello there, $my_name' # Variables NOT expanded in single quotes
    ```
*   **Accessing:** Use the dollar sign `$` followed by the variable name: `$VARIABLE_NAME` or `${VARIABLE_NAME}`.
    *   The curly braces `${}` are safer, especially when the variable is next to other characters (e.g., `echo "${my_name}_files"`).
    ```bash
    echo $my_name
    echo "Count: ${file_count}"
    echo $greeting
    echo $literal_greeting
    ```
*   **Command Substitution:** Store the output of a command in a variable.
    ```bash
    current_dir=$(pwd)
    echo "I am in: $current_dir"
    num_files=$(ls | wc -l) # Count files/dirs using wc (word count) -l (lines)
    echo "There are $num_files items here."
    ```
*   **Environment Variables:** Special variables set by the system or your shell configuration. Usually uppercase.
    ```bash
    echo "User: $USER"
    echo "Home Directory: $HOME"
    echo "Search Path: $PATH"
    printenv # Show all environment variables
    ```

## 5. Basic Scripting

A script is simply a file containing Bash commands.

1.  **Create a file:** Use `touch` or a text editor (like `nano`, `vim`, `gedit`, VS Code). Example: `my_script.sh`.
    ```bash
    nano my_script.sh
    ```
2.  **Add the Shebang:** The very first line **must** be `#!/bin/bash` (or similar, like `#!/usr/bin/env bash`). This tells the system which interpreter to use.
3.  **Add commands:** Write your Bash commands line by line. Use `#` for comments.
    ```bash
    #!/bin/bash
    
    # This is a comment
    echo "Hello from my script!"
    echo "Current directory: $(pwd)"
    echo "Script name: $0"
    echo "First argument: $1"
    echo "All arguments: $@"
    
    name="Bash Learner"
    echo "Variable 'name' holds: $name"
    
    echo "Script finished."
    ```
4.  **Save and Exit:** (In `nano`: `Ctrl+X`, then `Y`, then `Enter`).
5.  **Make it Executable:** Grant the script permission to run.
    ```bash
    chmod +x my_script.sh
    ```
6.  **Run the Script:** Execute it from the terminal.
    ```bash
    ./my_script.sh # Run without arguments
    ./my_script.sh "First Arg" "Second Arg" # Run with arguments
    ```
    *   The `./` tells the shell to look for the script in the *current directory*. This is usually necessary unless the directory containing the script is listed in your `$PATH` environment variable.

## 6. Getting Help

*   `man <command>`: Displays the manual page (e.g., `man ls`, `man cp`, `man bash`). Press `q` to quit.
*   `<command> --help`: Many commands offer a concise help summary (e.g., `ls --help`, `grep --help`).
*   `help <builtin_command>`: Get help specifically for Bash built-in commands (like `cd`, `echo`, `pwd`, `type`, `read`).
*   `type <command>`: Shows if a command is a shell builtin, alias, function, or external program file.

## 7. Next Steps & Important Concepts

*   **Quoting:** Understand the crucial difference between:
    *   Double quotes `"..."`: Allows variable expansion (`$VAR`), command substitution (`$(cmd)`), and interprets some special characters.
    *   Single quotes `'...'`: Treats *everything* literally. No expansion occurs.
*   **Control Flow:** `if`/`then`/`elif`/`else`/`fi`, `case`, `for` loops, `while` loops, `until` loops.
*   **Functions:** Define reusable blocks of code within scripts.
*   **More Commands:** Explore `grep` (search text), `sed` (stream editor), `awk` (pattern scanning/processing), `find` (search for files), `tar` (archiving), `ssh` (secure remote login), `curl`/`wget` (downloading), `xargs` (build and execute command lines from stdin).
*   **Permissions:** Understand `rwx` (read, write, execute) for user, group, and others. Use `chmod` and `chown`.
*   **Error Handling:** Check the exit status (`$?`) of commands, use `set -e` (exit on error), `set -u` (treat unset variables as errors), `set -o pipefail` (make pipe fail if any command fails).
*   **Shell Globbing (Wildcards):** Using `*` (matches any sequence of characters), `?` (matches any single character), `[...]` (matches any character within the brackets) to match filenames.

**Practice is essential!** Experiment in your terminal (safely!) and write small scripts to solidify your understanding.