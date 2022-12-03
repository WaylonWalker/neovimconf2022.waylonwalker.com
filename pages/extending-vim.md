---
date: 2022-11-12 18:38:11
templateKey: blog-post
title: extending vim with shell commands
tags:
  - vim
status: draft

---

Vimconf 2022

## The pitch

Extending vim does not need to be complicated and can be done using cli tools
that you might already be comfortable with.  Examples, setting up
codeformatters with autocmds, using lf/ranger as a tui file manager, generating
new files using a template framework like cookiecutter/copier/yeoman, using ag
to populate your quickfix.

## Plugins

Plugins are awesome, this talk will not focus on plugins, but will use them when it makes sense.

## vimscript / lua

lua is an amazing feature of neovom.  Both let you extend neovim in amazing
ways with little effort, but there quickly becomes a limit where you need to
learn a lot more about it to do what you need.

## why a cli

A cli is going to be slower than vimscript/lua in many cases, but its often
something that you already know.  If you write any sort of code its very likely
that you can write a cli in that language that you are familiar with and get
the benefits of all your familiar tooling.

* familiarity
* low barrier to entry
* works good enough

## run a command

``` bash
vimconf!!<esc>!!figlet
```

run it

``` txt
       _                            __ _ _ 
__   _(_)_ __ ___   ___ ___  _ __  / _| | |
\ \ / / | '_ ` _ \ / __/ _ \| '_ \| |_| | |
 \ V /| | | | | | | (_| (_) | | | |  _|_|_|
  \_/ |_|_| |_| |_|\___\___/|_| |_|_| (_|_)
                                           
```

## for .! to work your cli must accept stdin

Many formatters don't support stdin so I made a little shim `genericformat` 

``` bash
genericformat --help

usage: genericformat [-h] --formatter FORMATTER [code]

format some code with a formatter

positional arguments:
  code                  the code to format

options:
  -h, --help            show this help message and exit
  --formatter FORMATTER
                        path to the formatter to run
```

## format some code

Format this one python statement.

```python
print('here')
```

press !!genericformat --formatter black<cr>

```python
print('here')
```


Now try a multiline statement.

``` python
def func(arg_one, arg_two, arg_three, kwarg='one',):
   ...
```

press Vj!!genericformat --formatter black<cr>

``` python
def func(
    arg_one,
    arg_two,
    arg_three,
    kwarg="one",
):
    ...
```


## using BufWritePost for formatters


``` lua
local settings = require'waylonwalker.settings'

M.waylonwalker_augroup = augroup('waylonwalker', { clear = true })
M.format_python = function()
    if settings.auto_format.python then
        vim.cmd('silent execute "%!tidy-imports --black --quiet --replace-star-imports --replace --add-missing --remove-unused " . bufname("%")')
        vim.cmd('silent execute "%!isort " . bufname("%")')
        vim.cmd('silent execute "%!black " . bufname("%")')
    end
end

autocmd({ "BufWritePost" }, {
    group=M.waylonwalker_augroup,
    pattern = { "*.py" },
    callback = M.format_python,
})
```

## File Navigation
_markata_

I built my own static site generator, one thing that it can do pretty well is
navigate through large sets of posts and list out their path.  I can pipe this right into 

``` bash
markata list --map path --filter '"til" in path' --fast --no-pager
```

## File Navigation

``` lua
vim.keymap.set('n', 'geit', '<cmd>terminal markata list --map path --filter \'"til" in path\' --fast --no-pager<cr>')
```

``` lua
vim.keymap.set('n', 'geit', '<cmd>Telescope find_files find_command=markata,list,--map,path,--filter,date==today,--fast<cr>')
```

``` lua
vim.keymap.set('n', '<leader>ee', '<cmd>vertical terminal lf<cr>')
```

## FloatTerm

``` lua
vim.keymap.set('n', '<leader><leader>w', '<cmd>FloatermNew waylonwalker<cr>')
vim.g['floaterm_opener'] = 'vsplit'
vim.keymap.set('n', 'gee', '<cmd>FloatermNew lf<cr>')
```

## vimgrep over hidden files ##

I know all the files that I care to search for are called build.yml, and they
are in a hidden directory.

``` vim
:args `fd -H build.yml`
:vimgrep /upload docs/ ##
```

Once opened as a buffer by using args, and a handy fd command I can vimgrep
over all the open buffers using `##`

> Open buffers are represented by ##

Now I can just `dap` and `:cnext` my way through the list of changes that I
have, and know that I hit every one of them when I am at the end of my list.
And can double check this in about 10s by scrolling back through the quickfix
list.
