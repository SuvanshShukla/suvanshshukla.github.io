---
title: What is Zoxide?
categories: [misc]
tags: [misc, zoxide]
---

## What is Zoxide?
- This is basically a useful little CLI tool which allows you to switch directories faster and smarter 

Here's the GitHub link for this tool -> [GitHub - ajeetdsouza/zoxide: A smarter cd command. Supports all major shells.](https://github.com/ajeetdsouza/zoxide)

## How to install and set-up
> [!Note]
> - The pre-requisite for this tool to work is that you need `fzf` installed. Go to -> [How to use fzf]({% post_url /misc/23-02-2024-how-to-use-fzf %}) for more information on `fzf`

- install zoxide (just use winget it's easier)
```powershell
winget install zoxide 
```
- Next you need to add a init command to your powershell config file, to find your powershell config file use this command #imp 
```powershell
echo $profile
```
- next add this statement to your poweshell config file 
```powershell
Invoke-Expression (& { (zoxide init powershell | Out-String) })
```
- After adding this line to your config file, if you didn't have a config file previously you might want to just create it
- After this zoxide command should work for you 

## Using Zoxide 
- after installing via winget, adding the statement in the config file you can use zoxide 
- To use Zoxide you first need to go into a directory 
```powershell
z /path/to/directory/
z
```
- go into a directory using the keyword `z` then once inside that directory hit `z` to 'remember' it 
- next you can sort of choose which directories to jump between using `zi` command. It opens up an interactive picker 
- you can also hit `zi <search-term>` to sort of search all the remembered directories interactively 


## Other zoxide commands 
These were copied from the GitHub repo 

```bash 
z foo              # cd into highest ranked directory matching foo
z foo bar          # cd into highest ranked directory matching foo and bar
z foo /            # cd into a subdirectory starting with foo

z ~/foo            # z also works like a regular cd command
z foo/             # cd into relative path
z ..               # cd one level up
z _                # cd into previous directory

zi foo             # cd with interactive selection (using fzf)

z foo<SPACE><TAB>  # show interactive completions (zoxide v0.8.0+, bash 4.4+/fish/zsh only)
```


## How to use Zoxide on Git Bash 
- go to the [Zoxide GitHub repo](https://github.com/ajeetdsouza/zoxide) 
- copy paste this into the bash shell 
```bash 
curl -sS https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | bash 
```
- then set up zoxide in your shell using this command : 
```bash 
zoxide init
```
- then some commands will run automatically in git bash and you'll get the following near the end :
```bash 
# =============================================================================
#
# To initialize zoxide, add this to your configuration (usually ~/.bashrc):
#
# eval "$(zoxide init bash)"
```
- after this... basically add this command to your `.bashrc` file, this is this exact command 
```bash 
eval "$(zoxide init bash)"
```
- then reload the `.bashrc` file using the following command : 
```bash 
source ~/.bashrc
```
- then your zoxide `zi` commands should run 