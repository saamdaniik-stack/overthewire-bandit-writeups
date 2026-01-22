# OverTheWire Bandit – Writeups
## Level 0 and Level 0 → Level 1
### Level Goal
The objective of this level is to access the NATAS game through a web browser and locate the password for the next level. The login credentials for this level are provided, and the password for natas1 is hidden within the webpage itself.

#### Solution:
First, open the following URL in a web browser:
`http://natas0.natas.labs.overthewire.org`

Log in using the given credentials:

Username: natas0
Password: natas0

After successfully logging in, view the page source of the website. Upon inspecting the HTML code, a comment is found that contains the password for the next level.

The comment reveals the password for natas1, which can then be used to proceed to the next level.

##### Flag `0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq`

<img width="1086" height="354" alt="image" src="https://github.com/user-attachments/assets/2e06cf14-e2ea-489d-b73f-316f26e8cae8" />


## Level 1 → Level 2
### Level Goal
The password for the next level can be found in a file named readme inside the home directory. Use this password to log in to bandit1 through SSH. Each time a password is discovered, connect to the next level using SSH on port 2220 to continue.

#### Solution:


