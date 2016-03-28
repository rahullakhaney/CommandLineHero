# Manipulation

So far we have used the command line to navigate through the filesystem. In this lesson you will learn how to copy, move and delete files and directories from the command line.


## The cp command

The ``` cp ``` command is used to copy files or directories.

```console
$ cp hello.txt world.txt

# This will copy the contents of hello.txt into world.txt
```

You can also directly copy contents of a file inside a folder into another one

```console
cp desktop/hello.txt gominds/

# This will copy the hello.txt file inside the desktop directory to the gominds directory.
```

So to copy a file into a directory, use the ``` cp ``` with the source file as the first argument and the destination directory as the second argument. Here, we copy the file **desktop/hello.txt** and place it in the **gominds/** directory.

You can also copy multiple files into a directory, use ``` cp ``` with a list of source files as the first argument, and the destination directory as the last argument. Below we copy the files **desktop/hello.txt** and **downloads/world.txt** into the **gominds/** directory.

```console
$ cp desktop/hello.txt downloads/world.txt gominds/

```
### Copy groups of files.

In addition to using filenames as arguments, we can also use special characters like ``` * ``` to select groups of files. These sspecial characters are called **wildcards**. The ``` * ``` selects all files in the working directory.

```console
$ cp * gominds/

# Copy all files into the gominds/ directory
```

In order to select all files in the working directory starting with a specific character use the following command:

```console
$ cp a*.txt gominds/

In the above command all the files in the working directory starting with "a" and ending with .txt will get copied to the gominds/ directory.
```

### Moving files

In addition to copying files, we can move files from the command line using the ``` mv ``` command. We use the source file as the first argument and the destination directory as the second argument.

```console
$ mv hello.txt gominds/

# This moves the hello.txt file to gominds/ directory
```

To move multiple files into a directory we use the ``` mv ``` command with a list of source files as the first argument and the destination directory as the last argument.

```console
$ mv hello.txt world.txt gominds/

# This moves the hello.txt and worl.txt files onto the gominds/ directory
```

You can also rename files using the ``` mv ``` command, to rename we use the ild file as the first argument as the second argument.

```console
$ mv hello.txt world.txt

# This command would rename the hello.txt file to world.txt
```

### Deleting files.

The ``` rm ``` command deletes files and directories.

```console
$ rm hello.txt

# We remove the file hello.txt from the filesystem
```

The ``` rm -r ``` is an option that modifies the behavior of the ``` rm ``` command. The ``` -r ``` stands for "**recursive**" and it's used to delete a directory and all of its child directories.

Be careful when you're using ``` rm ``` it deletes files and directories permanently. There is no way you can undo that command, so once you delete a file or directory using it, there's no way to undo them.

```console
$ rm -r gominds
```
```console
$ rm gominds/*

# This deletes all files in the gominds/ directory
```
