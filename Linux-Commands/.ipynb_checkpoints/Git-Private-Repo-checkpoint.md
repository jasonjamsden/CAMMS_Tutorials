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

- **clone** -> Bring a repository that is hosted somewhere like Github into a folder on your local machine.
- **pull** -> Download changes from remote repo to your local machine, the opposite of push
- **add** -> Track your files and changes in Git.
- **commit** -> Save your files in Git **locally**.
- **push** -> Upload Git commits to a remote repo (master of branch), like Github.


**Clone and install a repository:**

a. `$ cd ~`

b. `$ git clone git@github.com:PATH_REPO_NAME.git`
      
   - for example: `$ git clone git@github.com:jasonjamsden/CAMMS_Tutorials.git`
   
**Take the latest Update from the Master repository:**

a. `$ git pull`

**Steck Status of the local git repo:**

- This will check **ONLY** local changes in your local computer relative to the master git as you downloaded, which haven't yet commited locally, **NOT** changes and updates in the master branch.

a. `$ cd REPO_NAME` 

- to the particular git repo and check status: 

b. `$ git status`

- or see particular local changes:

c. `$ git diff`

**Git branches:**

- Check in the list of branches and which branch you currently are with a star infront of the branch name:  

`$ git branch`

- Swiche to one other branch:

`$ git checkout BRANCH_NAME`

- Create a swiche to a new branch:

`$ git checkout -b NEW_BRANCH_NAME`

- Delete branch:

`$ git branch -d BRANCH_NAME`

**Save an commit local changes to your local git:**

a. make some local code changes to a previously existing file and save this file.

b.

- adds and commits at the same time for modified files NOT newly created files
`$ git commit -am "COMMENT_OF_COMMIT"`
**`-a` stands for add and `m` stands for message



# Reference
- https://www.youtube.com/watch?v=RGOj5yH7evk
