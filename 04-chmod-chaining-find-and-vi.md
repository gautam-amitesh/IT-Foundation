# Permissions in Linux

## Three different user categories
1. owner -> who created the file/directory `/home/amitesh/`
2. group -> differnt sets of users present at the `/home/`
3. others (world) -> users not listed in `/home/`

## Numeric values instead of permission names or letters
1. read(r) = 4
2. write(w) = 2
3. execute(x) = 1
4. No permission(-) = 0

## Conversion of permission set into number
1. rwx => 4 + 2 + 1 = 7
2. rw => 4 + 2 = 6
3. rx => 4 + 1 = 5

## Changing permission
`chmod` stands for change mode
### For file
`chmod 750 file_name/file_path` => rwx to owner, r-x to group, and --- to others

### For directory
`chmod 755 directory_name/directory_path` => rwx to owner, r-x to group, and r-x to others

### For directory and sub-directories
`chmod -R 755 directory_name/directory_path` =>  rwx to owner, r-x to group, and r-x to others

# Chaining multiple commands
`command1 | command2 | command3` => output of command1 will be the input for command2 and output of command2 will be the input for command3
examples:-
1. `ls -l | cat > fl01` => output of `ls -l` will be list of files and directories in long listing format > `cat > fl01` will take input to write which is provided by `ls -l`.
2. `cal -3 | wc -l` => output of `cal -3` will be calendar of past month, current month, and next month > `wc -l` will take a file input conatining texts which will be `cal -3` itself.

# Finding line or lines containing a character/word
## For character
`grep character file_name`
examples:-
`grep a fl01` => find line inside fl01 containing `a`
`ls -p | grep /` => list only directories from the list of directories and files.

## For word
`grep word file_name`
examples:-
`grep linux fl01` => find line inside fl01 containing `linux`
`ls -l | grep fl01` => finds `fl01` inside list of directories and files

## Ignore case sensitivity(-i)
`grep -i linux fl01` => without carring for case of `linux` it will find the line containing it

## Invert match(-v)
`grep -v linux fl01` => find line/lines inside fl01 not-containing `linux`

# The `vi` editor
## Open a file
`vi file_name`

## Open vi to create a file
1. `vi` hit enter
2. Type something
3. go back to command mode by hitting `esc`
4. `:w/path_to_save_` to create and write a file
5. `:q` to quit

## Modes
1. Command mode => default mode when we open a file but to switch from insert mode `esc`
2. Insert mode => to write and edit text to switch from command mode `i`
3. Command-Line mode => to save, quit, search to switch from command mode `:`

## Commands
### Navigation(move cursor) from command mode
1. `h` => left
2. `l` => right
3. `k` => up
4. `j` => down

### Write(insert) text(from command mode)
1. `i` start writting
2. `dd` delete entire line
3. `u` undo
4. `ctrl + r` redo
5. `yy` copy(yank) line
6. `p` paste below current line
7. `shift + p` paste above current line
8. `o` new line below current line
9. `shift + o` new line above current line
10. `:%s/modify_from/modify_to` substitute all `modify_from` to `modify_to`, if `modify_to` not supplied it will delete `modify_from`
11. `:/search_word` search `search_word`
12. `:set number` set numbered lines
13. `:set nonumber` set non-numbered lines

### (write)save/quit (from command line)
1. `:q` quit(only works with no unsaved changes)
2. `:w` write the file
3. `:wq` write and quit
4. `:q!` force quit without saving

# Find file/directory
## In case we know the path
`find path_to_start -type f/d -name file/directory_name` 
1. `path_to_start` part from where to start the search
2. `f` file / `d` directory
3. `file/directory_name` name of the file/directory searching for

## In case we don't know the path(/ is the parent directory of all paths but not have access to all users)
`find / -type f/d -name file/directory_name 1>file_name_to_divert_successfull(1)_result` 1 for successful results => redirects successful results and shows errors
`find / -type f/d -name file/directory_name 2>file_name_to_divert_error(2)_result` 2 for error results => redirects error results and shows successful results
