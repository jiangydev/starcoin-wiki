# GoldShell STC Box

### 0x1 STC, PoolCola introduction <a href="#womnh" id="womnh"></a>

#### Starcoin(STC) <a href="#krd24" id="krd24"></a>

Starcoin is a decentralized hierarchical smart contract network. It aims to provide a secured digital asset and a decentralized financial operation platform, so that the blockchain can be applied in more fields with a lower threshold.

* algorithm: CryptoNight-R
* Total supply: 3,185,136,000
* Current liquidity: 175,025,861
* Starcoin official website: [https://starcoin.org/](https://starcoin.org)
* Block explorer: [https://stcscan.io/](https://stcscan.io)

#### KelePool <a href="#b4u8j" id="b4u8j"></a>

KelePool is built into Bixin Wallet and is the earliest platform to support mining Starcoin (STC). It automatically sends money to Bixin Wallet at 9:30 (UTC+8) every day, and the transfer fee is as low as 0.01 STC.

At the same time, PoolCola has a low rejection rate and high income, and has a good reputation in the Starcoin's community.

#### STC-BOX <a href="#feg8n" id="feg8n"></a>

Hashrate: 13.9Kh/s

Power: 61W

Shopping：

* Cyber Rare：[https://www.cyberrare.io/](https://www.cyberrare.io)
* DxShop：[https://global.dxpool.io/product/st-box/](https://global.dxpool.io/product/st-box/)

### 0x2 Mining pool setup steps <a href="#dvtue" id="dvtue"></a>

#### 2.1 Install Bixin Wallet and register <a href="#jb9ka" id="jb9ka"></a>

download link: [https://www.bixin.com](https://www.bixin.com)

![](../.gitbook/assets/wallet\_download.png) ![](../.gitbook/assets/wallet\_register.png)

#### 2.2 Enter KelePool <a href="#sh14y" id="sh14y"></a>

![](../.gitbook/assets/pool\_enter.png) ![](../.gitbook/assets/pool\_switch\_STC.png)

#### 2.3 Create sub-account <a href="#bknc2" id="bknc2"></a>

![](../.gitbook/assets/pool\_create\_click.png) ![](../.gitbook/assets/pool\_create\_subaccount.png)

#### 2.4 Set up payment address <a href="#acjdv" id="acjdv"></a>

The payment address is the Bixin Wallet address by default, and modification is not supported, and the proceeds will be automatically transferred to Bixin Wallet.

### 0x3 STC-BOX Setup steps <a href="#hzrmv" id="hzrmv"></a>

#### 3.1 Box Power <a href="#rhs0c" id="rhs0c"></a>

To prepare a PSU, at least one 6P interface is required.

Reminder:

If you use a one-to-one power supply or a power supply without a switch, you need to use the power cord to short circuit the 24P interface, so that the power supply can start to work, as shown in the figure below.

If the power supply does not work after the stc-box is plugged in, try to short circuit again.

![](../.gitbook/assets/box\_psu\_power.png)

After the power is connected, the normal state: the green light is always on after the red and green lights are flashing.

![](../.gitbook/assets/box\_psu.png)

#### 3.2 Access network cable <a href="#cmh0y" id="cmh0y"></a>

![](../.gitbook/assets/box\_net.png)

#### 3.3 Configure mining pool <a href="#por5i" id="por5i"></a>

**1) Enter the console**

Enter in the browser address bar: [https://find.goldshell.com](https://find.goldshell.com)

Reminder:

* Google Chrome or Microsoft edge browser is recommended;
* The miner must be on the same LAN with your browser;
* The language can be switched in the upper right corner of the page;

![](../.gitbook/assets/box\_find.png)

**2) Unlock the console**

Initial password: 123456789

![](../.gitbook/assets/box\_unlock\_1.png)

![](../.gitbook/assets/box\_unlock\_2.png)

**3) Add pool addresses**

* **Address**：ssl.ccc.zxxx123.com:22

{% hint style="info" %}
* TLS supported：ccc.zxxx123.com:22
* kelepool TG group: [https://t.me/kelepoolcom](https://t.me/kelepoolcom)
* Note: If you want to connect the pool with TLS/SSL, you have to upgrade the STC-BOX version to 2.1.6.
{% endhint %}

Username：your sub-account

Password: 123

![](../.gitbook/assets/box\_set\_pool.png)

**4) Check the configuration**

After configuring the correct address, the icon is green.

![](../.gitbook/assets/box\_set\_done.png)

#### 3.4 View info <a href="#wm7kg" id="wm7kg"></a>

![](../.gitbook/assets/box\_info.png)

### 0x4 Transfer and more settings <a href="#xllw5" id="xllw5"></a>

#### 4.1 View earnings <a href="#lilfj" id="lilfj"></a>

You can view the estimated earnings of the day and yesterday's earnings.

![](../.gitbook/assets/pool\_reward.png)

#### 4.2 Set hashrate alarm <a href="#e2rgc" id="e2rgc"></a>

It is recommended to set up "Hash Power Alarm", and you can get timely reminders when STC-BOX is offline.

![](../.gitbook/assets/pool\_alarm.png)

#### 4.3 Withdraw or transfer <a href="#mklg2" id="mklg2"></a>

Bixin Wallet supports address (starting with 0x) and Receipt Identifier (starting with stc).

![](../.gitbook/assets/wallet\_withdraw.png) ![](../.gitbook/assets/wallet\_transfer.png)

### 0x5 Trade <a href="#j41nl" id="j41nl"></a>

You can buy or sell STC in Bixin Wallet.

In addition to STC, the Exchange also supports transactions in other mainstream currencies.

![](../.gitbook/assets/wallet\_trade.png) ![](../.gitbook/assets/wallet\_trade\_page.png)

### 0x6 FAQ <a href="#ncknj" id="ncknj"></a>

#### 6.1 Firmware Upgrade <a href="#c8rpg" id="c8rpg"></a>

The upgrade steps are as follows.

**1) Check stc-box firmware version**

Enter the miner page, and the current firmware version "2.1.4" is displayed on the right.

![](<../.gitbook/assets/image (2).png>)

**2) Download the latest firmware**

Firmware address: [https://github.com/goldshellminer/firmware](https://github.com/goldshellminer/firmware)

![](<../.gitbook/assets/image (1) (1).png>)

**3) Update firmware**

![](<../.gitbook/assets/image (2) (3).png>)

#### 6.2 Reset the miner to the factory setting(Not recommended) <a href="#nmu6m" id="nmu6m"></a>

{% hint style="info" %}
**Note:** the reset operation may cause some problems.
{% endhint %}

**1) Method 1: physical reset**

For scenarios:

1. The miner cannot be found at find.goldshell.com;
2. Miner setting error, such as closing DHCP, resulting in failure to find miner;

Press and hold on the reset key for about 10s, as shown in the following figure:

![](../.gitbook/assets/box\_reset.png)

**2) Method 2: reset on the console**

![](<../.gitbook/assets/image (3) (3).png>)

****

****
