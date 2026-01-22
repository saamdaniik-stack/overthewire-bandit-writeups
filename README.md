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




















