# VIM cheatsheet

## Motions

`f<character>` moves the cursor *on* the first occurrence of `character`.
`t<character>` moves the cursor *to* the first occurrence of `character` but not *on* it.
`I` goes before the first non-blank character of the current line in insert mode.
`A` goes after the last character of the current line in insert mode.

## Scroll

`zt` scroll such the cursor is at the top of the screen
`zz` scroll such the cursor is centered on the screen
`zb` scroll such the cursor is at the bottom of the screen

## Search and replace

`:s/foo/bar/g`

Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'.

`:%s/foo/bar/g`

Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.

`:%s/foo/bar/gc`

Change each 'foo' to 'bar', but ask for confirmation first.

`:%s/\<foo\>/bar/gc`

Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation.

cf. https://vim.fandom.com/wiki/Search_and_replace#Basic_search_and_replace


## Indentation

https://vim.fandom.com/wiki/Shifting_blocks_visually


## Copy to clipboard

```
:%y+
```
cf. [https://vim.fandom.com/](https://vim.fandom.com/wiki/Copy,_cut_and_paste)
cf. https://stackoverflow.com/questions/749544/pipe-to-from-the-clipboard-in-a-bash-script#comment54347773_749544

`*` -> selection register
`+` -> "ctrl+c" register

## Previous and next edit location

Previous: `Ctrl + o` (old)

Next: `Ctrl + i`

## Search word under cursor

`*` forward, `#` backward

Also, see https://superuser.com/questions/41378/how-to-search-for-selected-text-in-vim

```
y
/
ctrl + r
"
Enter
```


## Surround with characters

https://superuser.com/questions/875095/adding-parenthesis-around-highlighted-text-in-vim
