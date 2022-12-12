# Give SUDO permissions to Users

(1) we’ll log in as a user that has full sudo privileges, usually `root user`
(2) then we’ll run `sudo visudo`. 
(3) This will open up an editor on the command line. 
(4) Next, we’ll add this line at the end of the file to give to `<user>` sudo rights:
`<user> ALL=(ALL:ALL) ALL`
(5) save the file and restart the systme. This will work 


# References
- https://www.baeldung.com/linux/sudo-privileges-user