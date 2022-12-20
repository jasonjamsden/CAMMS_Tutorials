# Give SUDO permissions to Users

To see a list of accounts that belong to the sudoers group run:  

`sudo getent group sudo`  

### Way 1

(1) we’ll log in as a user that has full sudo privileges, usually **root user**
(2) then we’ll run `sudo visudo`. 
(3) This will open up an editor on the command line. 
(4) Next, we’ll add this line at the end of the file to give to `<user>` sudo rights:
`<new_user_name> ALL=(ALL:ALL) ALL`
(5) save the file and restart the systme. This will work 


### Way 2

To add a user to the sudoers group, run the following command (as root or an account that already has sudo privileges):   

(1) `usermod -aG sudo [new_user_name]`  


# File Permissions

Permissions for a file or directory may be restricted to by types. There are 3 type of permissions
- r - read
- w - write
- x - execute = running a program  

Each permission (rwx) can be controlled at three levels:
- **u - user** = yourself
- **g - group** = can be people in the same project
- **o - other** = everyone on the system
- **a - all** (user, group, & others) = to everyone

File or Directory permission can be displayed by running command `ls -l`, and we take results as `-rwxrwxrwx` the 1st 3 are for user, the 2nd 3 for the group, the 3rd 3 for others.  

Command to change permission: `chmod`. For example to **remove** write permission from the group to a file called FILE_NAME execute the command: `chmod g-w FILE_NAME` or to **add** write permission to the group to a file called FILE_NAME execute the command: `chmod g+w FILE_NAME`.

* for directories you have `x` so to get into this directory 

# File OWNERSHIP

There are 2 owners of a file or directory: **User** and **Group**. Command to change file ownership:
- `chown`: changes the ownership of a file. 3rd column presents the ownership when `ls -ltr` is executed
- `chgrp`: changes the group ownership of a file. 4rd column presents the group when `ls -ltr` is executed
- `chown`: changes both the ownership and the grpup ownership of a file

**Recursive ownership** change option (Cascade) using `-R` changes the ownership for all the files and folders in this directory.  

For example to the ownership of a file named *FILE_NAME* to a user named *user_name* execute the command:`chown user_name FILE_NAME`, or to change the group ownership `chown group_name FILE_NAME`.  



# References
- https://www.baeldung.com/linux/sudo-privileges-user
- https://phoenixnap.com/kb/sudo-vs-su-differences