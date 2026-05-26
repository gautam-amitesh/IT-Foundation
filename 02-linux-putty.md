# Introduction
1. Unix is the oldest operating system but it is paid
2. Linux is an open source operating system developed by some developers of Unix
3. Kernel is the mediator between OS and hardware which is present in every OS
4. In Unix or Linux we can modify kernel according to our requirements but in Windows it is compiled so we can't change as a result virus or spam attacks are easier in case of widows
5. Windows is a GUI based OS while Linux and Unix are CLI based OS
6. In windows machine we can easily run Linux by connecting to a remote linux server
7. We use PuTTY to securely connect to non-windows remote servers

# PuTTY
1. Host Name(or IP address): non-windows remote server IP
2. Port: 22(SSH) - default for secure and encrypted server
3. Connection type: SSH(Secure Shell) preferred
4. For new session enter session name and save, for saved sessions just load and click open to run CLI
5. In terminal enter username and password to login, a $ sign will appear when logedin

# Commands
1. To check for unix name(OS name):
```
uname
```

2. To check username which is currently loged in:
```
whoami
```

3. To check current (day month date time timezone year):
```
date
```

4. To see the calendar of particular month of a year:
```
cal 05 2026
```

5. To see the calendar of whole year(past current or future):
```
cal 2026
```

6. To see the calendar of previous month, current month and next month:
```
cal -3
```

7. To clear the screen (`ctrl + l`):
```
clear
```

8. To know the name of the server:
```
hostname
```

9. Present working directory(folder in windows):
```
pwd
```

10. To see all the mount points(partition in windows):
```
df -h
```
`df` stands for disk free and `-h` option converts units into human-readbale units. Main(where OS and Apps are by default stored) mount point is `/` we also call it root mount point.

# Assignment
1. Create a github Wiki on how to connect to a remote linux server on windows using putty.
