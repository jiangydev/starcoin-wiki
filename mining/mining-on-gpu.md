# Mining on GPU

This tutorial is currently only available for Windows, which is separate from the previous CPU and can be run together.

The mining pools currently supporting STC are as follows:

|                    |                Kelepool               |                     Dxpool                     |                                    Poolin                                   |                         ViaBTC                        |
| :----------------: | :-----------------------------------: | :--------------------------------------------: | :-------------------------------------------------------------------------: | :---------------------------------------------------: |
|                    |     [Click](https://www.bixin.im)     | [Click](https://www.dxpool.com/register/phone) |                       [Click](https://www.poolin.com)                       |         [Click](https://www.viabtc.com/signup)        |
|    Pool Address    | <p>ccc.zxxx123.com</p><p>port: 22</p> |   <p>stc.ss.dxpool.net</p><p>port: 9977 </p>   |                   <p>stc.ss.poolin.com</p><p>port: 443</p>                  |         <p>stc.viabtc.com</p><p>port: 3005</p>        |
| Initial Difficulty |                  7000                 |                      10000                     | <p>8192</p><p>Adjustable, for example, fill in the password: fixed=3000</p> | Adjustable, for example, fill in the password: d=3000 |

## For Windows User

### Download XMRig <a href="#bwkcd" id="bwkcd"></a>

* Nvidia: [https://github.com/xmrig/xmrig-nvidia/releases/latest](https://github.com/xmrig/xmrig-nvidia/releases/latest)​
* Amd: [https://github.com/xmrig/xmrig-amd/releases/latest](https://github.com/xmrig/xmrig-amd/releases/latest)​

Select and download the win64 version of the XMRig program.

![](<../.gitbook/assets/image (2) (2).png>)

### Modify script <a href="#otcrt" id="otcrt"></a>

After downloading the XMRig program, unzip and right-click to "edit" the `start.cmd` file.

![](<../.gitbook/assets/image (3) (2).png>)

Contents of `start.cmd` file:

```powershell
@echo off
xmrig-nvidia.exe --donate-level 1 -a cn/r -o ccc.zxxx123.com:22 -u an.1 -p x -k --user-agent Ibctminer/1.0.0
pause
```

The modified result is shown in the following figure:

![](<../.gitbook/assets/image (5) (3).png>)

### Double-click to run <a href="#occsi" id="occsi"></a>

![](<../.gitbook/assets/image (3) (1).png>)

​

​
