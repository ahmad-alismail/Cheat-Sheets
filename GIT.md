[[Model Deployment Notes]]
# Git Cheat Sheet
## Important Notes:
- Create Repository for Every Project
- Create a New Branch For Every Feature or Enhancement

![[Pasted image 20220613092716.png]]

![[Pasted image 20220614154447.png]]
## Create new project on local based on remote repo
1. Go to directory you want (or right click git bash here):

```markdown
cd/users/ahmadalismail/Documents # macOs
```
2. Create new directory
```markdown
mkdir My-Github
cd My-Github/
```
3. Clone repo from your github 
```markdown
git clone https://github.com/afi1289/Git_Course.git

# check it 
dir

cd Git_Course\
```
==**Important**== You have to put your files inside the created folder to `add`,`commit`, and `push` etc...


**OR** [Check out this link](https://www.youtube.com/watch?v=usjh4jj7_nQ&list=PLDoPjvoNmBAw4eOj58MZPakHjaO3frVMF&index=9&ab_channel=ElzeroWebSchool)

### Create Public Key
- To avoid filling username/password with each action taken
- It's not specific for git or github

1. ``ssh- keygen -t rsa -b 4096 -C "afi.89@outlook.com"`` 
2. Enter 
3. Enter your password
4. ``cat ~/.ssh/id_rsa.pub`` will show your key
5. Copy it (starting from ssh)
6. Past it in github (go to Settings -> SSH and GPG Keys -> New secure shell key)
7. Let's test it using ``ssh -T git@github.com``

1. Initialize repo on your device (You have to add public key)
```markdown
git init
```
2. Try to create any file
```markdown
touch index.html
```
3. Status
```markdown
git status
```
4. Add
```markdown
git add index.html
```
5. Create the main file
```markdown
git commit -m "hello this is my first repo"

git remote add origin git@github.com:afi1289/Twitter-Scraper.git
```
6. Push the files
```markdown
git push -u origin master
```




## Git Basics
Command | Description
------------ | ------------
```git init <directory>```| Create empty Git repo in specified directory. Run with no arguments to initialize the current directory as a git repository
**``git clone https://github.com/afi1289/Git_Course.git``** | Clone repo located at ``<repo>`` onto local machine. Original repo can be located on the local filesystem or on a remote machine via HTTP or SSH.
``git config user.name <name>`` | Define author name to be used for all commits in current repo. Devs commonly use ``--global`` flag to set config options for current user.
**``git add <directory>``** | Stage all changes in for the next commit. Replace ``directory`` with a to change a specific file.
**``git add *``** | Stage all files in the directory for the next commit. 
**``git reset head <directory>``** | Unstage all changes in for the next commit. 
**``git commit -m "<message>"``** | Commit the staged snapshot, but instead of launching a text editor, use ``<message>`` as the commit message.
**``git status``** | List which files are staged, unstaged, and untracked.
``git log`` | Display the entire commit history using the default format. For customization see additional options.
``git diff`` | Show unstaged changes between your index and working directory.

## Undoing Changes
Command | Description
------------ | ------------
**``git remote -v``** | show the ``<remote>`` name
``git revert <commit>`` | Create new commit that undoes all of the changes made in ``<commit>``, then apply it to the current branch.
**``git restore -- staged <file_name>``** or ``*`` for all files | Remove ``<file>`` from the staging area, but leave the working directory unchanged. This unstages a file without overwriting any changes.
``git clean -n`` | Shows which files would be removed from working directory. Use the ``-f`` flag in place of the ``-n`` flag to execute the clean.


## Rewriting Git History
Command | Description
------------ | ------------
``git commit --amend`` | Replace the last commit with the staged changes and last commit combined. Use with nothing staged to edit the last commit’s message.
``git rebase <base>`` | Rebase the current branch onto ``<base>``. ``<base>`` can be a commit ID, branch name, a tag, or a relative reference to ``HEAD``.
``git reflog`` | Show a log of changes to the local repository's ``Head``.


## Git Branches
Command | Description
------------ | ------------
**``git branch <branch_name>``** | List all of the branches in your repo. Add a ``<branch>`` argument to create a new branch with the same ``<branch>`` 
``git checkout master`` | Merge to my master branch
``git merge "development"`` | _Merge to my master branch_
**``git push origin master``** | send to github/pull request
``git checkout -b <branch>`` | Create and check out a new branch named ``<branch>``. Drop the ``-b`` flag to checkout an existing branch.
``git branch -m <new_branch_name>`` | Change the branch name
``git branch -d <branch_name>`` | Delete the branch if the changes are already `merged` (SAFE)
``git branch -D <branch_name>`` | Delete the branch even if the changes are NOT already `merged` (NOT SAFE)
``git merge <branch>`` | Merge `<branch>` into the current branch



## Remote Repositories
Command | Description
------------ | ------------
**``git push <remote> <branch>``** | Push the branch to `<remote>`, along with necessary commits and objects. Creates named branch in the remote repo if it doesn’t exist. **NOTE**: Check the name of `branch` and `remote` if necessary
``git remote add <name> <url>`` | Create a new connection to a remote repo. After adding a remote, you can use `<name>` as a shortcut for `<url>` in other commands.
``git fetch <remote> <branch>`` | Fetches a specific `<branch>`, from the repo. Leave off `<branch>` to fetch all remote refs.
``git pull <remote>`` (fetch + merge) | Fetch the specified remote's copy of current branch and immediately merge it into the local copy.

## Git Config
Command | Description
------------ | ------------
``git config --global user.name <name>`` | Define the author name to be used for all commits by the current user.
**``git config --global user.email <email>``** | Define the author email to be used for all commits by the current user.
``git config --global alias. <alias-name> <git-command>`` | Create shortcut for a Git command. E.g. ``alias.glog``  ``log --graph --oneline`` will set ``git glog`` equivalent to ``git log --graph --oneline``.
``git config --system core.editor <editor>`` | Set text edito used by commands for all users on the machine. `editor` arg should be the command that launches the desired editor (e.g., vi)
``git config --global --edit`` | Open the global configuration file in a text edito for manual editing
``Content in the first column`` | Content in the second column

## Git Log
Command | Description
------------ | ------------
``git log - <limit>`` | Limit number of commits by `limit`. E.g. `git log -5` will limit to 5 commits
``git log --online`` | Condense each commit to a single line
``git log -p`` | Display the full diff of each commit
``git log --stat`` | Include which files were altered and the relative number of lines that were added or deleted from each of them.
``git log--author="<pattern>"`` | Search for commits by a particular author.
``git log --grep="<pattern>"`` | Search for commits with a commit message that matches `<pattern>`
``git log <since>..<until>`` | Show commits that occur between `<since>` and `<until>`. Args can be a commit ID, branch name, `HEAD`, or any other kind of revision reference
``git log -- <file>`` | Only display commits that have the specified file
``git log --graph --decorate`` | ``graph`` flag draws a text based graph of commits on left side of commit msgs. `--decorate` adds names of branches or tags of commits shown.
``Content in the first column`` | Content in the second column

## Git Diff
Command | Description
------------ | ------------
``git diff HEAD`` | Show difference between working directory and last commit.
``git diff --cached`` | Show difference between staged changes and last commit

## Git Reset (to delete unneeded commits )
Command | Description
------------ | ------------
``git reset`` | Reset staging area to match most recent commit, but leave the working directory unchanged
``git reset --hard`` | Reset staging area and working directory to match most recent commit and **overwrites all changes** in the working directory.
``git reset <commit>`` | Move the current branch tip backward to `<commit>`, reset the staging area to match, but leave the working directory alone.
``git reset --hard <commit>`` | Same as previous, but resets both the staging area & working directory to match. **Deletes** uncommitted changes, and **all commits after** ``<commit>``. **NOTE**: Then you have to update remote using `get push origin main --force`
``git reset --hard origin/master`` | If your local changes are bad then just remove them or reset your local master to the state on remote

## Git Rebase
Command | Description
------------ | ------------
``git rebase -i <base>`` | Interactively rebase current branch onto `<base>`. Launches editor to enter commands for how each commit will be transferred to the new base.

## Git Pull
Command | Description
------------ | ------------
**``git pull origin``** | Fetch the remote's copy of current branch and merged it into the local copy.
``git pull -rebase <base>`` | Fetch the remote's copy of current branch and rebases it into the local copy. Uses git rebase instead of merge to integrate the branches.

## Git Push 
Command | Description
------------ | ------------
``git push <remote> --force`` | Forces the `git push` even if it results in anon-fast-forward merge. Do not use the `--force` flag unless you're absolutely sure know what you're doing  
``git push <remote> --all`` | Push all of your local branches to the specified remote
``git push <remote> --tags`` | Tags aren't automatically pushed when you push a branch or use the `--all` flag. The `--tags` flag sends all of your local tags to the remote repo


## Add Large files to github
1. Download and install Git on your pc. [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Then download and install GitLFS on your pc. [https://git-lfs.github.com/](https://git-lfs.github.com/)
3. Now clone your GitHub repository to your local machine. First go to your repository and copy the ‘clone/download’ URL. Next, create a new folder in your pc wherever you prefer: this is to clone the copy of your GitHub repository to your pc. Then right-click the background and click ‘Git Bash Here’ as follows. [More Information](https://medium.com/linkit-intecs/how-to-upload-large-files-to-github-repository-2b1e03723d2)
````markdown 
git clone https://github.com/afi1289/my_repo.git
````
Then close bash command
1. Go to inside the cloned repository and click **git bash here**. Then run the following:
````markdown
git lfs install
# you only need to run this once per user account
````
5. **Now**  copy the large files in github repository in your **local** machine.
6. Go to inside the cloned repository and click **git bash here**. Run the following command ``git lfs track "*.fileextension"`` or ``"big_file"``. 
7. Now make sure .gitattributes is tracked: 
````markdown
git add .gitattributes
````
8. Just commit and push to github as you normally would:
````markdown
git add big_file.psd
git commit -m "Add design file"
git push origin master
````

## Collaborate with other users
1. **Kankajan814** creates a repo and goes to settings -> Collaborators -> Add **afi1289**
2. **Afi1289** check the inbox -> Accept invitation
3. On the local machine of **afi1289**: ``git clone https://github.com/kankajan814/our-project2.git``
4. Now **afi1289** can add, commit, and push (master branch) files into repo as usual. The uploaded files will be available on **kankajan814** main remote server.
5. Any **Changes** on the **kankajan814** main remote repo could be fetched and merged into the **afi1289** local repo using the command `git pull origin`

## Create Public key (Secure shell key SSH)
 - To avoid using username/password each time you make an action
 1. Go the the command line (choose the project folder while editing)
 2. ``ssh-keygen -t rsa -b 4096 -C "afi.89@outlook.com"``
 3. Enter
 4. Enter the password (optional)
 5. The system shows you the path where the key is saved (e.g., `C:\Users\ahmad.alismail\.ssh`)
 6. Go to the above mentioned path using `cd`
 7. `cat ~/.ssh/id_rsa.pub` Shows the content of the key.(In windows you have to use powershell)
 8. Copy the content of the public key into the clipboard
 9. Go to another github profile -> Settings -> SSH and GPG keys -> New SSH key -> Past from clipboard -> Choose Title as you like -> Add SSH key
 10. ``ssh -T git@github.com`` in cmd

## Create Repository from Existing Project
The following steps are used for learning purposes 1-6
1. go to a path you want -> `mkdir repos` -> `cd repos` 
2. Initialize git repository in the path `git init`
3. Create new file `touch index.html`
4. `git status`
5. `git add index.html`
6. ``git commit -m "created the main file"``
NOW (we assume that we have a project on local machine)
1. Create new Repo on Github.com (Without readme file)
2. Click on the SSH above
3. Copy ``git remote add origin git@github.com:afi1289/test_project.git`` and implement it in cmd
4. `git push -u origin master`

# Stoped at video 9 from the [library](https://www.youtube.com/watch?v=usjh4jj7_nQ&list=PLDoPjvoNmBAw4eOj58MZPakHjaO3frVMF&index=10&ab_channel=ElzeroWebSchool)
