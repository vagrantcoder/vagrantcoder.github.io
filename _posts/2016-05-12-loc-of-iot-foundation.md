---
layout: post
title:  "Line of code log"
categories: IoT foundation
---

## git command 

```sh
$git log --author="xuxiaoxin" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' 
```


go build -ldflags "-X main._BUILD_STAMP_=`date -u '+%Y-%m-%dT%H:%M:%SZ'` -X main._GIT_HASH_=`git rev-parse HEAD`"

## LoC of IoT foundation

2016-05-11: added lines: 20695, removed lines: 16885, total lines: 3810
2016-05-16: added lines: 21248, removed lines: 16889, total lines: 4359
2016-05-18: added lines: 22010, removed lines: 17239, total lines: 4771
2016-05-19: added lines: 22637, removed lines: 17784, total lines: 4853
2016-05-20: added lines: 22727, removed lines: 17824, total lines: 4903
2016-05-24: added lines: 22727, removed lines: 17824, total lines: 4903


