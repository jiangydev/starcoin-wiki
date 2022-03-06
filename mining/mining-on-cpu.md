# Mining on CPU

This tutorial is divided into Windows and Docker, Docker is also suitable for running in the server.

The mining pools currently supporting STC are as follows:

|                    |                Kelepool               |                     Dxpool                     |                                    Poolin                                   |                         ViaBTC                        |
| :----------------: | :-----------------------------------: | :--------------------------------------------: | :-------------------------------------------------------------------------: | :---------------------------------------------------: |
|                    |     [Click](https://www.bixin.im)     | [Click](https://www.dxpool.com/register/phone) |                       [Click](https://www.poolin.com)                       |         [Click](https://www.viabtc.com/signup)        |
|    Pool Address    | <p>ccc.zxxx123.com</p><p>port: 22</p> |   <p>stc.ss.dxpool.net</p><p>port: 9977 </p>   |                   <p>stc.ss.poolin.com</p><p>port: 443</p>                  |         <p>stc.viabtc.com</p><p>port: 3005</p>        |
| Initial Difficulty |                  7000                 |                      10000                     | <p>8192</p><p>Adjustable, for example, fill in the password: fixed=3000</p> | Adjustable, for example, fill in the password: d=3000 |

## For Windows User <a href="#bwkcd" id="bwkcd"></a>

### Download XMRig

Select and download the win64 version of the XMRig program.

![](<../.gitbook/assets/image (10) (1).png>)

### Modify script <a href="#otcrt" id="otcrt"></a>

After downloading the XMRig program, unzip and right-click to "edit" the `start.cmd` file.

![](<../.gitbook/assets/image (11) (1).png>)

Modify the content of the `start.cmd` file:

```powershell
@echo off
xmrig.exe --donate-level 1 -a cn/r -o ccc.zxxx123.com:22 -u an.1 -p x -k --user-agent Ibctminer/1.0.0
pause
```

The modified result is shown in the following figure:

![](<../.gitbook/assets/image (12) (1).png>)

### Double-click to run <a href="#l7yut" id="l7yut"></a>

double-click the `start.cmd` file.

![](<../.gitbook/assets/image (3) (1) (1).png>)

## For Docker User <a href="#bucys" id="bucys"></a>

```bash
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

Command Explanation:

* `-d`: run the container in the background;
* `--name starcoin-xmr`: specify the container name;
* `--restart=always`: If the container exits unexpectedly, it will automatically restart;
* `-o ccc.zxxx123.com:22`: mining pool address, such as cola ccc.zxxx123.com:22;
* `-u an.1`: \<sub-account name>.\<number>, such as an.1;
* `-p x` : password, just fill `x`;
* `-a cn/r`: algorithm, cn/r, do not change, only use this;
* `--donate-level`: dev fee;
* `--cpu-max-threads-hint 90`: CPU usage ratio;

![](<../.gitbook/assets/image (4) (1) (1).png>)

## Performance Optimization

### Enable Huge Pages

According to the official documentation of XMRig, enabling Huge Pages can increase the computing power by 20%\~30%. The tutorial is as follows.

#### For Windows

**Step 1:**

`Windows Server 2003 Resource Kit Tools` must be installed first (provides SeLockMemoryPrivilege function)

Download link: [https://wwa.lanzoui.com/b0f8hmm6b](https://wwa.lanzoui.com/b0f8hmm6b) password: star

![](<../.gitbook/assets/image (5) (1).png>)

After downloading, unzip it, and install rktools as an administrator. If it prompts an incompatible popup, you can close it and ignore it.



**Step 2:**

Open a CMD window with administrator:

![](<../.gitbook/assets/image (6) (1).png>)

Enter the following command in the CMD window:

```powershell
ntrights -u "这里换成自己的Windows账户名" +r SeLockMemoryPrivilege
```

{% hint style="info" %}
Note:

Press and hold \[Ctrl+Alt+Delete] to open the task manager. You can see your account name in the task manager. The screenshot is as follows.
{% endhint %}

![](<../.gitbook/assets/image (7) (1).png>)

![](<../.gitbook/assets/image (8) (2).png>)

The prompt "successful" is successful, and then you must restart the computer! ! !



**Step 3:**

After restarting the computer, run the script again to see the effect.

![](<../.gitbook/assets/image (9) (1).png>)

#### For Linux <a href="#nblgs" id="nblgs"></a>

Temporarily enable:

```bash
sudo sysctl -w vm.nr_hugepages=1280
```

Persistence is enabled (it also takes effect after restart):

```bash
sudo bash -c "echo vm.nr_hugepages=1280 >> /etc/sysctl.conf"
```

### Modify the CPU thread usage occupancy ratio

Modify file: `start.cmd`

`--cpu-max-threads-hint 80`: The ratio of the maximum number of threads automatically configured.

![](<../.gitbook/assets/image (25).png>)

### Modify the number of threads <a href="#vjrvf" id="vjrvf"></a>

Modify file: `start.cmd`

`-t 4`: specify 4 threads; don't tune too much, it may backfire;

![](<../.gitbook/assets/image (1) (2).png>)

Check the number of threads in effect:

![](<../.gitbook/assets/image (12) (2).png>)
