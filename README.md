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

### `nc` (netcat)

Source: Copilot

`nc` is a command-line utility for data transfer over networks using TCP or UDP. It's also known as
netcat.

In the context of a shell script, `nc` could be used for a variety of tasks such as port scanning,
transferring files, or setting up network sockets for testing. However, without additional arguments
or context, it's hard to determine the exact purpose of this `nc` command in your script.

If you're seeing this command in isolation, it's likely a placeholder or an error, as `nc` requires
additional parameters to function correctly. For example, to open a TCP connection to a remote host,
you would use `nc` followed by the hostname and the port number, like so: `nc hostname 1234`.

For example:

```sh
if nc -z localhost $ANVIL_PORT; then
  echo "Port already used"
  kill $(lsof -i tcp:$ANVIL_PORT | tail -n 1 | awk '{print $2}')
  echo "Killed previous Anvil"
fi
```

In the context of this shell script, it checks if a process is running on a specific port
(`$ANVIL_PORT`) on the localhost. If a process is found, it kills that process.

Here's a step-by-step explanation:

1. `nc -z localhost $ANVIL_PORT`: The `nc` command is used with the `-z` option to scan for
   listening daemons, without sending any data to them. It checks if there's a process listening on
   the port specified by `$ANVIL_PORT` on `localhost`.

2. `if nc -z localhost $ANVIL_PORT; then`: If the `nc` command succeeds (i.e., a process is found
   listening on the specified port), the script proceeds with the commands inside the `if` block.

3. `echo "Port already used"`: This line outputs a message indicating that the port is already in
   use.

4. `kill $(lsof -i tcp:$ANVIL_PORT | tail -n 1 | awk '{print $2}')`: This line kills the process
   that's using the port. Here's how it works:

   - `lsof -i tcp:$ANVIL_PORT`: The `lsof` command is used to list all the processes listening on
     the specified port.
   - `tail -n 1`: This command gets the last line of the output from `lsof`, which should be the
     process using the port.
   - `awk '{print $2}'`: This command extracts the second field from the output line, which should
     be the process ID (PID).
   - `kill $(...)`: This command sends a SIGTERM signal to the process with the PID obtained from
     the previous commands, effectively killing the process.

5. `echo "Killed previous Anvil"`: This line outputs a message indicating that the previous process
   (presumably an instance of Anvil) has been killed.

6. `fi`: This ends the `if` block.

In summary, this script checks if a process is running on a specific port and, if so, kills it. This
is typically used to ensure that a port is free before starting a new process that needs to listen
on that port.

### `echo`

`-e` interpret escape sequences

```sh
$ echo -e 'Hello\nworld'
Hello
world

$ echo 'Hello\nworld'
Hello\nworld
```

Source: [linuxhandbook.com](https://linuxhandbook.com/echo-newline-bash/)

### `set -euo pipefail` (file setting)

Source: Github Copilot

For example:

```sh
#!/usr/bin/env bash
set -euo pipefail
```

Source: [`migrations_sol/deploy_precompiles.sh`](https://github.com/celo-org/celo-monorepo/blob/545efbc0f77b9cb7943c34ae0b038d391356668a/packages/protocol/migrations_sol/deploy_precompiles.sh#L1-L3)

The line `set -euo pipefail` is a common setting in bash scripts to make them more robust and fail-safe. It sets three shell options that change the script's behavior in the face of errors:

1.  `-e` or `errexit`: This option causes the shell to exit if any invoked command exits with a non-zero status, which is the convention for indicating errors in Unix-like operating systems. If this option is not set, the script would continue to execute subsequent commands even if a command fails, which could lead to unpredictable results or hard-to-diagnose errors.

2.  `-u` or `nounset`: This option causes the shell to treat unset variables as an error and exit immediately. This can help catch typos or other errors related to variables. Without this option, the shell would treat unset variables as if they were set to an empty string.

3.  `-o pipefail`: This option causes a pipeline (a sequence of commands separated by `|` characters) to fail if any of the commands fail, not just the last one. By default, a pipeline's exit status (which determines whether it's considered to have succeeded or failed) is the exit status of the last command. This option is useful for catching failures in any part of the pipeline.

In summary, `set -euo pipefail` is a way to make the script fail fast -- that is, to halt execution as soon as anything goes wrong, rather than trying to soldier on in the face of errors. This makes errors more visible and helps prevent them from having knock-on effects later in the script.