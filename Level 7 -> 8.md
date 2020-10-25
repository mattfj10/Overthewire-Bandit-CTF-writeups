# Level 7 -> 8

Password for this level:
```
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

## Intro
In this challenge a long text file is given to us and we have to find the
password inside it. 
We know the password is next to the word "millionth" and we're performing
a text search, so all that would be necessary is utilizing `grep` to perform
a text search for the word "millionth"
 

## Steps

### Searching a file for text in grep

Anyone whose followed my CTFs so far and has a basic grasp of using the Linux
commandline can probably assume how this command should be structured.
Below is the command to perform a text search on the file for the phrase
"millionth":

```
grep "millionth" data.txt
```

This will yield an output which will give you the password to go onto the next
level:

```
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```