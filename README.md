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










