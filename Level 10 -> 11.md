# Level 10 -> 11

The password for this entry level:
```
truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

## Intro

The goal of this CTF is to obtain the password from a text file which contains
base64 encoded data. Thankfully there is a command in the Linux BASH terminal
command specifically for encoding and decoding base64 strings called `base64`

## Decoding a base64 string

You can use the `-d` argument alongside the `base64` command to decode base64
strings that you pass to it as an argument, so we can pipe the output from the
text in data.txt into the base64 command to decode it:

```
base64 -d data.txt
```

this command will yield us the output that gives us the password:
```
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```