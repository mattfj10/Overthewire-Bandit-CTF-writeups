# Level 8 -> 9

Password requires to access this level:

```
cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

## Intro

In this level we're required to find the line which contains the password text.
The file is full of repeating strings, with each line having only one string on
it.
The correct password is the only string is this file that occurs only once. 
There is a command we can use called `uniq` for handling reporting or 
omitting unique lines, or counting line occurrences. 

## Steps

### Sorting the lines and obtaining only unique ones

The `uniq` command be passed an argument `-u` which will tell uniq to only
print out the unique lines in the text file.
However, the issue with uniq, is that it will only remove duplicate lines
if they occur consecutively after one another. Meaning if two lines are
in a separate place in the file, they won't get removed and will be
included in the output.
To fix this we will use `sort` so that way all duplicate lines
occur consecutively when we pipe it in as input into uniq.

The command should look like so:

```
cat data.txt | sort | uniq -u
```

As can be seen, the output from cat is put into sort, which has the sorted
output piped into `uniq` with the `-u` argument to ensure only lines
that appear once are shown. running this will give the following output:

```
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
