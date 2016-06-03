---
layout: post
title:  "IoT foundation 需要 backlog"
categories: IoT foundation
---

## Schema

* 设备和各个字段，字段类型，读写权限，是否时序存贮都由 Schema 定义
* 数据实际存贮的时候是以json格式进行序列化
当前支持的字段类型为 string 和 number
* 字段具有timeseries属性，会以时序方式存贮这个字段的每一次数据变更


```sql
create schemaName (
    id string
    dev_type number
    name string
    dis_temp string timeseries
)
```



## Topic uri

### 真实的设备 device 

真实的设备使用以下 uri 来注册

```
/schemaName/deviceId
```

> 比如说，海林的设备可以表达为 /hailin/ACCFAAAAAA
> 

### device tops

## Device

每种设备可以表示为 Device

Device 有 Schema

Device 有 Potocol

Schema 定义字段，字段类型，读写权限等

Potocol 定义设备端协议

Device 连接一个主 topic

Device 通过主 topic 的 #device channel 连接实际的设备

Device 负责创建 topic



## Topic

Topic 包含多个 channel, 其中有一个默认的 #device channel, 这个 channel 和实际的设备相连


## Channel




## 设备注册流程

参考 mqtt 的流程

### 设备上电、连接、认证

> CONNECT
    
    
> CONNACK

### 发布状态、数据变更

> 
 
