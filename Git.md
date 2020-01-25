# Git

**configure name for git**

```bash
git config --global user.name "Full Name"
git config --global user.email "email@address.com"
```

**create local git repository**

```bash
git init
```

**show active branch and changes**

```bash
git status
```

**create a new branch from a branch**

```bash
git checkout [develop]
git checkout -b [feature-branch-xxx] [develop]

# git checkout -b is a shortcut for branch + checkout

git branch [feature-branch-xxx]
git checkout [feature-branch-xxx]
```

**push new local branch to remote**

```bash
git push -u origin [feature-branch-xxx]
```

**merge the branch**

```bash
git checkout [develop]          # change into target branch
git pull                        # get latest remote changes
git merge [feature-branch-xxx]  # pull source into target
```

**merge file from different branch by interactive merge tool**

    git checkout --patch [feature-branch-xxx] path/file.ext

**copy commits from a different branch to the HEAD**

```bash
git checkout [develop]                      # change HEAD to desired branch or commit    
git cherry-pick [commitHash] [commitHash]   # pick two commits from a different branch to the HEAD
```

**remove a local branch**

```bash
git branch -d [feature-branch-xxx]
```

**remove all deleted remote branches**

```bash
git fetch --prune
```

**undo last commit but keep changes**


```bash
git reset HEAD^
git reset "HEAD^"   # avoid escaping on windows machines
```

**change branch but keep changes**

```bash
git stash save -u               # save changes (including untracked files) into stash
git checkout [develop]          # change to target branch
git stash apply                 # apply changes from stash into target branch
git stash drop                  # clear the index of the stash
```

**move branch to specific commit**

```bash
git checkout [commitHash]       # detech HEAD to commit hash
git branch -f [develop]         # move branch develop to HEAD
gut checkout [develop]          # set HEAD back to branch
```

**remove sensible data from repository**

```bash
# remove from history
git filter-branch --tree-filter 'rm -rf [MY_FILE_OR_FOLRDER]' --prune-empty HEAD        

echo [MY_FILE_OR_FOLRDER] >> .gitignore              # add to .gitignore
git add .gitignore
git commit -m 'Removing node_modules from history'   # history update commit
git gc                                               # clean up and reduce repository size
git push origin master --force                       # push changes to master branch
```

**adding a tag to a commit**

```bash
git tag v1.2                            # add tag v1.2 to current branch and commit
git tag -a v1.2 [commitHash]            # add tag v1.2 to existing commit
```

