# Notes

## Install a vim plugin

Vim 8 has native package loading. Leave .vimrc alone and just do this:

```
$ mkdir -p ~/.vim/pack/typescript/start
$ cd ~/.vim/pack/typescript/start
$ git clone https://github.com/leafgarland/typescript-vim.git
```

## Tree

Iignore directories with patterns.

```
$ tree -I node_modules
$ tree -I 'node_modules|test'

# List directories before files.
$ tree --dirsfirst
```
