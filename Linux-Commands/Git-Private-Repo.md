# Make sure git is installed:

- Install **git** through terminal:
a. `$ sudo apt-get install git`

- Check **git** version:
b. `$ git --version`
      
# Connect your local computer with your GitHub account:

**SSH Public/Private key** pair generated needed for Git clone:

a. `$ ls -al ~/.ssh/id_rsa.pub`
        (if a returned nothing continue to step b)

b. `$ ssh-keygen` (use default options - just press only Enter)


c. Go to the directory: `$ cd ~/.ssh`
    

d. Open the file `$ atom id_rsa.pub` and copy the key, the entire content of the file.
    

e. Go to your `Github > Setting > SSH and GPG keys > New SSH key` and and a new SSH key by copying the key from the `id_rsa.pub` file.  

f. now you are ready to clone and update your repositories. 

# Basic Git Commands:

- clone -> Bring a repository that is hosted somewhere like Github into a folder on your local machine
- add -> Track your files and changes in Git
- commit -> Save your files in Git
- push -> Upload Git commits to a remote repo, like Github
- pull -> Download changes from remote repo to your local machine, the opposite of push

**Clone and install the a repository:**

a. `$ cd ~`

b. `$ git clone git@github.com:REPO_NAME.git`
        (cloning ensues)

