
# filepp-net 
 filepp-net是由filepp社区维护的lotus独立网络，免费提供给社区使用。主要修改了以下功能：
 - 支持2K、8M、512M、32G、64G扇区
 - WaitSeed时间为60 Epoch
 - 最小爆块算力为2K
 
## 加入filepp-net
加入filepp-net，需要使用filepp社区提供的修改过后的lotus代码进行编译
```bash
git clone https://github.com/filepp/lotus
cd lotus 
git checkout net/private-v1.4.1
RUSTFLAGS="-C target-cpu=native -g" FFI_BUILD_FROM_SOURCE=1 make debug 
sudo make install
```

导入加速CDN
```
export IPFS_GATEWAY="https://proof-parameters.s3.cn-south-1.jdcloud-oss.com/ipfs/"
```

启动节点
```bash
lotus daemon
```

新建钱包地址
```bash
$ lotus wallet new bls
f3rzwb56yq2lujzoaax4jyajfzxnxesf2dstjqsq2keiwhwt7zfi5kgtqlx5fwdqmaxoybnj7xctva2fsr2uha
```

从水龙头获取测试币。每个IP每天可以领取一次,100Fil。请将下面这条命令的钱包地址替换成你的地址
```bash
curl http://122.9.61.5:6721/api/v1/send?address=f3rzwb56yq2lujzoaax4jyajfzxnxesf2dstjqsq2keiwhwt7zfi5kgtqlx5fwdqmaxoybnj7xctva2fsr2uha
```

等待几分钟后查看余额
```bash
$ lotus wallet list
Address                                                                                 Balance                    Nonce  Default  
f3rzwb56yq2lujzoaax4jyajfzxnxesf2dstjqsq2keiwhwt7zfi5kgtqlx5fwdqmaxoybnj7xctva2fsr2uha  100 FIL  0      X 
```

创建miner 
```bash
$ lotus-miner init --owner 钱包地址  --sector-size=2KiB (默认2K, 支持 8MiB、512MiB、32GiB、64GiB) 
```

启动miner

```
louts-miner run
```

### 区块链浏览器

http://122.9.61.5:4396/#/


