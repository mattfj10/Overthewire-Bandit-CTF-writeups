# Level 0
Password for this level: None

## Intro
This is the first level of the over the wire CTF.
All that's required of you in this CTF is to SSH in on the correct port
with the provided username and password.

```
Port: 2220
Username: bandit0
Password: bandit0
Address: bandit.labs.overthewire.org
```

## Steps
The commmand should like so:

 
### Run the SSH command 
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Now let's break this command down. We first run the main program `ssh`,
with the specified username `bandit0` and the @ to specify the start
of the address `bandit.labs.overthewire.org` and the `-p` argument
to specify to connnect ot he port 2220


You must use the `ssh` command along with the `-p` argument to specify the port.

### Extract the password file
When on the system run `ls` to list the files in your current directory.
There should be a file titled `readme` and within it you will find a password.
Run `cat readme` to view the contents of the readme file, and you should see
the same password listed below:

```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```