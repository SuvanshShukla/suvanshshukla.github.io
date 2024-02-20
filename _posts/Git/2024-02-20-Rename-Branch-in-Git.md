---
title: How to rename a branch in Git
date: 2024-02-20
categories: [git, tutorial]
tags: [learning, git]
---


LINK TO MAIN GIT Commands NOTE -> [Some-useful-git-commands]({% post_url 2024-02-20-Useful-Git-Notes %}) 

Here's the Stackoverflow answer that helped -> [Change a branch name in a Git repo - Stack Overflow](https://stackoverflow.com/questions/3866951/change-a-branch-name-in-a-git-repo) 
# How to rename a branch in GIT 
This process involves three steps 
1. rename the branch on local 
2. delete the pre-existing branch with the old name (otherwise you won't be able to push it as the branch only points to the older name at origin) 
3. push the changes to origin 

## 1. Rename the branch on local 
```bash
git branch -m "new name"
```
This will rename the branch you're on to the new name you have specified 


## 2. Delete old name branch 
```bash 
git push origin :old_branch_name 
```
This will delete the old branch with the old_name 

## 3. Push to Origin 
```bash 
git push origin new_name
```
This will push the changes to `origin/new_name` with the old branch with the old name deleted  


> [!Note]
> If you haven't pushed your new branch to origin yet then changing the name will mean that you don't need to do step #2 : Delete old name branch. You can just push the renamed branch and it will create an origin branch with this new name 


