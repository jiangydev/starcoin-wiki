# 使用 CPU 挖掘

本教程分为 Windows 和 Docker 版，Docker 也适合服务器中运行；

目前支持 STC 的矿池如下：

|      |                 可乐                 |                             大象                             |                    币印                   |                       ViaBTC                       |
| :--: | :--------------------------------: | :--------------------------------------------------------: | :-------------------------------------: | :------------------------------------------------: |
|      |    [点击前往](https://www.bixin.im)    | [点击前往](https://www.dxpool.com/register/phone?refer=542717) |      [点击前往](https://www.poolin.com)     | [点击前往](https://www.viabtc.com/signup?refer=693440) |
| 矿池地址 | <p>ccc.zxxx123.com</p><p>端口：22</p> |           <p>stc.ss.dxpool.net</p><p>端口：9977</p>           |  <p>stc.ss.poolin.com</p><p>端口：443</p>  |         <p>stc.viabtc.com</p><p>端口：3005</p>        |
| 初始难度 |                7000                |                            10000                           | <p>8192</p><p>可调节，例如密码处填：fixed=3000</p> |                  可调节，例如密码处填：d=3000                 |

## 一、Windows用户 <a href="#zalot" id="zalot"></a>

### 1.1 下载 XMRig <a href="#bwkcd" id="bwkcd"></a>

下载地址：[https://github.com/xmrig/xmrig/releases/latest](https://github.com/xmrig/xmrig/releases/latest)

选择和下载 win64 版本的 XMRig 程序。

![](<../.gitbook/assets/image (5).png>)

### 1.2 修改脚本 <a href="#otcrt" id="otcrt"></a>

下载 XMRig 程序后，解压并右键“编辑” `start.cmd` 文件。

![](<../.gitbook/assets/image (30).png>)

修改 start.cmd 文件的内容：

```powershell
@echo off
xmrig.exe --donate-level 1 -a cn/r -o ccc.zxxx123.com:22 -u an.1 -p x -k --user-agent Ibctminer/1.0.0
pause
```

修改后的结果如下图所示：

![](<../.gitbook/assets/image (21).png>)

### 1.3 双击运行 <a href="#l7yut" id="l7yut"></a>

![start](<../.gitbook/assets/image (3) (2).png>)

## 二、Docker 用户 <a href="#bucys" id="bucys"></a>

```
sudo docker run -d -it \
    --name starcoin-xmr \
    --restart=always \
    z0re/xmrig-stc \
    -o ccc.zxxx123.com:22 \
    -u an.1 \
    -p x \
    -a cn/r \
    --donate-level 1 \
    --cpu-max-threads-hint 90
```

命令解释：

* \-d：容器在后台运行；
* \--name starcoin-xmr：指定容器名；
* \--restart=always：容器如果意外退出，将自动重启；
* \-o ccc.zxxx123.com:22：矿池地址，例如可乐 ccc.zxxx123.com:22；
* \-u an.1：子账户名.数字，例如我的 an.1；
* \-p：写 x 就行；
* \-a：算法，cn/r，不要换，只能用这个；
* \--donate-level：dev fee；
* \--cpu-max-threads-hint 90：CPU占用，可以看自身情况调节，例如这里 90；

截图展示：

![](<../.gitbook/assets/image (4) (6).png>)

## 三、性能优化 <a href="#z3hen" id="z3hen"></a>

### 3.1 开启 Huge Pages <a href="#xfrdy" id="xfrdy"></a>

感谢社区小伙伴【余温】提供该优化点，并提供相关的参考文档；

据 XMRig 官方文档说明，开启 Huge Pages 能提升 20%\~30% 的算力，教程如下。

#### 3.1.1 Windows（各版本均适用） <a href="#cc8ff" id="cc8ff"></a>

**步骤一：**

必须先安装 Windows Server 2003 Resource Kit Tools（提供SeLockMemoryPrivilege功能）

**下载地址**：[https://wwa.lanzoui.com/b0f8hmm6b](https://wwa.lanzoui.com/b0f8hmm6b) 密码: star

![](<../.gitbook/assets/image (5) (6).png>)

下载后解压，以管理员身份安装 rktools，若提示不兼容的弹框，可以关闭，不予理会。

**步骤二：**

安装完成后，使用管理员打开CMD窗口：

![](<../.gitbook/assets/image (6) (2).png>)

在 CMD 窗口输入如下命令：

```
ntrights -u "这里换成自己的Windows账户名" +r SeLockMemoryPrivilege
```

小提示：**如何查看自己的账户名？**

按住【Ctrl键+Alt键+Delete键】打开任务管理器，任务管理器中可以看到自己的账户名，截图如下。

![](<../.gitbook/assets/image (7) (3).png>)

命令截图如下：

![](<../.gitbook/assets/image (8).png>)

提示“successful”就成功了，之后一定要重启电脑！！！

**步骤三：**

重启电脑后，再运行脚本看效果。

![](<../.gitbook/assets/image (9) (2).png>)

#### 3.1.2 Linux <a href="#nblgs" id="nblgs"></a>

临时开启：

```
sudo sysctl -w vm.nr_hugepages=1280
```

持久化开启（重启后也生效）：

```
sudo bash -c "echo vm.nr_hugepages=1280 >> /etc/sysctl.conf"
```

### 3.2 修改 CPU 线程占用比 <a href="#ph7bf" id="ph7bf"></a>

若对其他软件有影响，可修改自动配置的线程数占比。

修改文件：`start.cmd`

`--cpu-max-threads-hint 80`：自动配置的最大线程数占比。

![](<../.gitbook/assets/image (4).png>)

### 3.3 指定线程数 <a href="#vjrvf" id="vjrvf"></a>

修改文件： `start.cmd`

`-t 4`：指定 4 个线程；不要调的太大，可能会适得其反；

![](<../.gitbook/assets/image (20).png>)

查看生效的线程数：

![](<../.gitbook/assets/image (12) (1).png>)
