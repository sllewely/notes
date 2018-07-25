# Git basics

### Working locally

View working changes.  This shows modified/deleted files and staged files.
```git status```
A commit is like a checkpoint


View all local branches
```git branch```


Your team has a remote repo.  You can view which repos you are tracking with
```git remote -v```

To get references to all of the branches on the remote repo, you can write
```git fetch origin```
or to the reference of the specific branch
```git fetch origin master```

This doesn't get the branch itself.  To get the remote branch
```git checkout origin/master```
Now you will be in a detached head state.

To create a local branch based off of the branch you are currently in (for example, another branch or from detached head)
```git checkout -b new_branch_name```
To view all branches
```git branch```
