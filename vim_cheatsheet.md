# VIM cheatsheet

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

cf. https://stackoverflow.com/questions/749544/pipe-to-from-the-clipboard-in-a-bash-script#comment54347773_749544

## Previous and next edit location

Previous: `Ctrl + o` (old)

Next: `Ctrl + i`