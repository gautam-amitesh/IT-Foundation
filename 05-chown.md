# Change Owner(user & group)
To change the owner of a file/directory `chown` is used. Changing ownership is a security concern so root privilege is required and for granting root access:
1. `sudo` stands for SuperUser do it allows `permitted user` to execute command with Superuser(root) privileges
2. `su - root` stands for Substitute user(switch user) and the new login will be `root`

## For File
1. With least privilege
```
sudo chown new_owner file_name
```

2. With most privilege
```
su - root
```
provide `root` password to login
```
chown new_owner /file_full_path
```
```
exit
```

## For Directory & Sub-Directories
1. With least privilege
```
sudo chown -R new_owner directory_name/
```

2. With most privilege
```
su - root
```
provide `root` password to login
```
chown -R new_owner directory_full_path/
```
```
exit
```

## To change user and group
1. Substitute `new_owner` with `new_owner:new_group`
2. If we don't provide `new_group` by deafult it refers to primary group of `new_owner`

## To change group
1. Substitute `new_owner` with `:new_group`
2. Alternatively use `chgrp` instead of `chown`

# Execution
In a executable file(`file_name.sh`) a set of command/script is written which runs on its own when executed(`./file_name.sh`)

## Creating a Script
1. To display text
```
echo "This a text"
```

2. To read and store an input from executer
```
read variable_name
```

3. To access a variable
```
$variable_name
```

4. To write and store arithematic operation
```
((sum = num1 + num2))
```
