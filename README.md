# vim-python-docstring
This is a plugin to Vim for creating of docstrings. 

## What it does
Docstrings for methods will contain a **list of arguments**, **list of raised exceptions** and whether the method **yields** or **raises**.

Class docstring will have a **list of atributes**. 

![usage](https://media.giphy.com/media/SUtkPJMUd75Vm1UIxG/giphy.gif)

It uses Python's [ast](https://docs.python.org/3/library/ast.html) library for parsing code. 
This makes it quite **robust** solution, which can handle function signature such as 

~~~{.python}
def foo(a='foo(c,d)',
    b,
    z):
        pass
~~~


## Installation
If you use for example Vundle, add `Plugin 'pixelneo/vim-python-docstring'` to your `.vimrc` file.

Alternatively if you have Vim 8 and newer, you can clone this repository into `~/.vim/pack/<whatever>/start/` where `<whatever>` is *whatever* you want it to be.

## Usage
The plugin has only commands which you can map however you like (i use `<leader>ss` for `:Docstring`).

1. Place cursor at the first line of the object (`def ...` of `class ...`) for which you want to create a docstring
2. Then type `:Docstring` or different command

The plugin uses these commands:

| Command       | Description |
|---------------|-------------|
| Docstring     | Create full docstring 
| DocstringLine | Create empty one-line docstring  

## Options:
There are things you can set.

### The `g:python_indent` option
String which you use to indent your code.

Default: `'    '` (4 spaces).

~~~{viml}
let g:python_indent = '    '
~~~

### The `g:python_style` option
Which docstring style you wish to use.

Default: `'google'`

Possible values = [`'google'`, `'numpy'`, `'rest'`, `'epytext'`]

~~~{viml}
let g:python_style = 'google'
~~~

## Work in progress
Pull requests are welcome as are feature request and issue reports.

You can encounter some situations in which the plugin may not work as expected.
Most notably there *may* be issues if your keyword for refering to instance is not `self` -- in such case it *may* be added to the list of arguments.

There are [more unsolved issues](ISSUES.md).

