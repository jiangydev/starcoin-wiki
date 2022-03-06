# 运行 Docker 节点



## 一、准备工作 <a href="#rnxwk" id="rnxwk"></a>

已安装 Docker 的 Ubuntu/CentOS 等系统（也包括 Windows 10 专业版，命令类似），且 docker 是运行状态；

## 二、运行节点 <a href="#cac404006338d05dc87f6ab330ef4fbe" id="cac404006338d05dc87f6ab330ef4fbe"></a>

执行如下命令运行节点：

```shell
$ sudo docker run --restart=always \
    --name starcoin-main \
    -d -p 9880:9880 \
    -v /data/starcoin/:/data/starcoin/ \
    starcoin/starcoin \
    /starcoin/starcoin \
    -n main \
    -d /data/starcoin \
    --disable-metrics true \
    --stratum-address 0.0.0.0 --stratum-port 9880 \
    --miner-thread 0
```

> 小提示：
>
> * 若不需要启动矿池功能，可以去掉 -p 9880:9880，和最后的参数 --stratum-address 0.0.0.0 --stratum-port 9880；
> * \-n main：指定主网 main，测试网可以改为 barnard；
> * \--miner-thread 0：挖矿线程数，可自行调整；

查看节点运行状态：

```
$ sudo docker ps -a
```

![](<../../../.gitbook/assets/image (38).png>)

## 三、导出账号及私钥 <a href="#ea06b35261c8e025ea9791e1ebea8e9a" id="ea06b35261c8e025ea9791e1ebea8e9a"></a>

### 3.1 进入节点并连接Starcoin控制台 <a href="#b40f1d7ab7ce8a042c7fc157db40a639" id="b40f1d7ab7ce8a042c7fc157db40a639"></a>

进入节点：

```
$ sudo docker exec -it starcoin-main /bin/bash
```

连接控制台，看到最后返回 `starcoin%` 就说明成功到控制台了：

```shell
/starcoin/starcoin --connect /data/starcoin/main/starcoin.ipc console
```

![](<../../../.gitbook/assets/image (1) (1).png>)

### 3.2 查看账号并导出私钥 <a href="#603e8a317e1ae66c0f224cb12c9f199a" id="603e8a317e1ae66c0f224cb12c9f199a"></a>

前提：连接Starcoin控制台

查看默认账号：

```
account default
```

导出默认账号的私钥：

```
account export 0x8b79fdf7bd004b72ea4bd83289429455
```

如下图所示，导出了 account 和 private key（私钥），<mark style="color:red;">私钥一定要保存！！！</mark>

![](<../../../.gitbook/assets/image (18).png>)

### 3.3 查看账号公钥及余额 <a href="#e024ecc0a47d5aa9b300089b683cab90" id="e024ecc0a47d5aa9b300089b683cab90"></a>

这里只给下命令：

```
account show 0x8b79fdf7bd004b72ea4bd83289429455
```

![](<../../../.gitbook/assets/image (7).png>)

字段解释：

* public\_key: 账户公钥；
* balances：账户余额。`0x00000000000000000000000000000001::STC::STC` STC 余额，精度 9 位，出块后该余额会增加；

### 3.4 退出节点和控制台 <a href="#0ddf58a8254b8d35123044cf7d67b617" id="0ddf58a8254b8d35123044cf7d67b617"></a>

看截图：

```
$ exit
```

![](<../../../.gitbook/assets/image (4) (1).png>)

## 四、区块浏览器 <a href="#aac9c43b1ce7ef0cbe1c4bc3e9b87f22" id="aac9c43b1ce7ef0cbe1c4bc3e9b87f22"></a>

地址：[https://stcscan.io](https://stcscan.io)

![](<../../../.gitbook/assets/image (5) (1).png>)

