- 参考网址：https://www.cnblogs.com/Reskorey/p/10490584.html
- 区块数据目录：/data/btc/data
- 配置文件目录：/data/btc/bitcoin.conf

## 准备

服务器：硬盘300G+（2019年6月26日，区块数据占据250G）

节点下载地址：https://bitcoincore.org/bin/bitcoin-core-0.18.0/，选择：bitcoin-0.18.0-x86_64-linux-gnu.tar.gz （此版本无需编译，解压即用）

1. 解压BTC节点包
`tar -xvf bitcoin-0.18.0-x86_64-linux-gnu.tar.gz`
2. 新建区块数据存储目录data
3. 新建配置文件bitcoin.conf
4. 切换root用户，启动节点：
> 进入/data/btc/bitcoin-0.18.0/bin, 执行命令：
`./bitcoind -conf=/data/btc/bitcoin.conf -reindex `
> 注意：-reindex命令是对已经同步过区块数据，但未索引的节点执行。我在这里一开始不知道调用getRawTransactions需要对区块数据进行索引，所以用的是reindex命令，一旦索引以后，就可以调用txindex命令即可。或者从头开始同步时，在配置文件设置txindex = 1即可。参考USDT节点搭建中的bitconfig文件。


5. 测试RPC

进入/data/btc/bitcoin-0.18.0/bin, 连接节点命令：
`./bitcoin-cli -rpcconnect=127.0.0.1 -rpcuser=bizzan -rpcpassword=8897364ddefs -rpcport=8333 getblockchaininfo`

```
./omnicored -conf=/data/usdt/bitcoin.conf
./bitcoin-cli -rpcconnect=127.0.0.1 -rpcuser=bizzan -rpcpassword=8897364ddefs -rpcport=8333 getblockchaininfo
./bitcoin-cli -rpcconnect=127.0.0.1 -rpcuser=bizzan -rpcpassword=8897364ddefs -rpcport=8333 getblockhash
./omnicore-cli -rpcconnect=127.0.0.1 -rpcuser=bizzan -rpcpassword=8897364ddefs -rpcport=8333 getblockchaininfo
```
