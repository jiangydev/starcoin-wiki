# Run a node with Docker

## Environment <a href="#rnxwk" id="rnxwk"></a>

Ubuntu/CentOS and other systems (including Windows 10 Professional Edition, similar commands) with Docker installed, and docker is running.

## Run a node <a href="#cac404006338d05dc87f6ab330ef4fbe" id="cac404006338d05dc87f6ab330ef4fbe"></a>

Run the following command to run the node:

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

> Hint:
>
> * If you don't need to start the mining pool function, you can remove -p 9880:9880, and the last parameter --stratum-address 0.0.0.0 --stratum-port 9880;
> * \-n main: Specify the main network main, the test network can be changed to barnard;
> * \--miner-thread 0: The number of mining threads, which can be adjusted by yourself;

Check the running status of the node:

```
$ sudo docker ps -a
```

![](<../../../.gitbook/assets/image (27).png>)

## Export account and private key <a href="#ea06b35261c8e025ea9791e1ebea8e9a" id="ea06b35261c8e025ea9791e1ebea8e9a"></a>

### Connect to the Starcoin console <a href="#b40f1d7ab7ce8a042c7fc157db40a639" id="b40f1d7ab7ce8a042c7fc157db40a639"></a>

Enter the server and run this command:

```
$ sudo docker exec -it starcoin-main /bin/bash
```

Connect to the console and see that `starcoin%` is returned at the end, which means that you have successfully reached the console:

```shell
/starcoin/starcoin --connect /data/starcoin/main/starcoin.ipc console
```

![](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2F6Vef1eE79zMfK1VGuffy%2Fimage%20\(1\).png?alt=media\&token=7cc03ef8-96b1-465e-b854-a27b6e8cfc6e)

### View account and export private key <a href="#603e8a317e1ae66c0f224cb12c9f199a" id="603e8a317e1ae66c0f224cb12c9f199a"></a>

Prerequisite: Connecting the Starcoin console.

View the default account:

```
account default
```

Export the private key of the default account:

```
account export 0x8b79fdf7bd004b72ea4bd83289429455
```

As shown in the figure below, the account and private key are exported, and <mark style="color:red;">the private key must be saved! ! !</mark>

![](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2FyL68eEFXkVX2JdZ6qwGk%2Fimage.png?alt=media\&token=a3d1d60a-ebda-4150-9a26-e94b7585ad7d)

### View account public key and balance <a href="#e024ecc0a47d5aa9b300089b683cab90" id="e024ecc0a47d5aa9b300089b683cab90"></a>

Command:

```
account show 0x8b79fdf7bd004b72ea4bd83289429455
```

![](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2FBl9b8lV1SM1TkmPT7nts%2Fimage.png?alt=media\&token=17ec306d-d1b2-440b-8fc5-17b25ded43f1)

Field explanation:

* public\_key: Account public key;
* balances: Account balance. 0x000000000000000000000000000001::STC::STC STC balance, the precision is 9 digits, the balance will increase after the block is produced.

### Exit the console <a href="#0ddf58a8254b8d35123044cf7d67b617" id="0ddf58a8254b8d35123044cf7d67b617"></a>

Command:

```
$ exit
```

## Block explorer <a href="#aac9c43b1ce7ef0cbe1c4bc3e9b87f22" id="aac9c43b1ce7ef0cbe1c4bc3e9b87f22"></a>

Website: [https://stcscan.io](https://stcscan.io)

![](<../../../.gitbook/assets/image (6).png>)

