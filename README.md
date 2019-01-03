# chain33平行链部署

### Windows环境上部署chain33平行链

> 文件介绍：
- windows/chain33.exe:   chain33区块链的主程序文件
- windows/chain33-cli.exe: 命令行工具（可以用它来实现对区块链的操作，包括创建账户，转账，发送交易，查询等一系列功能）
- windows/chain33.toml: 主程序对应的配置文件

> 备注：
- 这边已经把chain33.exe和chain33-cli.exe两个可执行文件都编译好了，大家也可以下载源码自己编译。
- chain33 源码地址 [https://github.com/33cn/plugin](https://github.com/33cn/plugin) ， 下载后分别执行以下命令

```ini
go build -o chain33.exe
go build -o chain33-cli.exe github.com/33cn/plugin/cli
```

> 环境启动前准备工作：
- 复杂美官方已经提供可供连接的主链节点，可以不用修改配置文件直接启动。
- 如果需要连接自己搭建的主链，修改以下两个配置项中的IP，指向自己主链的地址。

```ini
mainnetJrpcAddr="http://139.219.1.47:8801"
ParaRemoteGrpcClient = "139.219.1.47:8802"
```

> 启动环境：
- 启动 chain33.exe

```ini
chain33.exe -f chain33.toml
```

> 状态检查
- 查询节点是否已经和主链同步 (平行链需要从主链上拉取区块，所以同步需要花一些时间)
```ini
chain33-cli.exe net is_sync
true
```

- 查看区块同步的状态
```ini
chain33-cli.exe block last_header
{
    "version": 0,
    "parentHash": "0x905d3c3ab62718381436720382e436a52976b6798896c77c97cb4e751e3a67c9",
    "txHash": "0x765a8babc9b63f7a5c608afb0943001741f3591f676026cd67dd99f6b3ad5122",
    "stateHash": "0xeb240fe1248028e9c7271ae2838ea3970bb880031764c8154c8bce2d16262cb7",
    "height": 57,
    "blockTime": 1546501778,
    "txCount": 1,
    "hash": "0xac2be112305b231b9851a34f6db7bde1745a2b7c9c3a684c736dc59baf3e6e51",
    "difficulty": 0
}
```

### Linux环境上部署chain33平行链

> 文件介绍：
- linux/chain33:   chain33区块链的主程序文件
- linux/chain33-cli: 命令行工具（可以用它来实现对区块链的操作，包括创建账户，转账，发送交易，查询等一系列功能）
- linux/chain33.toml: 主程序对应的配置文件

> 备注：
其余操作和上面window环境上的类似， 注意主程序文件和命令行工具和window上名字的区别