# Make Keys trusted

- Install a new key:  
`$> gpg --recv-key _THE_KEY_`  

- Check if the key is installed:
`$> gpg --list-keys`  
You will see the key _THE_KEY_  

-Edit key permission:
`$> gpg --edit-key _THE_KEY_`  
`gpg> trust`  
`Your decision> 5`
`Your decision> y`

- Exit gpg:
`Ctrl C`
