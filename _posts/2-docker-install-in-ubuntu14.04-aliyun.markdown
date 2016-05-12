---
layout: post
title:  "在ubuntu14.04阿里云模板上安装docker"
date:   2015-10-05 12:47:25
categories: docker
---

## 根据docker官网上的流程

http://docs.docker.com/linux/step_one/

$ wget -qO- https://get.docker.com/ | sh

这个命令会下载一个安装脚本自动把docker安装上

## 测试docker是否安装正确

$ docker run hello-world

会运行一大段文字，注意其中的

Hello from Docker.
This message shows that your installation appears to be working correctly.

表示安装成功

## mount disk to /opt

$vim /etc/fstab

加入一行

/dev/sdaX /opt ext4 defaults 0 0


## 运行nsq

### 首先运行 lookup

docker run --name lookupd -p 4160:4160 -p 4161:4161 nsqio/nsq /nsqlookupd

这个container的ip地址是192.168.0.2, 可以用

docker inspect lookupd 来查看

###  接下来运行 nsqd

docker run -d --name nsqd -p 4150:4150 -p 4151:4151 nsqio/nsq /nsqd --broadcast-address=192.168.0.2 --lookupd-tcp-address=192.168.0.2:4160

需要指定一下 lookupd 的地址








