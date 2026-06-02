# Introduction
1. In any OS when we login as a `user` we land up to home location which is `/home/user` in Linux and `C:\Users\user` in Windows
2. `cd` stands for change directory
3. `ls` stands for list
4. In long listing format each line provides following information: `permission` `number` `owner` `owners group` `size in bytes` `last modified time` `name` 
5. In long listing format `files` and `folders` are identified by two things:
   1. `directory` : permission starting with `d` and number is greater than `1`
   2. `file` : permission starting with `-` and number is `1`
6. Even without using `l` option we can differenciate between files and directories with `p` option
7. Whichever file starts with `.` is hidden
8. `mkdir` stands for make directory and `directory-name` is case sensitive in linux
9. If `number` is `2` then directory consists `0` sub-directory, `+1` for each sub-directory
10. Without creating `parent-directory` we can't run `mkdir parent-directory/child-directory`
11. `-p` stands for path
12. In Linux while creating file, extension is not mandatory whereas in Windows it's mandatory.
13. In linux a file can be opened in three different ways: `read` | `write` | `append`
14. In write mode Linux starts to write from top due to which it override the previous content
15. In linux to keep previous content intact while writing we use `append` mode
16. `cat` stands for concatenate
17. `-R` when used with `cp` or `ls` it stands for recursive.
18. `cp` stands for copy, `mv` stands for move, `rm` stands for remove, and `rmdir` stands for remove directory.

# Commands
1. To go one directory backward:
```
cd ..
```

2. To go to home location:
```
cd
```

3. To go two directory backward:
```
cd ../..
```

4. To go to a particular directory eg. (/home/amitesh):
```
cd /home/amitesh/
```

5. To list directories and files in `PWD`:
```
ls
```

6. To list files and directories in long listing format(permissions, owner, size, and the last modified date/time):
```
ls -l
```

7. To differenciate between files and directories without using `l` option:
```
ls -p
```

8. To sort list according to last modification time:
```
ls -tl
```

9. To reverse the sorting direction of list:
```
ls -rtl
```

10. To reveal hidden files:
```
ls -al
```

11. To list directories and files inside a particular directory:
```
ls -l directory-name
```

12. To create a directory:
```
mkdir directory-name
```

13. To create a `sub-directory` inside `parent-directory` if `parent-directory` exists:
```
mkdir parent-directory/child-directory
```

14. To create a path:
```
mkdir -p parent-directory/child-directory
```

15. To create multiple directories in one go:
```
mkdir one two three
```

16. To create a file:
```
touch file_name
```

17. To redirect the output of a command in a file:
```
command > file_name
```
```
cal -3 > file1
```

18. To open a file in read mode:
```
cat file_name
```

19. To quickly create and open a file in write mode in single command (to exit use `ctrl + d`):
```
cat > file_name
```

20. To open a file in append mode (to exit use `ctrl + d`):
```
cat >> file_name
```

21. To copy a file inside a directory:
```
cp file_name directory_name/
```

22. To copy a file with a different name inside a directory:
```
cp file_name directory_name/different_name
```

23. To copy a directory along with its sub-directories inside another directory(`-r/-R`):
```
cp -R source_directory destination_directory
```

24. To list sub-directories inside a directory:
```
ls -Rl directory_name
```

25. To move a file inside a directory:
```
mv file_name directory_name/
```

26. To move a file with a different name inside a directory:
```
mv file_name directory_name/different_name
```

27. To move a directory inside another direcctory:
```
mv source_directory destination_directory
```

28. To rename a file:
```
mv file_name rename_file_name
```

29. To delete a file:
```
rm file_name
```

30. To delete a directory:
```
rm -R directory_name
```

31. To delete an empty directory:
```
rmdir directory_name
```

32. To copy all files and directories with name starting with a particular character into another directory:
```
cp -R character_name* directory_name
```
```
cp -R f* dir01
```

33. To count number lines / words / characters in a file:
```
wc file_name
```
gives lines, words and characters count together
```
wc -l file_name
```
gives lines
```
wc -w file_name
```
gives words
```
wc -c file_name
```
gives characters

34. To view a file page wise (content is too longer)
```
more file_name
```
press `space bar` to scroll to next page and press `enter` to view next line

35. To view a file number of line wise
1. To view from top
```
head -number_of_lines file_name
```
2. To view from bottom
```
tail -number_of_lines file_name
```

36. To view process status(task manager)
```
ps -ef
```
