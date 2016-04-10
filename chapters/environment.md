# Environment

Every time we launch the terminal, it creates a new session. This session immediately loads settings and preferences that make up the command line environment.

This environment can be configured to support the commands and programs we create. Which enables us to customize greetings and command aliases, and create variables to share across commands and programs.

Let's begin with a simple command line text editor called **nano**

In your terminal type: 

```console
$ nano hello.txt
```
This opens the nano text editor, then in the editor at the top of the window type:

```console
"Hello World, Hello Nano"
```

Using the menu at the bottom of the terminal for reference, type Ctrl + O (the letter, not the number) to save the file. This is the letter "O", not the number zero.

Press Enter, when prompted about the filename to write.

Then type Ctrl + X to exit nano.

Finally, type clear to clear the terminal window. The command prompt should now be at the top of the window.

## Nano

nano is a command line text editor. It works just like a desktop text editor like TextEdit or Notepad, except that it is accessible from the command line and only accepts keyboard input.

- The command nano hello.txt opens a new text file named hello.txt in the nano text editor.

- "Hello world, Hello nano" is a text string entered in nano through the cursor.

- The menu of keyboard commands at the bottom of the window allow us to save changes to hello.txt and exit nano. The ^ stands for the Ctrl key.

- Ctrl + O saves a file. 'O' stands for output.

- Ctrl + X exits the nano program. 'X' stands for exit.

- Ctrl + G opens up help menu.

- ``` clear ``` clears the terminal window, moving the command prompt to the top of the screen.

## Store environment settings

In the terminal, type

```console
$ nano ~/.bash_profile

# This opens up a new file in nano.
```

In **~/.bash_profile**, at the top of the file, type:

```console
$ echo "Hello World, Isn't this cool?"
```

- Type Ctrl + O to save the file.

- Press Enter to write the filename.

- Type Ctrl + X to exit.

- Finally, type ``` clear ``` to clear the terminal window.

In the terminal, type

```console
$ source ~/.bash_profile
```

You should see the greeting you entered.

### How does it work?

**~/.bash_profile** is the name of file used to store environment settings. It is commonly called the "bash profile". When a session starts, it will load the contents of the bash profile before executing commands.

- The ~ represents the user's home directory.
- The . indicates a hidden file.
- The name ~/.bash_profile is important, since this is how the command line recognizes the bash profile.

1. The command nano ~/.bash_profile opens up ~/.bash_profile in nano.

2. The text echo "Hello Worl, Isn't this cool?" creates a greeting in the bash profile, which is saved. It tells the command line to echo the string "Welcome, Jane Doe" when a terminal session begins.

3. The command source ~/.bash_profile activates the changes in ~/.bash_profile for the current session. Instead of closing the terminal and needing to start a new session, source makes the changes available right away in the session we are in.

### The Alias

The alias command allows you to create keyboard shortcuts, or aliases, for commonly used commands.

Go to your **~/.bash_profile** and type:

```console
$ alias pd="pwd"
```
save the file, and clear the termina window. Now try typing:

```console
$ source ~/.bash_profile

# Followed by

$ pd
```

1. Here alias pd="pwd" creates the alias pd for the pwd command, which is then saved in the bash profile. Each time you enter pd, the output will be the same as the pwd command.

2. The command source ~/.bash_profile makes the alias pd available in the current session. Now, every time we open up the terminal, we can use the pd alias.

Try it with commands like:

```console
$ alias hy="history"

$ alias ll="ls -la"
```

```hy``` is set as alias for the history command in the bash profile. The alias is then made available in the current session through source. By typing hy, the command line outputs a history of commands that were entered in the current session.

```ll``` is set as an alias for ls -la and made available in the current session through source. By typing ll, the command line now outputs all contents and directories in long format, including all hidden files.

## Setting Environment Variables

Environment variables are variables that can be used across commands and programs and hold information about the environment.

Open **~/.bash_profile** in nano, and in the bash profile, beneath the aliases, on a new line, type:

```console
export USER="Your Name"
```

Don't forget to save the file. In the command line, use ``` source ``` to activate the changes in the bash profile for the current session.

Typing ``` $ echo USER ``` should return your name.

- The line ``` USER="Your Name" ``` sets the environment variable USER to a name "Your Name". Usually the USER variable is set to the name of the computer's owner.

- The line ``` export ``` makes the variable to be available to all child sessions initiated from the session you are in. This is a way to make the variable persist across programs.

- At the command line, the command ``` $echo $USER ``` returns the value of the variable. Note that $ is always used when returning a variable's value. Here, the command echo $USER returns the name set for the variable.

## PS1

PS1 is a variable that defines the makeup and style of the command prompt.
``` export PS1=">>> " ``` sets the command prompt variable and exports the variable. Here we change the default command prompt from $ to >>>. After using the source command, the command line displays the new command prompt.

Open **~/.bash_profile** in nano.

```console
$ export PS1=">>> "

# Save the file and clear your terminal window
```

In the command line, use source to activate the changes in the bash profile for the current shell session. Let's try out the new command prompt. In the terminal type:

```console
echo "hello world"
```

Did you notice the change in the prompt?

```console
Instead of the $ it shows >>> now

>>> echo "hello world"
```

## Home

The **HOME** variable is an environment variable that displays the path of the home directory. Here by typing ``` echo $HOME ```, the terminal displays the path **/home/ccuser** as output.

## Path

**PATH** is an environment variable that stores a list of directories separated by a colon. Looking carefully, ``` echo $PATH ``` lists the following directories:

1. /home/ccuser/.gem/ruby/2.0.0/bin
2. /usr/local/sbin
3. /usr/local/bin
4. /usr/bin
5. /usr/sbin
6. /sbin
7. /bin

Each directory contains scripts for the command line to execute. The PATH variable simply lists which directories contain scripts.

For example, many commands we've learned are scripts stored in the /bin directory.

```console
$ /bin/pwd
```

This is the script that is executed when you type the pwd command.

```console
$ /bin/ls
```

This is the script that is executed when you type the ls command. In advanced cases, you can customize the PATH variable when adding scripts of your own.

## ENV

In the command line type:

```console
$ env

# followed by

$ env | grep PATH
```

The ``` env ``` command stands for "environment", and returns a list of the environment variables for the current user. Here, the env command returns a number of variables, including **PATH**, **PWD**, **PS1**, and **HOME**.

``` env | grep PATH ``` is a command that displays the value of a single environment variable. Here the standard output of ``` env ``` is "piped" to the ``` grep ``` command. ``` grep ``` searches for the value of the variable **PATH** and outputs it to the terminal