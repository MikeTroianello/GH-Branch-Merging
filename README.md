# GH-Testing

## Overview

This is to establish the common practice that the Legato team uses. These commands will be the main focus of how we use Github, at least for now

## Notes

Any time chevrons are used, they are only for example, don't include them in your commands. eg: branch-name should never be used, this is just a hypothetical name for a branch, like login-fix or something. No command requires chevrons.

# The Commands

## Creating a New Branch

### git checkout -b branch-name

-b creates a new branch. Create all of your code on this branch, not on master. A new branch should always be made when the previous branch is pushed and merged.

### git checkout branch-name

This switches between branches. If you need to go back to master, you can use git checkout master

## Pushing the new branch for a Pull Request review

### git add .
### git commit -m "comment"
### git push -u origin branch-name

## IMPORTANT

If a correction needs to be made to your code, don't push a new branch, or create a new commit, just amend the previous one:

### git add .
### git commit --amend

This will open the text editor inside your terminal. When this is open, enter this text command:

:wq then press enter

If something accidentally gets entered in, try using the esc key

### git push --force


## Once a branch has been merged

Go ahead and delete your branch, this can be done with a few commands:


### git checkout master
### git pull
### git branch -d The-branch-you-just-merged

If you get an error deleting the branch, you can use -D for a forceful delete, but make sure you know what you're doing before you delete anything.


## Pulling someone else's code before your branch is done

If someone else merges their branch before you can push yours, take these steps:

## git stash

This will save all of your local branch changes. THIS IS IMPORTANT.

## git checkout master
## git pull
## git checkout the-branch-you-just-came-from
## git stash pop

This last command will take your local changes and fit them in with the changes made to the most recent branch.
If two people were working on the same screen, you'll likely have a couple merge conflicts, and will have to fix this inside your text-editor


## Accidentally making more than one commit

If you make a change to your branch, but make a regular commit instead of using --amend, you can fix this with:

## git reset --soft HEAD~x && git commit -m "something"

This will push all of your commits into one. Make sure x is the accurate number of commits you have.