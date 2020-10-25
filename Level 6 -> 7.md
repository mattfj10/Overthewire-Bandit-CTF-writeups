# Level 6 -> 7
Password for this level:

```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

## Intro

In this level, the file is stored somewhere on the server
(i.e. anywhere from '/' downward in terms of file structure), and has the
following traits:

1. It belongs to the user bandit 6
2. The group bandit 7
3. The file is 33 bytes in size

We know based on these qualities that the most likely candidate to solve our
challenge is the `find` command.

## Steps

### Finding the file with the -group, -user, and -size arguments

I won't bother breaking this part up into multiple parts and progressively
building it, since this solution is relatively simple, and only requires
adding on two arguments to the find command, which we're already familiar
enough with. The two new arguments are: `-user` and `-group` arguments.
After the user argument you would pass the user name you wish to filter by.
After the group argument, you pass the group name you wish to filter by.
As we learned previously we put the numerical value and the size identifier
when searching with the `-size` argument (in this case the size 
identifier is c).
The final command would look like so:

```
find / -type f -size 33c -group bandit6 -user bandit7"
```

### Filtering out permission denied
However, if you notice, upon running the search, you'll receive several
results that say "Permission denied" and clutter up your search results
since this is quite a nuisance. To deal with this we're going to filter
out all results that show "Permission denied" by redirecting the stderror
output into standard out, then using grep to remove any lines that contain
the phrase "Permission denied"

The command will look like so:

```
find / -type f -size 33c -group bandit6 -user bandit7 2>&1 | grep -v "Permission denied"
```

In the command we redirect stderror (represented by the number 2 which is
its associated file descriptor) into stdout (represented by file descriptor
1). We then pipe the output to the stdin of grep and use `-v` to invert
our grep search, essentially telling it to ignore anything that has the
phrase we've given it as a command line argument.

After running this search result you should get the following output:

```
find: ‘/proc/4718/task/4718/fdinfo/6’: No such file or directory
find: ‘/proc/4718/fdinfo/5’: No such file or directory

/var/lib/dpkg/info/bandit7.password
```

If you felt so inclined, you could add another pipe at the end
of our command to filter out the "No such file or directory" error
but I feel in this case it's not necessary since it's obvious
where the password file is, and it's not cluttering our output.

Within bandit7.password should be the following password to the next level:

```
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```