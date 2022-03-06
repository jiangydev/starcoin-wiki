# 在 Windows 上运行节点

安装环境：Windows 10



## 一、下载最新版本的软件 <a href="#yyl7b" id="yyl7b"></a>

下载地址：[https://github.com/starcoinorg/starcoin/releases/latest](https://github.com/starcoinorg/starcoin/releases/latest)

![](<../../../.gitbook/assets/image (10).png>)

## 二、新建目录及解压压缩文件 <a href="#uun7r" id="uun7r"></a>

新建的目录不要出现中文、空格以及特殊字符。

另外准备个数据目录；

完成的结果如下：

![](<../../../.gitbook/assets/image (1) (8).png>)

## 三、运行节点 <a href="#iyrgp" id="iyrgp"></a>

### 3.1 查看命令帮助 <a href="#zgikp" id="zgikp"></a>

进入解压后的"starcoin-artifacts"目录，在地址栏中输入 cmd 并回车（目录下要有 starcoin.exe），并在命令提示符下输入如下命令：

> 小提示：
>
> * 如果运行命令后，有弹窗提示权限，请允许；
> * 教程后面进入 cmd 窗口，若未做特殊说明，都是在解压后的目录中进入；

```
starcoin.exe -h
```

该命令是查看帮助，第一行会返回软件版本，命令截图如下：

![](<../../../.gitbook/assets/image (2) (3).png>)

### 3.2 运行节点 <a href="#dvjh0" id="dvjh0"></a>

运行完下面的命令，该窗口不要关，需执行其他命令，请重开 cmd 窗口。

> 小提示：
>
> * 每行结尾的 ^：表示命令未结束，需要换行；
> * \--net main：启动的网络，主网为 main，测试网为 barnard；
> * \--miner-thread：挖矿线程数，可适当调节，若无需挖矿，可设置为 0；
> * \--node-name：节点名称，随意；
> * \--data-dir：数据存放目录，这里 C:\starcoin\data 是第二步中创建的 data 目录，可根据情况修改；
> * \--stratum-address 0.0.0.0 --stratum-port 9880：启动矿池功能；

```powershell
starcoin.exe --net main ^
    --disable-metrics true ^
    --miner-thread 0 ^
    --node-name starcoin-main ^
    --data-dir C:\starcoin\data ^
    --logger-disable-file true ^
    --stratum-address 0.0.0.0 --stratum-port 9880
```

截图如下：

![](<../../../.gitbook/assets/image (3) (5).png>)

需要注意的：

* 重点1
  * Http rpc address: Some(http://0.0.0.0:9850)
  * TCP rpc address: Some(tcp://0.0.0.0:9860)
  * Websocket rpc address: Some(ws://0.0.0.0:9870)
* 重点2（<mark style="color:orange;">这个很重要！！！后面会用来连接控制台、导出私钥等，所以一定要关注\~</mark>）
  * Ipc file path: `\\.\pipe\starcoin\main\starcoin.ipc`
* 重点3（数据目录，迁移节点可以复制用来，减少区块同步耗时。）
  * Final data-dir is : `C:\starcoin\data\main`

## 四、导出账号及私钥 <a href="#h65dh" id="h65dh"></a>

### 4.1 连接Starcoin控制台 <a href="#b40f1d7ab7ce8a042c7fc157db40a639" id="b40f1d7ab7ce8a042c7fc157db40a639"></a>

前提：节点运行中

连接控制台，看到最后返回 `starcoin%` 就说明成功到控制台了：

```
starcoin.exe -c \\.\pipe\starcoin\main\starcoin.ipc console
```

![](<../../../.gitbook/assets/image (4) (7).png>)

> 小提示：
>
> * `\\.\pipe\starcoin\main\starcoin.ipc`：这个 ipc 文件，就是启动节点时返回的；

### 4.2 查看账号并导出私钥 <a href="#603e8a317e1ae66c0f224cb12c9f199a" id="603e8a317e1ae66c0f224cb12c9f199a"></a>

前提：连接Starcoin控制台

查看默认账号：

```
account default
```

导出默认账号的私钥：

```
account export 0x9cd5d558e01d33f1ec0b97b75bb1d34f
```

如下图所示，导出了 account 和 private key（私钥），私钥一定要保存！！！

![](<../../../.gitbook/assets/image (5) (2).png>)

### 3.3 查看账号余额 <a href="#e024ecc0a47d5aa9b300089b683cab90" id="e024ecc0a47d5aa9b300089b683cab90"></a>

这里只给下命令，如果返回了 balances.STC 说明有出块，精度 9 位；

```
account show 0x9cd5d558e01d33f1ec0b97b75bb1d34f
```

![](<../../../.gitbook/assets/image (6).png>)

### 3.4 编码 Receipt Identifier 地址 <a href="#vtr0r" id="vtr0r"></a>

```
account  receipt-identifier 0x8B79FDF7bd004b72Ea4bD83289429455
```

![](<../../../.gitbook/assets/image (7) (1).png>)

### 3.5 退出控制台 <a href="#0ddf58a8254b8d35123044cf7d67b617" id="0ddf58a8254b8d35123044cf7d67b617"></a>

看截图：

```
$ exit
```

![
](<../../../.gitbook/assets/image (8) (1).png>)

## 五、区块浏览器 <a href="#aac9c43b1ce7ef0cbe1c4bc3e9b87f22" id="aac9c43b1ce7ef0cbe1c4bc3e9b87f22"></a>

地址：[https://stcscan.io](https://stcscan.io)

![](<../../../.gitbook/assets/image (9) (1).png>)



