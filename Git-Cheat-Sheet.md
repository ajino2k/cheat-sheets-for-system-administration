# Git Cheat Sheet  
# Branches
Create New Branch
reate a new git branch and switch to it\
    
```git checkout -b```

and create it on origin too  

```git push --set-upstream origin <branch name>```  

# Tracking Remote Branches
To follow additional branches in your local repo follow these steps:

Find out all existing remote branches</br>
```git branch -r```</br>
And track one of them locally</br>
```git branch --set-upstream-to```

# Remove Branch
Remove git branch locally with

```git branch -d```
and remove on origin too</br>

```git branch -d -r origin/``` </br>
```git push origin :```
Alternatively remove on origin and then prune locally</br>

# Remove stale
When remote branches disappear clean them from your local repo with</br>
```git remote prune origin```

# Rebasing
To rebase on master</br>
```git rebase master```

# Solve Merge Conflicts
When a rebase fails manually fix files and

```git add``` </br>
```git rebase --continue```

# Move commits onto new branch 

```git branch```    
```git reset --hard HEAD~1```    # 1 to move 1 commit   
```git checkout```    

# Commits

Amending changes

```git add```</br>
```git commit --amend```

Apply patches

```git apply --stat cool_feature.patch```    # Check what the patch will do   
```git apply --check cool_feature.patch```   # Check if the patch fails   
```git am --signoff < cool_feature.patch```   

Create patches

```git format-patch -1```     # Creates one patch file for the commit   
```git format-patch -2 HEAD ```          # Creates two patch files for last two commits on HEAD   
```git format-patch -3 HEAD --stdout```  # Print last 3 commit changes on stdout    

Solving Mistakes

```git reset HEAD []```   
Accidental commit of too many files

```git reset --soft HEAD^```    
```git status```      # to list all added files   
```git reset```   # to remove incorrectly added files   

Stashing Changes

```git stash "Some test I made"  ```  # Stash some changes away   
```git stash list  ```                # List stashes    
```git stash show stash@{0}  ```      # Show changes file in last stash   
```git stash show -p stash@{0}  ```   # Show patch for last stash   
```git stash apply stash@{0}```       # Get last stash active again   
```git stash drop stash@{0}```        # Delete last stash   
```git stash pop     ```              # Apply and remove last stash   
```git stash clear  ```               # Delete all stashes    

Stash just some files by adding all others first 
and using --keep-index

```git add ```    
```git stash --keep-index```

List Commits in One Line Each

```git rev-list --all --pretty=oneline```

Search in Commits

```git log -p -S -- ```</br>
```git log -p -G -- ```

# Misc

Update submodules   
```git submodule update --init --recursive```

Enable git password Caching
To keep passwords for 1h run

```git config --global credential.helper 'cache --timeout=3600'```

Remove all repo files from a directory

```git clean -ffrx```

List Branch in Bash Prompt PS1

```export PS1='\u@\h:\w\$ "```    
```export PS1='\u@\h:\w$(git branch &>/dev/null; echo $(__git_ps1 "(%s)"))\$ '```   
```cuongnp2@cuongnp2:~/project/src(master)$ ```   

Push Dry Run

```git push --dry-run --porcelain```

git-write-tree: error building trees

```git reset --mixed```

Merge two repos

```cd repo2```    
```git remote add repo1 <path to repo1>```    
```git fetch repo1```   
```git merge -s ours --no-commit repo1/master```    
```git read-tree --prefix=<subdir> -u repo1/master```   
```git commit```    
