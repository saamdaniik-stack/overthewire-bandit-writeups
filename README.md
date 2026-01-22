# OverTheWire Bandit – Writeups
## Level 0 and Level 0 → Level 1
### Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

#### Solution:
Connecting to the given ssh hostname and password: ssh bandit0@bandit.labs.overthewire.org -p 2220

Then enter the password: bandit0

And we will get the shell access now just cat the readme file and here is over first Flag:

#### Flag: `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

<img width="779" height="216" alt="image" src="https://github.com/user-attachments/assets/b484ce5f-1eec-4b09-b515-e5b428d1d0eb" />

## Level 1 → Level 2
### Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

#### Solution:
After establishing an SSH connection using the SSH key (level 0 flag).

Executing the `ls` command, we found a file named `-`, which is treated as a special character.

Because of this, using the normal `cat` command does not work, so we access it by specifying the path as `./-`.

#### Flag: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

<img width="335" height="152" alt="image" src="https://github.com/user-attachments/assets/6db340e0-7330-4d84-bb04-1ab6d63a32fc" />

## Level 2 → Level 3
### Level Goal
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

#### Solution:
Logged in using the same SSH hostname and password (level 1 flag).

After listing the files using the ls command, we noticed that the filename contains spaces. Typing the filename directly causes errors because the shell treats spaces as argument separators.

To handle this, we use escape sequences, where a backslash (\) is placed before every space in the filename. Additionally, since the filename starts with --, it may be interpreted as an option, so we use -- to stop option parsing.
#### Command: `cat -- --spaces\ in\ this\ filename--`
#### Flag: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

<img width="871" height="162" alt="image" src="https://github.com/user-attachments/assets/ddc3fe55-d19f-4a60-84c8-1fdf499c45d0" />

## Level 3 → Level 4
### Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

### Solution:

Logged in to the server using the SSH credentials obtained from the previous level.

After navigating into the inhere directory, running the normal `ls` command did not show any useful files. This indicated that the required file might be hidden.

To list all files, including hidden ones, the `ls -la` command was used. This revealed a hidden file named `.Hidden-From-You`.

The contents of the hidden file were then displayed using the `cat` command to obtain the flag.

#### Flag: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

<img width="624" height="298" alt="image" src="https://github.com/user-attachments/assets/8bc80d54-8a8a-4216-a8bd-94f334981ae2" />

## Level 4 → Level 5
### Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Commands you may need to solve this level ls , cd , cat , file , du , find

### Solution:
Here also, there is a directory named `inhere`.

Inside this directory, we can see many files containing garbage data. To filter and identify the correct file, we use the following command:
`file ./*`

Here, `*` matches all the files in the directory, and the `file` command returns the type of each file.

From the output, `-file07` is identified as ASCII text, while the remaining files contain binary or irrelevant data. Since the flag is stored in a readable text file, we use the `cat` command to display its contents.
#### Flag: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

<img width="852" height="373" alt="image" src="https://github.com/user-attachments/assets/ce05c9d2-2510-48be-afef-8be224272efa" />

## Level 5 → Level 6
### Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable 1033 bytes in size not executable

### Solution:
Logged in to the server using the SSH credentials for level 5.

After listing the files using the ls command, a directory named inhere was found and accessed using the cd command. Inside the directory, multiple subdirectories named maybehereXX were present.

Since the level specifies that the flag file is readable, exactly `1033` bytes in size, and not executable, the find command was used to filter files based on these properties.
`find . -readable -size 1033c -not -executable`

This command searched the current directory and all subdirectories, returning the file `./maybehere07/.file2` as the only match.

The contents of the identified file were then displayed using the cat command to obtain the flag.

`cat ./maybehere07/.file2`

#### Flag: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

<img width="1183" height="192" alt="image" src="https://github.com/user-attachments/assets/b3c2fdb1-0add-4f48-bf7a-8772c3692059" />

##Level 6 → Level 7
###Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7 owned by group bandit6 33 bytes in size

### Solution:
Here also they have given the properties to find the flag file.

Using find command with the specific filters, we can find a file with no permission denied.

`find / -user bandit7 -group bandit6 -size 33c`

#### Flag: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

<img width="676" height="239" alt="image" src="https://github.com/user-attachments/assets/74b8c89f-559e-4eae-8a8e-ec822f5bd477" />

<img width="832" height="152" alt="image" src="https://github.com/user-attachments/assets/e9506561-bfe9-4cab-b72b-c0175e279e88" />

<img width="545" height="137" alt="image" src="https://github.com/user-attachments/assets/e75ed117-02fa-44f9-9325-0c481763fa01" />

## Level 7 → Level 8
### Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

### Solution:
Here, a wordlist containing usernames and passwords is provided. It is mentioned that the username millionth contains the flag. To extract the required entry, we use a simple grep command to filter the exact line.

#### Command: `cat data.txt | grep 'millionth'`

#### Flag: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

<img width="455" height="233" alt="image" src="https://github.com/user-attachments/assets/81579a85-224e-464e-a2c8-bf189c146675" />

## Level 8 → Level 9
### Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

### Solution:
A file containing multiple strings was provided, where most entries were repeated and only one entry appeared once. To identify the unique string, the file contents were sorted so that identical lines were grouped together. The `uniq -u` command was then used to filter and display only the line that occurs once.

#### Command: `cat data.txt | sort | uniq -u`

#### Flag: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

<img width="450" height="74" alt="image" src="https://github.com/user-attachments/assets/bacffe28-23dd-4162-8115-bf4a686cfb2e" />

## Level 9 → Level 10
### Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

### Solution:
Here we are given data.txt file, if we cat the file which returns garbage, So lets use `strings` command here

#### Command: strings data.txt

#### Flag: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

<img width="404" height="138" alt="image" src="https://github.com/user-attachments/assets/055706f2-83da-4272-917f-0aacede6d0d0" />

<img width="481" height="155" alt="image" src="https://github.com/user-attachments/assets/12423f4d-6425-4bf7-a0a5-48708fa919e4" />

## Level 10 → Level 11
### Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data.

### Solution: 
The given string was Base64-encoded. To retrieve the original password, the encoded string was decoded using the `base64` command with the decode option.

#### command: 'echo 'VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==' | base64 -d'

#### Flag: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

<img width="963" height="143" alt="image" src="https://github.com/user-attachments/assets/0004ff37-58ff-4d65-bc6b-b8432693fab3" />

## Level 11 → Level 12
### Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

### Solution: 
Simple rot13 has been done so rot13 returns the flag

#### Command: `echo 'Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4' | tr 'A-Za-z' 'N-ZA-Mn-za-m'`

#### Flag: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`


<img width="957" height="147" alt="image" src="https://github.com/user-attachments/assets/03d75a73-1946-4625-817c-1b972cc0afc8" />

using `CyberChef`

<img width="1365" height="604" alt="image" src="https://github.com/user-attachments/assets/f1e0a8c7-7d17-4336-adcb-dea32241a2fb" />

## Level 12 → Level 13
### Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

### Solution:
Here we can see a Hexdump stored in a text file:

<img width="634" height="296" alt="image" src="https://github.com/user-attachments/assets/7a1e77d5-d998-4627-b41e-934d78433019" />

By using this command we can reverse the hexdump to executable file

`cat data.txt | xxd -r > hexdump`

Before doing this make sure to copy the file .txt file to the /tmp/

After that using file command for finding the file of the reversed hexdump we can see that its a gzip file

The file is looped with gzip and bz2 zippers use this command multiple times and we should get a tar file. Here are the commands to do so

`mv hexdump hexdump.gz`

`gzip -d hexdump.gz`

`bzip2 -d hexdump`

`tar -xvf hexdump`

#### Flag: `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

<img width="510" height="110" alt="image" src="https://github.com/user-attachments/assets/2e8c5f22-fc7d-4a15-970e-b99fc527e130" />

## Level 13 → Level 14
### Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.

### Solution:

Here we can see a SSH key, to solve this lvl we need to simply connect to the localhost of the ssh server

#### Command: `ssh -i sshkey.private -p 2220 bandit14@localhost`
#### Flag: `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

<img width="939" height="524" alt="image" src="https://github.com/user-attachments/assets/3610c706-80ff-4b0a-9568-8bcf98f98724" />

## Bandit Level 14 → Level 15
### Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

### Solution:
In this challenge, we connect to port 30000 using netcat

#### Command: `nc localhost 30000`

After entering the current Level 14 password, the server responds by displaying the Level 15 flag on the terminal.

#### Flag: `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

<img width="418" height="119" alt="image" src="https://github.com/user-attachments/assets/ee47bc95-a760-48e0-88d6-75777fde973d" />

## Bandit Level 15 → Level 16
### Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

### Solution:

Here we need to connect to the port 30001 with openssl
`openssl s_client -connect localhost:30001`

And enter your LEVEL 15 password the new password will be printed
`8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

#### Flag: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

<img width="995" height="676" alt="image" src="https://github.com/user-attachments/assets/b6415049-b89a-403b-a558-e7a16f2f4547" />

## Bandit Level 16 → Level 17
### Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

### Solution:

In this challenge we can see that there is port range from 31000 to 32000 in which we need to find the one which uses ssl and nc into it.

For that we can use the nmap tool.

### Command: `nmap localhost -p 31000-32000`

Which is used for finding open ports and we got 6 open ports, so lets find the service running on the open ports using this command

#### Command: `nmap localhost -p 31046,31518,31691,31790,31960 -sV -T4`
Then simply connect with openssl

And a RSA key will show up
#### Command: `openssl s_client -connect localhost:31790 -ign_eof`


<img width="662" height="601" alt="image" src="https://github.com/user-attachments/assets/7117e90c-50f7-40b4-a868-1a35d5dbfe9e" />
Save that ssh key in a file like ssh_key.pem

## Bandit Level 17 → Level 18
### Level Goal
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

### Solution:
 In this level, two files are provided: passwords.old and passwords.new.
Both files are almost identical, except for one single line that was modified.
That changed line in passwords.new contains the password for the next level.

To identify the difference between the two files, we use the diff command, which compares files line by line and highlights the changes.

#### Command: `diff passwords.old passwords.new`

#### Flag: `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

## Bandit Level 18 → Level 19
### Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

### Solution:
In this level, logging in normally via SSH is not possible because .bashrc forces an immediate logout. To work around this, we execute a command directly during the SSH connection. By running cat readme as part of the SSH command, the contents of the file are printed before the session is closed. The output reveals the password for the next level.

#### Command: `ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme`
#### Flag: `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

<img width="692" height="325" alt="image" src="https://github.com/user-attachments/assets/2042be3d-2c5a-44f5-a56c-cb7e045bdaa6" />

## Bandit Level 19 → Level 20
### Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

### Solution:
Here we can see a elf file from which we can command execution and we can see that in the permission only the ELF file have access to the bandit20 host

#### Command: `./bandit20-do cat /etc/bandit_pass/bandit20`

#### Flag:`0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

<img width="587" height="48" alt="image" src="https://github.com/user-attachments/assets/aff78934-98ad-48de-a684-db69932a709a" />

## Bandit Level 20 → Level 21
### Level Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

### Solution:
In this challenge we need to use a ncat session for that we can simply use this command

`nc -lvp 2222`

And connect with `./suconnect` in another terminal and the given port number which is 2222 and giving the current flag unlocks the new flag!
#### Flag: `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

<img width="365" height="120" alt="image" src="https://github.com/user-attachments/assets/17560639-c432-41a2-92c9-b9749f042828" />

Another TERMINAL 

<img width="389" height="135" alt="image" src="https://github.com/user-attachments/assets/ab0e7d6a-3519-4b71-baa3-a4ad0156fa0d" />

## Bandit Level 21 → Level 22
### Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

### Solution:
 Here there is a cron job running. Cron jobs are scheduled tasks that run automatically in the background of the operating system and are stored in the /etc/cron.d directory. By checking this directory, we can see the cronjob_bandit22 file, which executes a bash script. Reading that script shows that it copies the bandit22 password from the protected directory into a temporary file. Since the temporary file is readable, accessing it directly reveals the flag.

 #### Flag: `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`

<img width="855" height="334" alt="image" src="https://github.com/user-attachments/assets/fb65ead8-c755-43d3-ac1e-d1634a32543d" />

## Bandit Level 22 → Level 23

### Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

### Solution:
Here there is a cron job running for bandit23. Cron jobs are scheduled tasks that run automatically in the background and are stored in the /etc/cron.d directory. By checking the cronjob_bandit23 file, we can see that it runs a script which creates a filename using the MD5 hash of the string I am user bandit23 and stores the password in the /tmp directory using that hash as the filename. By manually generating the MD5 hash with the given command and then reading the corresponding file from /.

#### flag: `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

<img width="686" height="186" alt="image" src="https://github.com/user-attachments/assets/e5e082e6-1c5e-4c71-9faa-4c05ee79478d" />

## Bandit Level 23 → Level 24
### Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

### Solution:
From this level, we understand that any file placed inside the bandit24 directory is automatically executed by a cron job. If the file is created by bandit23, it gets executed once and then deleted after about 60 seconds. To get the password for bandit24, we need to create a simple bash script that reads the password file and saves it in a location we can access, such as the /tmp directory. Once the script is copied into the bandit24 folder with proper permissions, the cron job executes it and stores the password for us before deleting the script.

#### Commands:

`ls /etc/cron.d/,cat /etc/cron.d/cronjob_bandit24,cat /usr/bin/cronjob_bandit24.sh,nano pass.sh,chmod +x pass.sh,cp pass.sh /var/spool/bandit24/foo/pass.sh,cat /tmp/bandit24_pass`

#### Flag: `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`

## Bandit Level 24 → Level 25
### Level Goal
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time

### Solution:
First we need to enter into the tmp directory and then we need to run this command for i in {0000..9999}; do printf "%s %04d\n" "$(cat /etc/bandit_pass/bandit24)" "$i" done | nc localhost 30002 where , we generate the four digit pin by for loop and using printf as it asked we need to print the password of bandit 24 and the four digit pin note: dont forget add the zero padding and pipe the input to the daemon listening port 30002 with the help of netcat

#### Command `for i in {0000..9999}; do printf "%s %04d\n" "$(cat /etc/bandit_pass/bandit24)" "$i"; done | nc localhost 30002`
#### Flag: `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`

<img width="714" height="252" alt="image" src="https://github.com/user-attachments/assets/103c2d04-1c9e-454c-9f45-dd253a7b1743" />

## Bandit Level 25 → Level 26

###Level Goal
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

###Solution:
































