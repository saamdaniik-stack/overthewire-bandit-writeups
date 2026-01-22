# OverTheWire Bandit – Writeups
## Level 0 and Level 0 → Level 1
### Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

#### Solution:
Connecting to the given ssh hostname and password: ssh bandit0@bandit.labs.overthewire.org -p 2220

Then enter the password: bandit0

And we will get the shell access now just cat the readme file and here is over first Flag:

####Flag: `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

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



