---
layout: post
title:  "Docker在阿里云上的配置"
date:   2016-05-04
categories: docker
---
##  安装docker
使用 daocloud 的源

```
$curl -sSL https://get.daocloud.io/docker | sh
```

## 配置
```
$service docker stop

$rsync -a /var/lib/docker/* /opt/docker/
```
```
$vim /etc/default/docker
```
更改docker 运行时路径，并使用阿里的镜像
```
DOCKER_OPTS="-g /opt/docker/ --registry-mirror=https://kw3bpzgp.mirror.aliyuncs.com"
```
重启 docker

```
$service docker restart
```

ref: https://github.com/docker/docker/issues/3127

## 安装 mysql
```
$docker run --name yt-mysql57 -v /opt/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root@1234 -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```
进入容器并使用 mysql-client
```
$docker exec -it yt-mysql57 bash -l
$mysql -uroot -p
```

ref: https://hub.docker.com/_/mysql/

## 安装redmine
```
$docker run -d --name yt-redmine  -v /opt/redmine/data:/usr/src/redmine/files --link yt-mysql57 -e MYSQL_DATABASE=redmine -p 3000:3000 redmine:3.2
```





