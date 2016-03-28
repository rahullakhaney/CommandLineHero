# Redirection

Up until now, we ran commands in the command line and received a stream of output in the terminal. In this lesson, we'll focus on input and output (I/O) redirection.

Through redirection you can direct the input and output of a command to and from other files and programs, and chain commands together in a pipeline. Let's try it out.

```console
$ echo "Hello World"

# Basic example of input output in Terminal
```

The ``` echo ``` command accepts the string "Hello World" as standard input, and echoes the string "Hello" back to the terminal as standard output. Let's discuss more about standard input, standard output and standard error.

1. **Standard Input:** abbreviated as ``` stdin ```, is information inputted into the terminal through the keyboard or input device.

2. **Standard Output:** abbreviated as stdout, is the information outputted after a process is run.

3. **Standard Error:** abbreviated as stderr, is an error message outputted by a failed process.

Redirection reroutes standard input, standard output, and standard error to or from a different location.

## How does redirection work?

### The ">" 

The ``` > ``` command redirects the standard output to a file. Here, "Hello" is entered as the standard input. The standard output "Hello World" is redirected by > to the file hello.txt

```console
$ echo "Hello World" > hello.txt
```

The cat command outputs the contents of a file to the terminal. When you type cat hello.txt, the contents of hello.txt are displayed.

```console
$ cat hello.txt
```

``` > ``` takes the standard output of the command on the left, and redirects it to the file on the right. Here the standard output of cat cats.txt is redirected to dogs.txt.

```console
$ cat cats.txt > dogs.txt
```

Note that ``` > ``` overwrites all original content in dogs.txt. When you view the output data by typing cat on dogs.txt, you will see only the contents of cats.txt.

### The ">>"

``` >> ``` takes the standard output of the command on the left and appends (adds) it to the file on the right. You can view the output data of the file with cat and the filename.

```console
$ cat cats.txt >> dogs.txt

Output:
Rottwiler
Pitbull
Bulldog
German Shephard

Bengal Cat
British Shorthair
Siamese Cat
Persian Cat
```

### The "<"

``` < ``` takes the standard input from the file on the right and inputs it into the program on the left. Here, cities.txt is the standard input for the cat command. The standard output appears in the terminal.

```console
$ cat < cities.txt
```

### The Pipe "|"

``` | ``` is a "pipe". The ``` | ``` takes the standard output of the command on the left, and pipes it as standard input to the command on the right. You can think of this as "command to command" redirection.

```console
$ cat cities.txt | wc
```

Here the output of cat cities.txt is the standard input of wc. in turn, the wc command outputs the number of lines, words, and characters in cities.txt, respectively.

Multiple ``` | ```s can be chained together. Here the standard output of cat cities.txt is "piped" to the wc command. The standard output of wc is then "piped" to cat. Finally, the standard output of cat is redirected to states.txt.

```console
$ cat volcanoes.txt | wc | cat > islands.txt
```

### Sorting through it all

``` sort ``` takes the standard input and orders it alphabetically for the standard output. Here, the lakes in sort lakes.txt are listed in alphabetical order.

```console
$ sort cities.txt
```

```console
$ cat cities.txt | sort > sorted-cities.txt
```

Here, the command takes the standard output from cat cities.txt and "pipes" it to sort. The standard output of sort is redirected to sorted-cities.txt.

## The Uniq Commmand

``` uniq ``` stands for "unique" and filters out adjacent, duplicate lines in a file. Here uniq valleys.txt filters out duplicate entries.

```console
$ uniq valleys.txt
```

A more effective way to call ``` uniq ``` is to call ``` sort ``` to alphabetize a file, and "pipe" the standard output to uniq. Here by piping sort valleys.txt to uniq, all duplicate lines are alphabetized (and thereby made adjacent) and filtered out.

```console
$ sort valleys.txt | uniq
```

```console
$ sort valleys.txt | uniq > uniq-valleys.txt

# Here we are just sending filtered contents to uniq-valleys.txt
```

### Global regular expression print (grep)

grep stands for "global regular expression print". It searches files for lines that match a pattern and returns the results. It is also case sensitive.

``` grep -i ``` enables the command to be case insensitive.

``` grep -R ``` searches all files in a directory and outputs filenames and lines containing matched results. -R stands for "recursive"

```console
$ $ grep -R June desktop/gominds
```

Here grep -R searches the desktop/gominds directory for the string "June" and outputs filenames and lines with matched results.

``` grep -Rl ``` searches all files in a directory and outputs only filenames with matched results. -R stands for "recursive" and l stands for "files with matches"

```console
$ $ grep -Rl June desktop/gominds
```

Here ``` grep -Rl ``` searches the desktop/gominds directory for the string "June" and outputs filenames with matched results.

### Stream Editor (sed)

``` sed ``` stands for "stream editor". It accepts standard input and modifies it based on an expression, before displaying it as output data. It is similar to "find and replace".

```console
$ sed 's/live/dead/' valleys.txt
```

- ``` s ```: stands for "substitution". it is always used when using sed for substitution.

- ``` live ```: the search string, the text to find.

- ``` dead ```: the replacement string, the text to add in place.

In the above case, sed searches valleys.txt for the word "live" and replaces it with "dead". Importantly, the above command will only replace the first instance of "live" on a line.

However, to globally replace a string we can use the ``` g ``` expression.

```console
$ sed 's/live/dead/g' valleys.txt
```