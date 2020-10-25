# Level 2 -> 3

Password for this level:
```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

## Intro
For this challenge, you must read the password from the file (again) and 
extract the password from it.
However, the catch is that the file has multiple spaces in it.
Therefore you'll need to include some escape characters in 
the command so that it doesn't interpret the spaces between
the file names as arguments rather than part of the name of 
a file.

## Steps

### Use escape characters to read the file

Using the cat command in combination with the `\ ` as an escape sequence
to represent a space in a filename we can use the following command to
read from the file:
```
cat spaces\ in\ this\ filename
```

running said command will give the password to the next level:
```
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```