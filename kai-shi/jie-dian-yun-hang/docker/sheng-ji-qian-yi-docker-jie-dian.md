# 升级/迁移 Docker 节点

## 一、准备工作 <a href="#4icdn" id="4icdn"></a>

<mark style="color:red;">必须先导出原节点私钥！！！</mark>

私钥导出教程：[点击前往](yun-hang-docker-jie-dian.md#ea06b35261c8e025ea9791e1ebea8e9a)

准备好私钥，用于导入节点账号。

## 二、停止原节点 <a href="#ki4nt" id="ki4nt"></a>

<mark style="color:orange;">如果是迁移节点，可跳过该步骤</mark>

停止并删除原节点：

```
$ docker rm -f starcoin-main
```

删除原节点 ipc 文件：

```
$ rm -rf /data/starcoin/main/starcoin.ipc
```

更新最新版的镜像：

```
$ docker pull starcoin/starcoin
```

该步骤操作截图如下：

![](<../../../.gitbook/assets/1 (1).png>)

## 三、启动新节点 <a href="#nvqnh" id="nvqnh"></a>

> 小提示：
>
> * 若无需启动矿池，可以删除 -p 9880:9880，和最后的参数：--stratum-address 0.0.0.0 --stratum-port 9880；
> * \-n main：指定主网，测试网可写 barnard；

```shell
# 运行新版本
$ sudo docker run --restart=always \
    --name starcoin-main \
    -d -p 9880:9880 \
    -v /data/starcoin/:/data/starcoin/ \
    starcoin/starcoin \
    /starcoin/starcoin \
    -n main \
    -d /data/starcoin \
    --disable-metrics true \
    --miner-thread 0 \
    --stratum-address 0.0.0.0 --stratum-port 9880

# 查看节点运行状态
$ docker ps -a
```

操作截图：

![](<../../../.gitbook/assets/2 (1).png>)

## 四、导入私钥并设为默认账号 <a href="#29p2e" id="29p2e"></a>

检查新版本默认账号：

```
$ docker exec -it starcoin-main /bin/bash

> /starcoin/starcoin --connect /data/starcoin/main/starcoin.ipc console

% account default
```

截图如下：

![](<../../../.gitbook/assets/3 (1).png>)

<mark style="color:red;">如果上面的账号是自己之前的，就结束了，如果账号不对，重新设置：</mark>

导入私钥：

```
% account import -i 私钥
```

设置为默认账号：

```
% account default 私钥对应的账号
```



