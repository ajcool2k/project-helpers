# project-helpers
Useful snippets and project helpers

## Git

### show active branch and changes

    git status

### create a new branch from a branch

    git checkout [develop]
    git checkout -b [feature-branch-xxx] [develop]

    # git checkout -b is a shortcut for branch + checkout

    git branch [feature-branch-xxx]
    git checkout [feature-branch-xxx]

### merge the branch

    git checkout [develop]          # change into target branch
    git pull                        # get latest remote changes
    git merge [feature-branch-xxx]  # pull source into target

### remove a branch

    git branch -b [feature-branch-xxx]

### undo last commit but keep changes

    git reset HEAD^
    git reset "HEAD^"   # avoid escaping on windows machines
