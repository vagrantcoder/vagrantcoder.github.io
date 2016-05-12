---
layout: post
title:  "Line of code log"
categories: IoT foundation
---

## git command 

git log --author="xuxiaoxin" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' 


## LoC of IoT foundation

2016-05-11: added lines: 20695, removed lines: 16885, total lines: 3810