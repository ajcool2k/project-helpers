# Git

## show active branch and changes

    git status

## create a new branch from a branch

    git checkout [develop]
    git checkout -b [feature-branch-xxx] [develop]

    # git checkout -b is a shortcut for branch + checkout

    git branch [feature-branch-xxx]
    git checkout [feature-branch-xxx]
    
## push new local branch to remote
    git push -u origin [feature-branch-xxx]

## merge the branch

    git checkout [develop]          # change into target branch
    git pull                        # get latest remote changes
    git merge [feature-branch-xxx]  # pull source into target

## merge file from different branch by interactive merge tool

    git checkout --patch [feature-branch-xxx] path/file.ext

## remove a local branch

    git branch -d [feature-branch-xxx]

## undo last commit but keep changes

    git reset HEAD^
    git reset "HEAD^"   # avoid escaping on windows machines

## change branch but keep changes

    git stash save                  # save changes into stash
    git checkout [develop]          # change to target branch
    git stash apply                 # apply changes from stash into target branch
    git stash drop                  # clear the index of the stash
    
## move branch to specific commit
    git checkout [commit]           # detech HEAD to commit hash
    git branch -f [develop]         # move branch develop to HEAD
    gut checkout [develop]          # set HEAD back to branch
    
## remove sensible data from repository

    git filter-branch --tree-filter 'rm -rf [MY_FILE_OR_FOLRDER]' --prune-empty HEAD        # remove from history
    echo [MY_FILE_OR_FOLRDER] >> .gitignore                                                 # add to .gitignore
    git add .gitignore
    git commit -m 'Removing node_modules from git history'                                  # history update commit
    git gc                                                                                  # clean up and reduce repository size
    git push origin master --force                                                          # push changes to master branch
