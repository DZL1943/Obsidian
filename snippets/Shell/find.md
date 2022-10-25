---
title: find
author: ""
description: ""
created: "2022-09-28 14:36"
modified: "2022-09-28 14:36"
status: "draft, in progress, done, publish, archive"
categories: []
tags: []
alias: []
links: 
---

```shell
# 排除目录
find . ! \( -path './.trash/*' -o -path './.obsidian/*' \) -name '*.png'

find . ! -path './.trash/*' ! -path './resources/*' ! -path './.obsidian/*' -name '*.png' -exec ls -lh {} \;
```

```shell
# 查询大文件
find . -size +100M -exec ls -lh {} \;
```