---
title: Emacs
author: ""
description: ""
created: "2022-10-05 04:04"
modified: "2022-10-05 16:56"
status: "publish"
categories: []
tags: []
aliases: []
---

## [Doc](https://www.gnu.org/software/emacs/documentation.html)

- tutorial
- manual
- elisp
- other
    - Org mode

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
    - C-h 帮助 (按 q 可以关闭临时窗口)
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
    - <> EOF/BOF
    - % replace
    - M-x
    - M-g
        - g goto-line

## 配置
[Init File (GNU Emacs Manual)](https://www.gnu.org/software/emacs/manual/html_node/emacs/Init-File.html)

```lisp
(package-initialize)

;; === general settings
(setq inhibit-startup-message t)    ;; no startup message
(setq initial-major-mode 'text-mode)   ;; scratch default mode
(setq initial-scratch-message nil)    ;; clean scratch default text
(setq help-window-select 't)    ;; auto switch to help window, input 'q' for quit
(global-linum-mode t)   ;; show line number (legacy)
(setq column-number-mode t)   ;; show column number at status bar

(ido-mode t)    ;; suggest options

(setq-default tab-width 4)
;; (setq-default indent-tabs-mode nil)

(global-set-key (kbd "C-c I") (lambda()(interactive)(find-file "~/.emacs.d/init.el")))

;; === UI settings
(if (not window-system)
  (progn 
    (message "terminal")
    (mouse-wheel-mode 1)
    (menu-bar-mode -1))
  (progn 
    (message "GUI")
    
    (set-face-attribute 'default nil :height 180)

    (setq initial-frame-alist `(
      (tool-bar-lines . 0)
      (vertical-scroll-bars . nil)
      (top . 28) (left . 150) (width . 90) (height . 35)
      (cursor-type . bar) (cursor-color . "green")))
    
    ;; (load-theme 'misterioso' t)
    ;; (set-face-attribute 'region nil :background "#6B8E23" :foreground "white")
    ;; (set-frame-parameter nil 'alpha 85)
  ))


;; === org settings
(with-eval-after-load 'org
  (setq org-adapt-indentation nil)
  (setq org-src-fontify-natively t)
  (setq org-startup-truncated nil)
  
  ;; (org-babel-do-load-languages 'org-babel-load-languages '((emacs-lisp . t) (shell . t) (python . t)))
)


;; === use-package

```

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

### Eshell