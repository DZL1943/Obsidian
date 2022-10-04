---
title: Emacs
author: ""
description: ""
created: "2022-10-05 04:04"
modified: "2022-10-05 05:42"
status: "draft"
categories: []
tags: []
aliases: []
---

## [Doc](https://www.gnu.org/software/emacs/documentation.html)

建议先看应用内的 tutorial

## Keymap

修饰键 (Modifier Keys)、功能键
- C - Control
- M - Meta/Option/Alt
- S - Shift
- ESC
- s - Super/Command
- H - Hyper
- A - Alt

>[!tip] 
>`C-h b` 列出所有 key-binding  
>`C-h k` 查询按键对应的绑定  
>`M-x describe-keymap ` 可以查看指定模式下的按键定义

### global
常用快捷键 (参考菜单栏)
- C
    - g  quit 退出输入
    - p/n/b/f 上下左右
    - a/e 行首行尾
    - k kill-line
    - r/s 搜索 (C-M-r/s 正则搜索)
    - v scroll-up (可能被 cua-mode 覆盖, M-v scroll-down)
    - w 剪切 (M-v 复制)
    - y 粘贴
    - / undo
    - C-c
    - C-h 帮助
        - b
        - f
        - k
        - m
    - C-x
        - 0 delete-window
        - 1 delete other-windows
        - 2 split-window-below
        - 3 split-window-right
        - o switch-window
        - d dired
        - h 全选
        - b switch buffer (直接按左右方向键可以快速切换)
        - k kill buffer
        - u undo
        - C-b list buffer
        - C-c 保存退出
        - C-e eval
        - C-f find-file
        - C-q read-only-mode
        - C-s save
        - C-t transpose-lines
        - C-; comment-line
- M
    - ! shell-command
    - >/< BOF/EOF
    - % replace
    - M-x
    - M-g
        - g goto-line

## 配置

## 插件

- use-package
- which-key
- company
- smartparens、rainbow-delimiters、flycheck、highlight-indentation、format-all、magit、imenu-list
- ivy、consel、swiper
- smart-mode-line
- drag-stuff、easy-kill、right-click-context、valign
- dashboard、scratch
- org-journal、org-brain、org-roam、org-noter
- slime
- evil
- treemacs、projecttile

## 进阶

### Org

calendar

agenda

### Dired

### EShell