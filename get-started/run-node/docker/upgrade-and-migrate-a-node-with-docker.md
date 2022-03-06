# Upgrade & Migrate a node with Docker



## Preparation <a href="#5634b8fb5e7251b57ac54e0571831eeb" id="5634b8fb5e7251b57ac54e0571831eeb"></a>

<mark style="color:red;">The private key of the original node must be exported first! ! !</mark>



Prepare the private key for importing the node account. Private key export tutorial, [click here](../windows/run-a-node-on-windows.md#h65dh).

## Stop the original node <a href="#1ba854af870aaec04ff07f5ba28884d2" id="1ba854af870aaec04ff07f5ba28884d2"></a>

<mark style="color:orange;">If you are migrating a node, you can skip this step.</mark>



Stop and delete the original node:

```
$ docker rm -f starcoin-main
```

Delete the ipc file of the original node:

```
$ rm -rf /data/starcoin/main/starcoin.ipc
```

Update the latest docker image:

```
$ docker pull starcoin/starcoin
```

## Start a new node <a href="#86ef772c2a90b5fc349fa3551d81db9a" id="86ef772c2a90b5fc349fa3551d81db9a"></a>

Unzip the downloaded compressed package to overwrite the file of the previous version.

Note:

* If you don't need to start the mining pool, you can delete the last parameter: --stratum-address 0.0.0.0 --stratum-port 9880;
* \--net main: Specify the main network, the test network can write barnard;

```powershell
# run a new node
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

# View the node running status
$ docker ps -a
```



## Import the private key and set it as the default account <a href="#bbe435aa638eed8bca80dc643170856e" id="bbe435aa638eed8bca80dc643170856e"></a>

Connect to the console (premise: the node is running):

```powershell
$ docker exec -it starcoin-main /bin/bash

> /starcoin/starcoin --connect /data/starcoin/main/starcoin.ipc console

% account default
```

Check the default account on the new node:

```
account default
```



<mark style="color:red;">If the account is your own, it is over. If the account is wrong, please import the private key and set it as the default account.</mark>

Import private key：

```
% account import -i your_private_key
```

Set as default account:

```
% account default your_account
```

