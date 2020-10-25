# Level 5 -> 6

Password for this level:

```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

## Intro

In this CTF, there is a are a set of numbered files starting with `maybehere` 
and within each of those folders, a set of files. One of those files in one of
those folders contains the password we are looking for, and it has the 
following traits:

1. It is 1033 bytes in size
2. It's not executable
3. It's in human-readable format

## Steps

### Searching for human-readable files

Now, from previous write-ups we know that the `file` command can be used to 
determine if a file is in human-readable format, and we know that `*` can be
used to match all files that have the same text up to the point of the star.
But this will output ALL files, and show us whether or not they're 
human-readable, and we want the output of this command to filter
out results that aren't human readable so we don't have to pick
them out ourselves. To fix this we can use the pipe operator `|`
to pipe the output of file as standard input into the `grep` command
and pass the argument `ASCII` to grep so it will search the input
we give it, for the words `ASCII` which appear in the results
when a file is human-readable. So let's start building the command we'll need 
to give the shell:


```
file inhere/maybehere* | grep ASCII
```

### Finding files of a certain size
This would work if there was only one human-readable file but there is not,
there's multiple across all the folders and unless we want to spend tedious
time checking each one, then it would be best to narrow down our search
by being more specific about what we're looking for. We can use the `find`
command to narrow down that we're searching specifically for a file and
the file size must be around 1033 bytes:

```
find inhere/maybehere* -type f -size 1033c
```

### Finding non-executable files
The find command can also be used to find files of certain traits, such as,
files that are executable/non-executable. Find has an argument `-executable`
to specify that we want the file we're searching for to be executable.
However, there is no explicit command to search for a non-executable file
but we can add a negation operator `!` before any argument which basically
find you want to search for anything that does NOT satify the argument
immediately ahead of the negation operator. Putting it all together our
completed find statement should look like this:

```
find inhere/maybehere* -type f -size 1033c ! -executable
```


### Command substitution
Now we have to combine the find argument and the file argument. 
We need to find out how we can pass the output from the call to 
`find` into the `file` command as arguments. 
 We can do this using something called command substitution,
 which uses the following syntax:

```
$(command whose output you wish to use as an argument here)
```

### Putting the command together
Tying it all together we get the following command that will 
find files that are 1033 bytes in size and not executable
and pass the files we got from the output of the `find` command
into the `file` command to see whether each file analyzed is 
human readable ASCII or in a data format of some form:

```
file $(find inhere/maybehere* -type f -size 1033c ! -executable) | grep ASCII
```

running this command will give you the following file as a result:

```
maybehere07/.file2
```

Aha! Our culprit has been found and it contains the following password which
will gain you entry to the next level:

```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
Now this was a longer entry than my previous writeups, which makes sense,
as the challenges get harder so will my entries.
But I really wanted to break down the command we would be using to find
the password file, as A LOT of important concepts relevant to bash shell
are covered in it, and will become incredibly helpful down the line
when it comes to using the bash shell environment.
