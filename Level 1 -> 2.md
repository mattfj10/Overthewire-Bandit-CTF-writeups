# Level 1 -> 2

Password for this level:
```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

## Intro

In this CTF, after connecting to `bandit1` on the bandit overthewire network,
you'll find a file called `-`. However simply typing `cat -` would not work
in this case since `-` is a special character in the bash terminal which
points to the previous location that the terminal session was at.

## Steps

### Output the file to the terminal

Run the following command to cat the output to the terminal output:
```
cat ./-
```

Lets break this command down. First off the `.` is a reference in the bash
terminal for the current working directory, it's treated just like any other
piece of a folder path so you must add a `/` to access its contents. By doing
this the terminal is made aware due to how it interprets the file path
that `-` is a file and not a reference to the previously visited location.

The output of the file should be the password to the next level:
```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```