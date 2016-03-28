# Navigation

To access the command line, we use a terminal emulator, often called the terminal.

In the terminal, the "``` $ ```" also called the shell prompt appears when the terminal is ready to accept a command.

## Where am I?

In the command line, you are always working in a directory, or a folder. We call this your **working directory**. You can see where you are by using the following command:

```console
$ pwd

# Short for print working directory
```

## Explore, Explore and Explore.

When you type ``` ls ```, the command line looks at the folder you are in and then lists the files and folder inside it. Try typing it in your Terminal/iTerm window. In command line we refer folders as directories. Files and directories on your computer are part of a filesystem.

```console
$ ls

# ls is an example of a command
```

```console
$ ls -a

# adding the -a lets you view the hidden files too.
```

The ``` -a ``` modifies the behavior of the ``` ls ``` command to also list the files and directories starting with a period "``` . ```". Files starting with a period are hidden, and don't appear when using just the ``` ls ``` command alone.

The ``` -a ``` is called an **option**. Options modify behavior of commands.

```console
$ ls -l

# Lists all contents of a directory in long format
```

The ``` -l ``` option lists files and directories as a table. With seven columns, each meaning the following:

1. **Access Rights:** These are the actions that are permitted on a file or a directory.

2. **Number of hard links:** Counts the number of child directories and files. This number includes the parent directory link (``` .. ```) and the current directory link (``` . ```)

3. Username of the file's owner

4. The name of the group that owns the file

5. The size of the file in bytes.

6. The date and time that the file was last modified.

7. The name of the file or directory.


```console
$ ls -t

# Orders files and directories by the time they were last modified.
```
Multiple options too can be used together like:

```console
$ ls -alt

# This command will list all contents, including hidden files and directories, in long format, ordered by date and time they were last modified.
```

The first directory in the filesystem is the **root directory**. It is the parent of all other directories and files in the filesystem. Each directory can contain many files and child directoriies. This parent-child relationship continues as long as directories and files are nested.

## Changing Directories

### Go one step ahead.

``` cd ``` stands for "change directory". Just as you would click on a folder in Finder, ``` cd ``` switches you into the directory you specify. It basically lets you change or switch your working directory. When a file directory or a program is passed into a command, it is called an argument.

```console
$ cd desktop

# Here the desktop directory is an argument for the cd command.
```

### Going multiple steps ahead.

You can always go directly to a directory, using the directory's path as an argument.

```console
$ cd desktop/coding/project

# This will take us straight to the project folder.
```

**Pro Tip:** hitting the TAB key autocompletes the directory name. No need to type it all.

### Going one step back.

To move up one directory, we use the ``` cd .. ```. This will navigate us back one directory.

```console
$ cd ..

# This will take us back to the desktop/coding directory from project.
```

### Going all the way back.

To move back to root directory we use the following command.

```console
cd ~

# This will take us to the root directory from the coding directory.
```

### Make a new directory.

The ``` mkdir ``` command stands for "make directory". It takes in a directory name as an argument, and then creates a new directory in the current working directory. Note that this command is only used to create directories and can not be used to create files.

```console
$ mkdir gominds

# Here we create gominds directory using the mkdir command
```

### Create a new file.

The ``` touch ``` command creates a new file inside the working directory. It takes the filename as an argument and then creates an empty file in the current working directory.

```console
$ touch hello_world.rb

# This will create a hello_world.rb file in the present working directory
```
