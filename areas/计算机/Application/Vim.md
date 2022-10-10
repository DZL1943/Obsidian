---
title: Vim
author: ""
description: ""
created: "2022-09-26 13:21"
modified: "2022-09-26 16:37"
status: "publish"
categories: []
tags: []
alias: []
links: 
---
## Modes
- BASIC
    - Normal
    - Visual
    - Select
    - Insert
    - Command-Line, Cmdline
    - Ex
- ADDITIONAL

## Keys
![](../../../resources/attachments/vi-vim-cheat-sheet.svg)

| key | cmdline    | normal                                          | shift                                          | ctrl                            | alt | cmd |
|:--- |:---------- |:----------------------------------------------- |:---------------------------------------------- |:------------------------------- |:--- |:--- |
| a   |            | append                                          | append at line end                             |                                 |     |     |
| b   |            | move backward start of word                     |                                                | scroll screen back              |     |     |
| c   |            | change                                          | c$                                             |                                 |     |     |
| d   |            | delete<div>dw de d0 d$ dd</div>                 | d$                                             | 补全<div>down half screen</div> |     |     |
| e   |            | move forward end of word                        |                                                | scroll up                       |     |     |
| f   |            | find in line                                    |                                                | scroll screen forward           |     |     |
| g   |            | gg 文首<div>ge</div><div>g0</div>               | 文尾<div>数字 +G goto line</div>               | 显示文件信息                    |     |     |
| h   |            | &nbsp; 左                                       | 将光标移到顶部                                 |                                 |     |     |
| i   |            | Insert                                          |                                                | jump in                         |     |     |
| j   |            | 下                                              | join line                                      |                                 |     |     |
| k   |            | 上                                              |                                                |                                 |     |     |
| l   |            | 右                                              | 将光标移到屏幕底部                             |                                 |     |     |
| m   |            |                                                 | 将光标移到屏幕中间                             |                                 |     |     |
| n   |            | next                                            |                                                |                                 |     |     |
| o   |            | open newline below                              | open newline above                             | jump out/back                   |     |     |
| p   |            | put/paste                                       |                                                |                                 |     |     |
| q   | quit       |                                                 |                                                |                                 |     |     |
| r   | read       | replace                                         | 连续替换                                       | redo                            |     |     |
| s   | 替换       | cl                                              | cc                                             |                                 |     |     |
| t   |            |                                                 |                                                |                                 |     |     |
| u   |            | undo                                            | undo line                                      | up half screen                  |     |     |
| v   |            | Visual mode                                     |                                                |                                 |     |     |
| w   | save       | move forward start of word                      |                                                |                                 |     |     |
| x   |            | dl                                              | dh                                             |                                 |     |     |
| y   |            | 复制                                            |                                                | scroll down                     |     |     |
| z   |            | zz、zt、zb 将光标所在行移到屏幕中间、顶部、底部 | ZZ 保存退出                                    |                                 |     |     |
| 1   | ! 执行命令 |                                                 |                                                |                                 |     |     |
| 2   |            |                                                 |                                                |                                 |     |     |
| 3   |            |                                                 |                                                |                                 |     |     |
| 4   |            |                                                 |                                                |                                 |     |     |
| 5   |            |                                                 | 括号匹配<div>接数字跳转到百分比</div>          |                                 |     |     |
| 6   |            |                                                 | move to first non-blank char of line           |                                 |     |     |
| 7   |            |                                                 |                                                |                                 |     |     |
| 8   |            |                                                 | `*yy` 复制到剪贴板<div>`*p` 从剪贴板拷贝</div> |                                 |     |     |
| 9   |            |                                                 |                                                |                                 |     |     |
| \/  |            |                                                 | 逆向搜索                                       |                                 |     |     |
| \[  |            |                                                 |                                                |                                 |     |     |
| \]  |            |                                                 |                                                | jump in                         |     |     |
| \`  |            | `` jump                                         |                                                |                                 |     |     |
| .   |            | repeat                                          |                                                |                                 |     |     |

## Doc
[Vim Chinese Documentation](http://vimcdoc.sourceforge.net)

- usr manual
    - 01-12 Getting Started
    - 20-32 Editing Effectively
    - 40-45 Tuning Vim
    - 90        Making Vim Run
- reference
    - General subjects
    - Basic editing
    - Advanced editing
    - Special issues
    - GUI
    - Interfaces
    - Versions
    - Remarks about special system
    - Standard plugins

> 看 Getting Started 1-4 就够了

## Config
配置文件路径
```
# vim --version
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
 2nd user vimrc file: "~/.vim/vimrc"
      user exrc file: "$HOME/.exrc"
       defaults file: "$VIMRUNTIME/defaults.vim"
  fall-back for $VIM: "/usr/share/vim"
```

```vimrc
syntax enable
set nocp
set mouse=a
set nu
set ru
set cul
set cuc
set ts=4
set sw=4
set sts=4
set et
"set list
set backspace=indent,eol,start
set hls
set scs    " smartcase
set is    " incsearch
set sm    " showmatch
set smd    " showmode
set sc    " showcmd
set ai
set fen    " foldenable
"set fdm=indent
set wrap
set whichwrap=b,s,<,>,[,]
set wildmenu
set ls=2
set stl=%<%f\%w%h%m%r\ [%{&ff}/%Y]
set acd
set showtabline=1
```
gvimrc
```gvimrc
set shortmess=atl

if has("gui_running")
    set gfn=Menlo-Regular:h18
    set lines=35 columns=90
    winp 140 20
    colorscheme desert
    set guioptions-=r
    set guioptions+=k
    set transparency=10  " set it at .gvimrc
endif
```

## Plugin

[Vim Awesome](https://vimawesome.com)
