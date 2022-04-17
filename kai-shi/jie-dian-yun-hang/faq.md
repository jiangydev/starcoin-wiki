# FAQ

## 一、节点同步到哪儿了？同步要多长时间？ <a href="#qzomi" id="qzomi"></a>

连接节点 console，执行下面的命令：

不知道如何进入 console？可参考如下教程：

* Docker 节点进入控制台：[点击前往](docker/yun-hang-docker-jie-dian.md#b40f1d7ab7ce8a042c7fc157db40a639)
* Windows 节点进入控制台：[点击前往](windows/zai-windows-shang-yun-hang-jie-dian.md#b40f1d7ab7ce8a042c7fc157db40a639)

```
node sync status
```

执行上面的命令，可以看到当前的区块高度：

![node sync status](<../../.gitbook/assets/image (17).png>)

滑到最后一行，会有两种结果：

* 结果1：如果返回下面截图中的内容，表示在同步中，当 chain\_status.head.number 和 state.Synchronizing.target.number 一致，才同步完成。

![node synchronizing](<../../.gitbook/assets/image (29).png>)

* 结果2：同步完成

![node Synchronized](<../../.gitbook/assets/image (35).png>)

A：同步进度执行上面的命令查看，同步耗时可以根据命令执行结果自己预估。

## 二、区块数据同步太慢了，怎么能快点？ <a href="#jz3hs" id="jz3hs"></a>

### 1. 解决方案

下载其他节点的主网区块数据到新节点，并以下载的区块数据启动节点。

### 2. 操作步骤

#### 2.1 下载 Starcoin 节点数据导出工具

下载 `starcoin_db_exporter` 节点数据导出工具，这个是必须的，同步脚本需要使用到。

```shell
$ wget https://github.com/starcoinorg/starcoin/releases/download/v1.9.1/starcoin-ubuntu-18.04.zip
$ unzip starcoin-ubuntu-18.04.zip
$ cp starcoin-artifacts/starcoin_db_exporter starcoin_db_exporter
```

#### 2.2 下载区块数据 <a href="#hkw1t" id="hkw1t"></a>

先下载官方提供的同步脚本工具：

```shell
$ wget https://raw.githubusercontent.com/starcoinorg/starcoin/master/scripts/import_block.sh
```

给脚本执行权限，并开始下载主网区块数据到`/data/starcoin/main`目录并导入：

```bash
$ chmod 755 import_block.sh
$ ./import_block.sh main /data/starcoin/main
```

> 小提示：
>
> * main：main 是主网，可以替换为测试网，如 barnard, proxima, halley；
> * /data/starcoin/main：自定义的区块数据目录；

![import db file](<../../.gitbook/assets/image (12).png>)

![](<../../.gitbook/assets/image (36).png>)

#### 2.3 运行新节点 <a href="#ytln8" id="ytln8"></a>

脚本运行完成后，就可以运行新节点了。

下面使用 Docker 方式运行新节点，如果是 Windows 可以参考之前文章中的运行命令。

```bash
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



