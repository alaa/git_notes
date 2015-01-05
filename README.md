# Git Notes

Collected notes on daily git usage
Please don't be shy to fork and contribute

## Git Configurations:

**List global git config values**

```git config --global -l```

**Edit global git config**

```git config --global -e```

**Set basic config**

```git config --global user.name “name”```

```git config --global user.email “email”```


## Git Log:

```Show git log with patch diffs```

```git log --patch```

```git log -p```

**Show git log with diff stat additions/deletions**

```git log --stat```

**Show git diff between head and -2 commits**

```git diff master~2 master```


*Running `git diff` without args show the diff between the staging index and the current state of the indexed files.*

**Show git diff between head and -2 commits considering specific file “main.rb”**

```git diff master~2 master -- path/main.rb```

Show `git diff` the difference between words rather than lines. Userful for text docs
git diff master~1 master --word-diff

*master^^ is equivalent syntax to master~2*


## Git Remotes:

**Add git remote**

```git remote add origin git@github.com:alaa/repo.git```

**List git remotes**

```git remote --verbose```

```git remote -v```

**List information about git remotes**

```git remote show <remote name>```

```git remote show origin```

**Rename git remote**

```git remote rename <current remote> <new remote>```

```git remote rename origin new_origin```

*delete remote references to branches that have been deleted from the remote repository
git remote prune origin*

**Simulate deletion of the remote references that have been deleted from the remote repository**

```git remote prune origin -n```

**First time Git push to remote with creating the upstream or “tracking branch”**

```git push --set-upstream origin master```

```git push -u origin/master```


** `git clone` command does the upstream set up automatically so there is no need to set it up after cloning a repo **

** `git push` command can take --all option to push all branches and tags to the remote **

** `git push` command can take --force, -f option to force rewriting the branch history. it is very dangerous to do. **


*`git clone` command can take --depth followed by a position integer which creates a shallow clone of the repo, where only a specific number of revisions are downloaded*

*`git clone` command takes --bare, and --mirror which create a repository suitable for hosting on a server*

*`git clone` command takes --recursive or --recurse-submodules flag that initializes all the git submodules in the repository*

*if your master branch is tracking origin/master then git pull is equivalent to git fetch && git merge origin/master*


## Git Branches:

**Listing git branches**

```git branch```

**Creating git branch**

```git branch branch_name```

**List remote tracking branches**

```git branch -r```

**Push a local branch remotely**

```git push --set-upstream origin branch_name```

```git push -u origin branch_name```

**Checkout to a branch with uncommitted tracked changes**

```git checkout -f branch_name```

```git stash```

**Merge feature_branch with master**

```git checkout master```

```git merge feature_branch```

**Delete a branch from the remote repository**

```git push origin :branch_name```

```git push --delete origin branch_name```

**Delete a branch from the local repository**

```git branch --delete branch_name```

```git branch -d branch_name```


## Git File System operations:

**Renaming/moving a tracked file**

```git mv path/filename path/new_filename```

**Deleting a tracked file**

```git rm file```

```git rm -f file #in case of uncommitted changes```

```git rm -r directory```

```git rm -n file #dry_run```


**Deleting untracked files**

```git clean --force```

**Deleting ignored files from .gitignore**

```git clean -f -X```

```git clean -x ```

**Deleting ignored files and directories from .gitignore**

```git clean -xdf```


## Git Changes:

**Resetting file modifications and “index staging area” to the last commit state**

```git reset --hard```

**Resetting only the “index staging area” to last commit state**

```git reset  #Defaults to --mixed```

```git reset --mixed```

**Stashing all uncommitted changes**

```git stash save```

```git stash```

**Listing all stashes**

```git stash list```

**Showing the difference between the working directory and the content of the stash**

```git diff stash@{id}```

*Stash implements a Stack data structure that’s why the latest stash will be on the top of the stack and will hold the ID {0}*


**Re-applying stashed changes and remove the stash from the stack**

```git stash pop```

**Re-applying stashed changes and keep it in the stack for later use in different branches for example.**

```git stash apply```

**Clearing stashes stack**

```git stash clear```

**Tell Git to assume that the file is unchanged**

```git update-index --assume-unchanged filename```

**Listing assumed-unchanged files**

```git ls-files -v ```

**Tell Git to remove the assume-unchanged on file**

```git update-index --no-assume-unchanged filename```


## Git Log 2:

**List commits log by author after specific date**

```git log --author ‘name’ --after ‘Nov 20’ --grep word```

```git log --author ‘name’ --before ‘Nov 20’ --grep word```


**List only merge commits**

```git log --min-parents=2```

```git log --merges```

**Git log format in a nice way**

```git log --oneline --graph --decorate```

**List commits log in reverse order**

```git log --reverse```

**Show the details of a single commit**

```git show commit_id```

**Show who change code per line in a file**

```git blame filename```

```git blame --date=short filename```

```git blame --show-email filename```

```git blame -e filename```

```git blame -L 1,10 filename```


## Git Merges:

**Asking git to generate a merge commit for merging a Fast-Forward branch**

```git merge --no-ff branch_name```

**Show the contents of a file on different branch**

```git show branch_name:file_name```


## Git tags:

**Create a git tag**

```git tag v0.1```

**Show current tags**

```git tag```

**Push tags to the remote**

```git push --tags```

**Generate tag version based on the previous tag**

```git describe --tags```


## Cherry Pick:

**Pick last commit from different branch to your current branch**

```git cherry-pick other_branch```

**Cancel cherry-pick operation in case of conflict**

```git cherry-pick --abort```

**Continuing cherry-pick operation after resolving the merge conflict**

```git cherry-pick --continue```

**Pick specific commit from another branch**

```git cherry-pick <commit-id> --edit```

```git cherry-pick <commit-id> -e```

**Signoff a cherry-pick by person who did it**

```git cherry-pick --signoff <commit-id>```

```git cherry-pick -s <commit-id>```

**List all cherry-picked commits in a branch**

```git cherry --verbose master```

**Git Revert:**

**Reverting a git commit**

```git revert <commit_id>```

