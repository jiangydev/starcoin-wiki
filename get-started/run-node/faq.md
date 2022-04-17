# FAQ

## What happened to the node synchronization process? How long does it take to sync?

Connect to the node console and execute the following command:

Not sure how to enter the console? You can refer to the following tutorials:

* How to enter the console of the node with Docker, [click here](docker/run-a-node-with-docker.md#b40f1d7ab7ce8a042c7fc157db40a639)
* How to enter the console of the node on Windows, [click here](windows/run-a-node-on-windows.md#b40f1d7ab7ce8a042c7fc157db40a639)

```
node sync status
```

Execute the above command to see the current block height:

![node sync status](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2Fql8fImL0dIOSyd9SzyrJ%2Fimage.png?alt=media\&token=f562c4c7-d7e5-465e-b43c-21d5d56effbe)

Sliding to the last line, there are two results:

* Result 1: If the content in the screenshot below is returned, it means that during synchronization, the synchronization is completed when `chain_status.head.number` and `state.Synchronizing.target.number` are the same.

![node synchronizing](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2FxdGmgzjipw7iHm9tLAkr%2Fimage.png?alt=media\&token=08733ec7-675f-4c01-8595-20e873b821bc)

* Result 2: Synchronization complete

![node Synchronized](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2Fbo9ON0OPfRgW37bDLBrl%2Fimage.png?alt=media\&token=f624369f-e1c4-4ab1-8a18-03dbc9c6956a)



Answer: Execute the above command to view the synchronization progress. The synchronization time can be estimated by yourself according to the command execution result.

## How to speed up the synchronization of block data? <a href="#jz3hs" id="jz3hs"></a>

### Solution

Download the mainnet block data of other nodes to the new node, and start the node with the downloaded block data.

### Steps

#### 2.1 Download the Starcoin Node Data Export Tool

Download the `starcoin_db_exporter` node data export tool, this is a must, and the synchronization script needs to be used.

```shell
$ wget https://github.com/starcoinorg/starcoin/releases/download/v1.9.1/starcoin-ubuntu-18.04.zip
$ unzip starcoin-ubuntu-18.04.zip
$ cp starcoin-artifacts/starcoin_db_exporter starcoin_db_exporter
```

#### Download block data <a href="#hkw1t" id="hkw1t"></a>

First download the official synchronization script tool:

```shell
$ wget https://raw.githubusercontent.com/starcoinorg/starcoin/master/scripts/import_block.sh
```

Grant the script execution permission and start downloading the mainnet block data to the /data/starcoin/main directory and import:

```bash
$ chmod 755 import_block.sh
$ ./import_block.sh main /data/starcoin/main
```

> Hint:
>
> * main: main is the main network. You can replace it with testnet, such as: barnard, proxima, halley.
> * /data/starcoin/main: Custom block data directory;

![import db file](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2FEHylUW6rYIR4Hc5sqkX7%2Fimage.png?alt=media\&token=f12fb8ac-c80a-44d0-bf28-213f63a889c6)

![](https://3786882916-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdXzzGpY0VSaA01mucBHD%2Fuploads%2FwDO8SIf3QIw3qCDPRKQT%2Fimage.png?alt=media\&token=8d43d949-bef4-4e11-af17-13d2aeba5154)

#### Run a new node <a href="#ytln8" id="ytln8"></a>

Once the script has finished running, it's time to run the new node.

Let's use Docker to run the new node. If it is Windows, you can refer to the running command in the previous article.

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

