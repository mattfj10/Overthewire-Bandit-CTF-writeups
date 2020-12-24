# Level 12 -> 13

The password for this level is: 

```
5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

## Intro
This level is undoubtedly a test of your partience and ability to withstand
the tediousness that often comes along with these kind of tech/cybersecurity
related tasks. To achieve obtaining the password in this challenge we'll be
using the command `xxd`, `tar`, `gzip`, and `bzip`

## Steps

### Reversing the hex dump

Initially the text file we're given is an ASCII dump of hex values belonging
to a file that has been compressed multiple times. We can first start off by
reversing the hex dump with the `-r` flag which will tell `xxd` to take the
hex dump and reverse it into the original file:

```
xxd -r data.txt > dataoutput
```

### Determining the compression type

Next up is determining what type of compression has been applied to the file.
We can do that with the `file` command:

```
file dataoutput
```

### Extracting the file

The files in this challenge will be in one of 3 formats:

1. gzip compressed files

2. bzip2 compressed files

3. POSIX TAR Archives

with the final password answer being in an ASCII text format. 

To unarchive a gzip file use the following command:

```
gunzip -c (filename here) >> outputfilenamehere
```

To unzip a bzip2 file use the following command:

```
bzip -d (filename here)
```

To unzip a POSIX TAR Archive use the following command:

```
tar -xf (filename here)
```

use `file` to determine which type of compression is used then based
on the output pick command you should use for uncompressing it.
Repeat those steps until file shows the file is an ASCII text file.
This ASCII text file will contain the password for the next level:

```
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```