---
title: How to use fzf 
categories: [misc]
tags: [misc, fzf]
---


## What is fzf?
- `fzf` otherwise known as fuzzy finder is a search utility for the CLI
- Here's it's installation info on GitHub : [GitHub - junegunn/fzf: :cherry\_blossom: A command-line fuzzy finder](https://github.com/junegunn/fzf#installation)

## How to use
```bash
> fzf <then press> enter
```
- after entering `fzf` into the CLI you'll get a search line which allows you to enter more key words and narrow down your search 

```bash 
> fd | fzf | cd
```
- this combination of commands allows you to use `fzf` to search through directories and go into them 
- just be careful that you have selected the exact directory that you want to `cd` into 

```bash
> fzf --preview 'cat {}'
```
- this command opens a little preview window that shows what's inside the file selected right now in fzf 
- for more info on how the preview window works check out : [GitHub - junegunn/fzf: :cherry\_blossom: A command-line fuzzy finder](https://github.com/junegunn/fzf#installation)
- 
