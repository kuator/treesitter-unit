# treesitter-unit

This is a fork of [nvim-treesitter-unit](https://github.com/David-Kunz/treesitter-unit) due to nvim-treesitter's migration to a new `main` branch.
A tiny [Neovim](https://neovim.io/) plugin to deal with [treesitter](https://github.com/tree-sitter/tree-sitter) units.
A unit is defined as a treesitter node including all its children.
It allows you to quickly select, yank, delete or replace language-specific ranges.

For inner selections, the main node under the cursor is selected.
For outer selections, the next node is selected.

![demo-with-highlight](https://user-images.githubusercontent.com/1009936/130355705-5da61f06-52a9-43f4-a98c-7e2df3ae175b.gif)

## Installation

Using neovim's built-in package manager `vim.pack`:
```
vim.pack.add({ "https://github.com/kuator/treesitter-unit" }, { load = true, confirm = false})
```

For [vim-plug](https://github.com/junegunn/vim-plug):
```
Plug 'https://github.com/kuator/treesitter-unit'
```

## Usage

### Select treesitter unit
You can select the current treesitter unit
```
:lua require"treesitter-unit".select(outer?)
```
This function takes an optional Boolean flag to specify if the outer scope should be selected as well, default `false`.
For operations like delete, change, ... please see section "Useful mappings".

### Automatic Highlighting
You can toggle automatic highlighting for the current treesitter unit.
```
:lua require"treesitter-unit".toggle_highlighting(higroup?)
```
As an optional parameter you can specify the highlight group, default: `"CursorLine"`.

Alternative: `enable_highlighting(higroup?)` and `disable_highlighting()`.

### Useful mappings

For init.vim:
```
xnoremap iu :lua require"treesitter-unit".select()<CR>
xnoremap au :lua require"treesitter-unit".select(true)<CR>
onoremap iu :<c-u>lua require"treesitter-unit".select()<CR>
onoremap au :<c-u>lua require"treesitter-unit".select(true)<CR>
```
For init.lua:
```
vim.keymap.set('x', 'iu', function() require"treesitter-unit".select() end, { noremap = true })
vim.keymap.set('x', 'au', function() require"treesitter-unit".select(true) end, { noremap = true })
vim.keymap.set('o', 'iu', function() require"treesitter-unit".select() end, { noremap = true })
vim.keymap.set('o', 'au', function() require"treesitter-unit".select(true) end, { noremap = true })

```

Examples:
- `viu` to select the inner unit
- `cau` to change the outer unit


## Similar plugins

- [nvim-treesitter-textobjects](https://github.com/nvim-treesitter/nvim-treesitter-textobjects) for more fine-granular control
- [nvim-ts-hint-textobject](https://github.com/mfussenegger/nvim-ts-hint-textobject)

## The original video by David Kunz
[![](https://i.ytimg.com/vi/dPQfsASHNkg/hqdefault.jpg?sqp=-oaymwEcCPYBEIoBSFXyq4qpAw4IARUAAIhCGAFwAcABBg==&rs=AOn4CLC_iCGCXjipwKLOxHi2OFBR5XAQfw)](https://youtu.be/dPQfsASHNkg "Let's create a Neovim plugin using Treesitter and Lua")
