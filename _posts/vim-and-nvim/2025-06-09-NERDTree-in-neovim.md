---
title: How to add and use NERDTree plug-in with neovim
categories: [nvim]
tags: [nvim, nvim-plugins, nerdtree]
---

## Prerequisites

- `vim-plug` installed 
- `init.lua` file or `init.vim` file
- `Neovim` obviously

## Steps to follow

Add the following to your `init.lua` file: 

```lua
vim.cmd([[
call plug#begin()

" NERDTree
Plug 'preservim/nerdtree'

" Optional: NERDTree icons
Plug 'ryanoasis/vim-devicons'

" Optional: NERDTree Git integration
Plug 'Xuyuanp/nerdtree-git-plugin'

call plug#end()
]])
```

then save and source your `init.lua` file using `:luafile %` 

then install the plug-in by running: `:PlugInstall` 

## NERDTree basics

- to open NERDTree run: `:NERDTreeToggle`
- or add the following keymap to your `init.lua` 

```lua
vim.api.nvim_set_keymap('n', '<leader>n', ':NERDTreeToggle<CR>', { noremap = true, silent = true })
```

Additional Commands:

`:NERDTreeFind` - Focus on the current file in NERDTree.
`:NERDTreeRefreshRoot` - Refresh the root directory.

You can customize NERDTree further by adding options to your `init.lua` or `init.vim`. For example:

```lua
-- Example in init.lua
vim.g.NERDTreeShowHidden = 1 -- Show hidden files
vim.g.NERDTreeIgnore = { '.git$', 'node_modules$', '.cache' } -- Ignore certain directories
```

## Finding the current file in NERDTree

- sometimes you want to reveal the current file in the file tree structure
- to do this just hit `:NERDTreeFind`
- this will open up NERDTree to wherever the file is located
- you can also add a custom mapping for this

```lua
vim.api.nvim_set_keymap('n', '<leader>fi', ':NERDTreeFind<CR>', { noremap = true, silent = true, desc='Reveal the current file in NERDTree' })
```

