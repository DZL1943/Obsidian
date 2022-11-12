---
title: Vim 和 Emacs
author: ""
description: ""
created: "2022-11-13 02:58"
modified: "2022-11-13 02:58"
status: "draft"
categories: []
tags: []
aliases: []
---

- Vim 是基于 mode 的, 而 Emacs 有 major mode、minor mode 且可由插件定义
  - Vim 的操作模式更适合在 terminal 下编程, Emacs 的按键更为通用但编辑效率不如 Vim
- 两者均可在 terminal、GUI 下使用
  - terminal 下预装的是 Vim, 或许因为 Vim 更加适合、轻量、易于配置
  - Vim 的 GUI 版本更加现代? 但总体上个人更倾向于 Emacs
- Vim 使用 VimScript 配置 (nvim 也可使用 lua 配置), Emacs 使用 EmacsLisp 配置
  - 前者更加便捷, 后者更具扩展性 (插件开发貌似会更加困难?)