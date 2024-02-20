---
title: Useful Git Commands & Notes
date: 2024-02-20
categories: [git, tutorial]
tags: [git, learning]
---


# Some Useful Git Commands
---

[GIT DOCs](https://docs.github.com/en/get-started/using-git/about-git)

## Git "diff"
- used to get the difference between the current state and last saved/committed changes
- output can be redirected to a file for easier reading

```bash
git diff
```
the above command is used to find difference in current state of repo and last committed state

```bash
git diff @{upstream}
```
this command is used to find the differences between current repo state and with the branch it will be pushed to 

```bash
git diff --name-only
```
this command is used to only get the files names where changes have happened

```bash
git diff origin/master...origin/main > foo.txt
```
this command is used to compare the remote master branch and remote main branch and redirect its output to foo.txt (viewing this file in vim shows it in color)

```bash
git diff origin/master origin/bhaskar-demovideos --color > foo.txt
```
another example of comparing two remote branches

```bash
git diff --stat <commitID>
```
this gives the stats (which files were modified) for a specific commit 

## How to save git credentials
### This link is pretty useful [LINK](https://www.shellhacks.com/git-config-username-password-store-credentials/). It even discusses how to set git credentials for a single repo and also for global usage.

The usernames and passwords for different GitHub repositories will be stored in `~/.git-credentials` file separately on their own lines:
```bash
https://**<USERNAME>**:**<PASSWORD>**@github.com/path/to/repo1.git
https://**<USERNAME>**:**<PASSWORD>**@github.com/path/to/repo2.git
```


## How to Configure Git To Remember Username and Password in a Repository
[LINK](https://www.goranstimac.com/blog/how-to-configure-git-to-remember-username-and-password-in-a-repository/)
So that you don’t have to constantly enter your username and password while working with the git repository, you can save this information as follows:

```bash
git config credential.helper store
git config user.name "Goran Štimac"
git config user.email "info@goranstimac.net"
```

Of course, instead of my name and email details, you will enter your details.

You can also use this short command if you clone a repository

```bash
git clone https://<USERNAME>:<PASSWORD>@github.com/path/to/repo.git
```

IMPORTANT these commands save the login information to a file located in the repository directory

```bash
.git/config
```

which means you can easily reveal user data to others so use it carefully!

## [(Stackoverflow) how to set up username and passwords for different git repos?](https://unix.stackexchange.com/questions/335704/how-to-set-up-username-and-passwords-for-different-git-repos)


According to the below StackOverflow Answer
[Push git config file settings to remote URL](https://stackoverflow.com/questions/47112822/push-git-config-file-settings-to-remote-url)
> he config remains purely local, for security reason, as [I mentioned in 2011](https://stackoverflow.com/a/6548056/6309).  
> So `git push` does _not_ replicate config as well.
>
>One way would be to store a config file as a regular file in the repo, with instruction to set it up once cloned.
>
>But directly change a config setting on a remote server from a client-side command-line is not possible.
>
>Not unless you can establish a direct connection (for instance `ssh`) onto the server, to the the repository path, and execute a `git config` command there.



## How to list out all branches
[Freecodecamp link](https://www.freecodecamp.org/news/git-list-branches-how-to-show-all-remote-and-local-branch-names/)

> git branch -> to see current branch    
> git branch -r -> to see all remote branches     
> git branch -a -> to see all remote and local branches     
> git branch -vv -> to see local branch and the last commit on it     
> git branch -vva -> to see all branches and their last commits     

## Git Log 
Here's a few useful git log command flags that may prove useful
Here's the link on some of these options -> [Git Docs on git log](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

```bash
git log --graph 
```
displays a graph with all the different commits

```bash
git log --graph --oneline --pretty
```
displays a commit graph but with different formatting

```bash
git log --stat
```
displays all the logs but with some more useful stats like which files were modified and which had additions and deletions

```bash
git log --patch or git log -p
```
displays all the logs but with code snippets showing what was changed (useful for quick reviews)


## Search for a keyword in a git commit in git logs

```bash
git log --grep "keyword"
```

you  can also use 

```bash
git log --author "author name" 
```

for getting all commits written by this person/author

## Git Stash
Go here to see git stash commands -> [[Git-Stash]]


## Un-stage a file on Git 
simply do reset and mention the file path, like below :

```bash
git reset <file>
```

Here's a link to some more useful GIT commands via freecodecamp -> [Git Cheat Sheet – 50 Git Commands You Should Know](https://www.freecodecamp.org/news/git-cheat-sheet/)

## GIT Rebasing 
Here's a link from GIT's own documentation talking about GIT Rebase -> [Git - Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)


## Roll back un-staged changes 
You can roll back un-staged changes if you don't want to commit them to git 
This is a little bit like `Ctrl + z` as it makes it like you haven't added anything to your code after your last push/pull from origin 
```bash 
git checkout -- .
```

## Git Reset 
- This helps revert changes or move the head of your branch 
- find more here - [Atlassian git reset](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset), [useful stackoverflow answer](https://stackoverflow.com/questions/9529078/how-do-i-use-git-reset-hard-head-to-revert-to-a-previous-commit), [another useful stack overflow answer](https://stackoverflow.com/questions/31519071/i-want-to-reset-my-current-git-branch-to-master-branch)

Here's how I used it to move my branch `minor-changes` to bring it up to where `master` was 
> - check status using `git status     
> - if there's nothing to commit then find the latest commit or the commit where master is currently at     
> - this can be done using `git log origin/master`     
> - then use the reset command - `git reset <COMMIT ID OF MASTER BRANCH>`      
> - then check the status again using `git status`      
> - if it says that your branch is ahead of `minor-changes` by some commits then you've succeeded      
> - after that just push it to your remote branch - `git push origin minor-changes`  
> - you can change where you're branch is by using `git log` again and it should show you being at the same commit as `origin/master`     

in case of extreme resetting use the force parameter after resetting to the commit on local 
```
git push origin minor-changes -f
```

Be careful that you don't diverge from your origin (upstream) branch as it will prevent you from pushing after reset 

links : [Need to reset git branch to origin version - Stack Overflow](https://stackoverflow.com/questions/9301782/need-to-reset-git-branch-to-origin-version)
[git - master branch and 'origin/master' have diverged, how to 'undiverge' branches'? - Stack Overflow](https://stackoverflow.com/questions/2452226/master-branch-and-origin-master-have-diverged-how-to-undiverge-branches)


## View the git history of a single file 
Read more here -> [Git: View the (detailed) commit history for a single file | alvinalexander.com](https://alvinalexander.com/git/show-commit-history-detailed-for-single-file/)

This command shows the git history of a single file :
```bash
git log -p --follow <filename>
```


## How to Rename a branch in GIT 
Check out this note with the complete process -> [[Rename_a_branch_in_git]] 
```bash 
git branch -m "new_name" 
``` 


## How to keep a file in GIT but no longer track it's changes 
Here's an answer I found on Stack Overlfow : 
[caching - Ignore files that have already been committed to a Git repository - Stack Overflow](https://stackoverflow.com/a/11366713)

If you are trying to ignore changes to a file that's already tracked in the repository (e.g., a dev.properties file that you would need to change for your local environment but you would never want to check in these changes), then what you want to do is:

```
git update-index --assume-unchanged <file>
```

If you want to start tracking changes again:

```
git update-index --no-assume-unchanged <file>
```

See [_git-update-index(1) Manual Page_](https://www.kernel.org/pub/software/scm/git/docs/git-update-index.html).

Also have a look at the `skip-worktree` and `no-skip-worktree` options for update-index if you need this to persist past a git-reset ([_via_](https://stackoverflow.com/a/4633776/367456))

---

Update: Here's a convenient alias for seeing which files are currently "ignored" (--assume-unchanged) in your local workspace

```
git config --global alias.ignored = !git ls-files -v | grep "^[[:lower:]]"
```

### More on Git
- [Interactive staging in Git]({% post_url 2024-02-20-Git-interactive-staging %})
- [Stashing in Git]({% post_url 2024-02-20-Git-stash %})