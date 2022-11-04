# Make sure git is installed:

a. `$ sudo apt-get install git`
    
    
**SSH Public/Private key** pair generated needed for Git clone:

a. `$ ls -al ~/.ssh/id_rsa.pub`
        (if a returned nothing continue to step b)

b. `$ ssh-keygen` (use default options - just press only Enter)


c. Go to the directory `$ ~/.ssh`
    

d. Open the file `$ atom id_rsa.pub` and copy the key, the entire content of the file.
    

e. Go to your `Github > Setting > SSH and GPG keys > New SSH key` and and a new SSH key by copying the key from the `id_rsa.pub` file.  


**Clone and install the client:**

a. `$ cd ~`

b. `$ git clone git@github.com:REPO_NAME.git`
        (cloning ensues)

