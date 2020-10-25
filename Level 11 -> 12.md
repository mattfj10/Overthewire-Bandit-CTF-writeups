# Level 11 -> 12

Password for this level:
```
IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

## Intro

In this level, the file is stored in a password file called `data.txt`.
To decipher it we must shift the each character in the text string by 13. 
For example if we have the character 'a' and we shift that by 13 we will get
'n' since the character 'n' is 13 places down from 'a'. This translation by 13
is a popular cipher known as ROT13 and is often a beginner difficulty challenge
in many CTFs.

In the Linux environment a common tool that's consistently used when dealing
with text transformation is `tr` which can be used for translating text from
one form to another. 

## Steps

### translating 

To translate text fed into `tr` and rotate it by 13 characters you can use the
following command:

```
cat data.txt | tr '[a-z]' '[n-za-m]' | tr '[A-Z]' '[N-MA-Z]'
```

Let's break this command down a bit.
For `tr` the first argument is the set of characters we want to target for
translating/replacement (in this case [a-z] is short hand for all the 
characters of the alphabet) and the second argument represents what to replace
the characters in the first set that appear in the file with.
In this case [n-za-m] which represents the subset of characters in the alphabet
between n-z inclusive concatinated with a-m inclusive
(i.e. nopqrstuvwxyzabcdefghijklm) which essentially represents the English
alphabet rotate by 13 places. So using the first argument as what in the file
to replace in the text file and what to replace it with via the secnod argument
we essentially replace each text character in the file with the character
that is 13 places down from it in the alphabet. 
The reason for the second occurrence of the `tr` command is to handle the
shifting of capital letters as well since the text in the file has a mix of
upper and lower case text characters.

The result of running this command will yield the following output giving us
the password:

```
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```