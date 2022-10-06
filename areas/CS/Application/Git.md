---
title: Git
author: ""
description: ""
created: "2022-09-26 09:58"
modified: "2022-09-27 11:12"
status: "publish"
categories: []
tags: []
alias: []
links: 
---

## 基础
![image](https://git-scm.com/book/en/v2/images/areas.png)
三种状态和阶段 (通过 `git status` 命令查询):
- untracked、modified
- staged (index)
- committed (HEAD)

## 实践
basic workflow
- git init / git clone
- git status
    - diff
    - checkout
- git add
- git commit
    - --amend
    - [reset](https://git-scm.com/book/zh/v2/Git-工具-重置揭密#_git_reset)
        - --soft: 撤销 commit
        - --mixed (default): 并且取消暂存
        - --hard
    - revert
- git log
- git pull/push
- code-review
- CICD

## 进阶
### 分支和远程分支
- stash
- merge
    - cherry-pick
- rebase
    - pick
    - reword
    - edit
    - squash
    - fixup
    - exec
    - break
    - drop
    - label
    - reset
    - merge
### Tag
### Submodule

## Tips & Issues
- [gitignore](https://docs.github.com/cn/get-started/getting-started-with-git/ignoring-files)
- [alias](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)
    - ga add
        - gaa
    - gb branch
        - gba
    - gc commit
        - gcam
    - gco checkout
    - gd diff
    - gl pull
    - gm merge
    - gp push
    - gst status
- 如何让 gitignore 仅作用于 push? 如何在使用 git 的同时避免隐私信息推送到远程?
    - 假如用分支区分, 如何在 merge 时应用 ignore?
    - 如何把文件夹变成子模块? 
        - [Splitting a subfolder out into a new repository - GitHub Docs](https://docs.github.com/en/get-started/using-git/splitting-a-subfolder-out-into-a-new-repository)
        - [Nested git repositories without remotes (a.k.a. git submodule without remotes) - Stack Overflow](https://stackoverflow.com/questions/6100966/nested-git-repositories-without-remotes-a-k-a-git-submodule-without-remotes)
- git status 中文乱码问题  `git config --global core.quotepath false`
- 计算仓库大小 `git count-objects -vH`
- 清空提交历史 [git - how to delete all commit history in github? - Stack Overflow](https://stackoverflow.com/questions/13716658/how-to-delete-all-commit-history-in-github)

## Internal