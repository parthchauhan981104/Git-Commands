Git Commands
============

## Translated Versions
- [Versão em português](READMEpt.md)

___
touch file-name.extension - linux command to create a file of any type of extension

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository, can also pass an optional name after it that will be given to the copy|

On cloning git will Download the entire project into a specified directory; and Create a remote repository called origin and point it to the URL you pass. you don't need to run "git remote add origin git@github.com:YourUsername/your-app.git" after cloning a repository. The "clone" command will add a remote origin automatically, and you can simply run "git push" from the repository.

### Basic Snapshotting
When you modify a file in your repository, the change is initially unstaged. In order to commit it, you must stage it(staging area)—that is, add it to the index—using git add.

| Command | Description |
| ------- | ----------- |
| `git status` | Check status (shows changes that need to be commited) |
| `git add [file-name.txt]` | Add a file to the staging area |
|  git add . | Add all files in current working directory to the staging area |
| `git add --all  | Add all files and files in folders in current working directory to the staging area | (or git add -A)|
| `git commit -m "[commit message]"` | Commit changes |
| `git commit |Commit changes, commits all files even non tracked ones.a flag should be put to only commit tracked ones. like -m or -a |
   git commit -a -m "hjbsdjks" - add and commit at same time. -a stands for add
| `git rm -f [file-name.txt]` | Remove a file (or folder) from staging area but also deletes the file |
| `git rm --cached [file-name.txt]` | Remove a file (or folder) from staging area only |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

# to get commitid and revertid use git log
git checkout [commit id] - temporarily gets back to the moment of that commit. files temporarily changed to past.
git checkout master - gets back to last commit that was made
git revert [commitid] - reverts back the commit. changes stay, revert is also kind of a commit
git revert [revertid] - reverts the revert as revert is also like a commit
git reset --soft - moves head back, like a checkout. uncommit changes, changes are left staged (index) as seen by git status. used in case of commit mistakes like spelling error
git reset --mixed - it is default. opposite of add. uncommit + unstage changes, changes are left in working tree. git status show the changes as unstaged. need to git add to again make them staged . use example - remove a file that was accidently commited
git reset --hard-  permanent.  uncommit + unstage + delete changes, nothing left. removes from working directory also. uncommited changes lost forever.
git reset --soft HEAD^ - undo the commit. HEAD is just a pointer to a branch(current branch).  "^" represents the last commit. We can read "git reset --soft HEAD^" as "Undo the last commit in the current branch and move HEAD back by one commit."

# add new file(s) to last commit
$ git add file-i-forgot-to-add.html
$ git commit --amend -m "Add the remaining file"
The "--amend" option lets you amend the last commit by adding a new file (or multiple files). Using the "--amend" option, you can also overwrite the message of your last commit.

## ignore a file from being tracked by git
first remove all cached files git rm -r --cached .
then create a .gitignore file - touch .gitignore 
add name of files (with extension) to be ignored
git add .
git commit
to test make changes to file and git status, nothing shows up to be commited

### Branching & Merging https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging
before starting to make branches, must have an initial commit in the repository
| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch - doesnt switch to it|
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch. Merging only takes the last commit of the source branch.|
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
# rebase differs from merge by rewriting the commit history in order to produce a straight, linear succession of commits.

| `git stash` | Stash changes in a dirty working directory | store partial changes in temporary space(stack) and can later commit on it|
| `git stash list` | view a list of stashed changes |
| `git stash apply` | reapply the last stash |
| `git stash apply stash@{2}` | reapply an older stash. 
The changes to your files were reapplied, but the file you staged before wasn’t restaged
| `git stash apply --index` | --index option to tell the command to try to reapply the staged changes.
The apply option only tries to apply the stashed work — you continue to have it on your stack. 
|`git stash drop stash@{0}|` | to remove stash from stack
| `git stash pop` | apply the stash and then immediately drop it from your stack |
| `git stash clear` | Remove all stashed entries |

if your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git won’t let you switch branches. It’s best to have a clean working state when you switch branches. There are ways to get around this (namely, stashing and commit amending)

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |  # The "origin" option is the default name for the server on which your remote repository is located. 
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]`| Push changes to remote repository (and remember the branch) we can run just "git push" next time |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote -v` | list all remote repositories we've connected to. show push and pull url's |
| `git remote add origin https://github.com/YourUsername/some-small-app.git` | - Add a remote repository. a push with https requires credentials everytime|
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository. doesnt require credentials everytime|
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --oneline` - shows in a shorter way |
| `git log --summary` | View changes (detailed) |
| `git show [commit id]` | view commit details |
| `git diff [source branch] [target branch]` | Preview changes before merging |

