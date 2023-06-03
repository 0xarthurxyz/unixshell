# CLI (Cheat Sheet)

This is a cheatsheet on various CLI commands (mostly notes-to-self). They are incomplete by default.

Todos:

+   [ ] Add tl;dr from cloud computing class with Stelios

## Zsh shell (configuration)

See `code ~/.zshrc`

Source: [dev.to > Customizing my Zsh Prompt](https://dev.to/cassidoo/customizing-my-zsh-prompt-3417)

## Unix commands

I borrowed a few commands from [0nn0/terminal-mac-cheatsheet/README.markdown](https://github.com/0nn0/terminal-mac-cheatsheet)

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
