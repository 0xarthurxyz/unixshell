# ✨ Unix (Cheat Sheet)

This is a cheat sheet for Unix commands (mostly notes-to-self). They are incomplete by default.

> [!NOTE]  
> This repo currently contains git commands as well, which I'll remove at some point.

## Unix commands

### Zsh shell (configuration)

See `code ~/.zshrc`

Source: [dev.to > Customizing my Zsh Prompt](https://dev.to/cassidoo/customizing-my-zsh-prompt-3417)

I borrowed a few commands from
[0nn0/terminal-mac-cheatsheet/README.markdown](https://github.com/0nn0/terminal-mac-cheatsheet)

### List and kill processes

From [wikipedia](<https://en.wikipedia.org/wiki/Top_(software)>):

> `top` (table of processes) is a task manager or system monitor program, found in many Unix-like
> operating systems, that displays information about CPU and memory utilization.

```sh
$ top
```

Find the PID (process identification number) you want to kill and use `kill-9 <PID>`.

For example::

```sh
kill -9 27201
```

Source: [setapp.com](https://setapp.com/how-to/how-to-view-and-kill-processes-on-mac)

### Create directory: `mkdir`

```bash
# Example:
mkdir a_test_folder
```

### Navigate to directory: `cd`

```bash
# Example anywhere:
cd /Users/USERNAME/FOLDER/FOLDER/
# Example within folder:
cd [folder]
```

### Full path to working directory: `pwd`

```bash
# Example:
pwd .
```

### Short listing: `ls`

```bash
# Example:
ls .
```

### Home directory: `~`

```bash
# Example:
cd ~
```

### Previous directory: `-`

```bash
# Example:
cd -
```

### Current folder: `.`

```bash
# Example:
ls .
```

### Parent directory: `..`

```bash
# Example:
ls ..
```

### Move up 2 levels

```bash
cd ../../
```

### Create new file: `touch`

```bash
# Example:
touch an_algorithm.py
```

### Remove file: `rm`

```bash
rm an_algorithm.py
```

### Rename folder: `mv`

```bash
mv old_name new_name
```

Only if `new_name` **is not** already a folder.

### Move folder: `mv`

```bash
mv old_location new_location
# mv home/user/desktop/folderA home/user/documents/github/folderX
```

Only if `new_location` **is** already a folder.

### Delete a directory and its contents

`rm -r [dir]`

### Show head of a file:

`head [file].[extension]`

### `#!/bin/bash`

Source: ChatGPT

The line `#!/bin/bash` at the beginning of a unix shell script is known as a shebang (or hashbang,
pound-bang, or sharp-bang). In Unix-like operating systems, the shebang specifies which
**interpreter** should be used to execute the script. This ensures consistent behavior regardless of
the user's default shell (e.g. zsh, bash, ...).

1. **`#`**: In many scripting languages, the hash symbol is used to start a comment. However, when
   combined with `!` as the first two characters of a script file, it gains a special meaning.

2. **`!`**: When the exclamation mark is combined with the hash symbol as `#!`, it tells the
   operating system that the file is a **script** and should be **interpreted**.

3. **`/bin/bash`**: This specifies the **interpreter's path** that should be used to execute the
   script. In this case, it's the Bash shell located at `/bin/bash`. This path can vary depending on
   the system and the script interpreter. For example, Python scripts often start with
   `#!/usr/bin/env python`.

When you execute a script from the command line in a Unix-like system, the system checks the first
line of the script. If it starts with `#!`, it uses the specified interpreter to run the script. If
this line is not included, the system will use the current shell to execute the script, which might
not be the intended interpreter and can lead to errors or unexpected behavior.

For example, consider the following script:

```sh
#!/bin/bash
echo "Hello, world!"
```

When you make this script executable and run it, the system reads the first line, sees
`#!/bin/bash`, and invokes `/bin/bash` to run the script. This ensures that the script is executed
in the Bash shell, even if the user is currently using a different shell like `zsh` or `ksh`.
