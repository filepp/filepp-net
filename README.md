
# filepp-net 
 filepp-net是由filepp社区维护的lotus独立网络，免费提供给社区使用。主要修改了以下功能：
 - 支持2K、8M、512M、32G、64G扇区
 - WaitSeed时间为10 Epoch
 - 最小爆块算力为2K
 
## 加入filepp-net
加入filepp-net，需要使用filepp社区提供的修改过后的lotus代码进行编译。
```
git clone https://github.com/filepp/lotus
cd lotus 
git checkout net/private-v1.4.1
RUSTFLAGS="-C target-cpu=native -g" FFI_BUILD_FROM_SOURCE=1 make debug 
```

下载private.car文件，启动节点
```
lotus daemon --genesis=private.car  --bootstrap=false
```

连接创世节点，使用上面` lotus net listen`，命令返回的地址。如果有公网ip，换成公网ip。（注意每次重启lotus都要执行这条命令，数据才会同步）
```
lotus net connect /ip4/192.168.6.55/tcp/55555/p2p/12D3KooWSr6MuGscVkqvrdXjsVDwB7whQbFj94SmzJs6MStdhYsB
```
查看连接情况
```
$ lotus net peers

12D3KooWSr6MuGscVkqvrdXjsVDwB7whQbFj94SmzJs6MStdhYsB, [/ip4/192.168.6.55/tcp/55555]

```

新建钱包地址
```
$ lotus wallet new bls

f3slo5iisbjgnndg5gygkpqpfv3xotjjqir4scs7bep5gaxfpgahj4y2bjlk7mjsrm6iomyr3rwfm4onzfkbia
```

从水龙头获取测试币
```
curl http://122.9.61.5:6161/api/v1/send?address=f3slo5iisbjgnndg5gygkpqpfv3xotjjqir4scs7bep5gaxfpgahj4y2bjlk7mjsrm6iomyr3rwfm4onzfkbia
```
