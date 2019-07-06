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
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting
When you modify a file in your repository, the change is initially unstaged. In order to commit it, you must stage it(staging area)—that is, add it to the index—using git add.

| Command | Description |
| ------- | ----------- |
| `git status` | Check status (shows changes that need to be commited) |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git commit |Commit changes, commits all files even non tracked ones.a flag should be put to only commit tracked ones. like -m or -a |
| `git rm -f [file-name.txt]` | Remove a file (or folder) from staging area but also deletes the file |
| `git rm --cached [file-name.txt]` | Remove a file (or folder) from staging area only |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

# to get commitid and revertid use git log
git checkout [commit id] - temporarily gets back to the moment of that commit. files temporarily changed to past.
git checkout master - gets back to last commit that was made
git revert [commitid] - reverts back the commit. changes stay, revert is also kind of a commit
git revert [revertid] - reverts the revert as revert is also like a commit
git reset --soft - moves head back, like a checkout. uncommit changes, changes are left staged (index) as seen by git status. used in case of commit mistakes like spelling error
git reset --mixed - it is default.  uncommit + unstage changes, changes are left in working tree. git status show the changes as unstaged. need to git add to again make them staged . use example - remove a file that was accidently commited
git reset --hard-  permanent.  uncommit + unstage + delete changes, nothing left. removes from working directory also. uncommited changes lost forever, commited changes can be brought back by reflog.
## ignore a file from being tracked by git
first remove all cached files git rm -r --cached .
then create a .gitignore file - touch .gitignore 
add name of files (with extension) to be ignored
git add .
git commit
to test make changes to file and git status, nothing shows up to be commited

### Branching & Merging
### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
git log --oneline - shows in a shorter way
| `git log --summary` | View changes (detailed) |
| `git diff [source branch] [target branch]` | Preview changes before merging |

