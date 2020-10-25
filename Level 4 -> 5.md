# Level 4 -> 5

Password for this level:
```
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

## Intro

In this CTF, you're required to find the password in a series of files, only
one of which is human readable, that file being the one with the password.
The best way to achieve this is with the `file` command which is a useful
tool for figuring out information about the file that is passed to it as
an argument.

## Steps

### Using file to figure out the data stored in each file

A combination of the `file` and the `*` wildcard operator cna be used to figure
out which file it is, that contains the normal ASCII data which represents the 
password. 

Running the following command:
```
file ./file0*
```

Should give the output:
```
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

As can be seen, `-file07` is the one containing the ASCII text password.
The `*` is a wildcard operator that can be used for matching against
multiple files. The `*` means it matches with any number of characters beyond
that point so long as the file starts with `-file0`. We must use the `./` file
operator to stop the terminal from being confused by the special character `-`.
Now if we `cat` `-file07` we will get the password for the next level:

```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```