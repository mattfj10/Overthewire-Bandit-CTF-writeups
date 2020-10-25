# Level 9 -> 10

password to enter this level:

```
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

## Intro 
For this level, we're told the password is stored as one of the few
human-readable strings and is preceded by several '='s. 


## Steps

### Extracting all human-readable strings from a file

First we will extract all the human-readable strings from the text file.
This can be done using the `strings` command, which will print all
human-readable strings in the file to the terminal and use grep to search
for ones that are preceded by several "=" symbols:

```
strings data.txt | grep "====="
```

This command should yield the following output:

```
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

Since we're familiar with the typical format for the passwords on the
overthewire CTF challenges, we can deduce fairly easily that the bottom
choice is the likely password to the next level (which it is).
