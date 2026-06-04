# Script writing
1. Shorthand for displaying and taking input
```
read -p "Enter the input: " input_variable
```

2. Writing input to a file
```
echo "Input Variable = $input_variable" >> /home/user_name/file_name
```

# Inspecting Server
1. How long server has been running since its last boot
```
uptime
```

2. Display all commands provided by users to server in last 7 days
```
history
```

3. Display current terminal session name
```
tty
```

4. Display a static picture of all the process running in full-format listing
```
ps -ef
```

5. Kill a process forcefully(-9)
```
kill -9 process_id
```

6. Display live processes(health of server)
exit: `ctrl + c`
```
top
```
## Load Average, Tasks
* Average of cpu, memory, and storage over three different time windows:
1. First number - avg. load over last 1 minute
2. Second number - avg. load over last 5 minutes
3. Third number - avg. load over last 15 minutes

* For single core CPU:
1. less than 0.80 = fine
2. reaching 0.80 or greater = alarming stage (system administrator should take action)
3. reaching 0.90 or more = critical stage (immediate action needed or server can crash)

* `zombie` - when parent process doesn't collect the status of child process which finished executing

# Compare two files
```
diff file1 file2
```

# Concatenate two files
```
cat file1 file2 > new_file
```

# To view multiple files together
```
cat file1 file2
```

# To display size of directory/directories
## For particular directory
```
du -h directory_name/
```

## For all directories and sub-directories inside a directory
```
du -h
```

# To sort files according to size
```
ls -lS
```

# To display format type of each mount point
```
df -Th
```

# To change last modification time for a file without changing its content
```
touch file_name
```
