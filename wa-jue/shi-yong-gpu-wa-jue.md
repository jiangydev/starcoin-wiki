# 使用 GPU 挖掘

本教程目前只有 Windows 版，和上一篇 CPU 分开的，可以一起跑；

目前支持 STC 的矿池如下：

|      |                 可乐                 |                             大象                             |                    币印                   |                       ViaBTC                       |
| :--: | :--------------------------------: | :--------------------------------------------------------: | :-------------------------------------: | :------------------------------------------------: |
|      |    [点击前往](https://www.bixin.im)    | [点击前往](https://www.dxpool.com/register/phone?refer=542717) |      [点击前往](https://www.poolin.com)     | [点击前往](https://www.viabtc.com/signup?refer=693440) |
| 矿池地址 | <p>ccc.zxxx123.com</p><p>端口：22</p> |           <p>stc.ss.dxpool.net</p><p>端口：9977</p>           |  <p>stc.ss.poolin.com</p><p>端口：443</p>  |         <p>stc.viabtc.com</p><p>端口：3005</p>        |
| 初始难度 |                7000                |                            10000                           | <p>8192</p><p>可调节，例如密码处填：fixed=3000</p> |                  可调节，例如密码处填：d=3000                 |

## 一、Windows用户 <a href="#zalot" id="zalot"></a>

### 1.1 下载软件 <a href="#bwkcd" id="bwkcd"></a>

N卡用户下载地址：[https://github.com/xmrig/xmrig-nvidia/releases/latest](https://github.com/xmrig/xmrig-nvidia/releases/latest)

A卡用户下载地址：[https://github.com/xmrig/xmrig-amd/releases/latest](https://github.com/xmrig/xmrig-amd/releases/latest)

选择和下载 win64 版本的 XMRig 程序。

![](<../.gitbook/assets/image (16).png>)

### 1.2 修改脚本 <a href="#otcrt" id="otcrt"></a>

下载 XMRig 程序后，解压并右键“编辑” `start.cmd` 文件。

![](<../.gitbook/assets/image (28).png>)

修改 start.cmd 文件的内容：

```powershell
@echo off
xmrig-nvidia.exe --donate-level 1 -a cn/r -o ccc.zxxx123.com:22 -u an.1 -p x -k --user-agent Ibctminer/1.0.0
pause
```

修改后的结果如下图所示：

![](<../.gitbook/assets/image (23).png>)

### 1.3 双击运行 <a href="#occsi" id="occsi"></a>

![](<../.gitbook/assets/image (3) (3).png>)



