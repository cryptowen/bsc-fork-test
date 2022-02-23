# 复现说明

```bash
yarn install
cp .env.example .env
npx hardhat run scripts/sample-script.js
```

## 问题说明

### 使用 BSC 公共节点

不指定 BLOCK_NUM 直接跑可以成功。

反注释掉 BLOCK_NUM 再跑，有如下报错：

```
HardhatError: HH110: Invalid JSON-RPC response received: {"jsonrpc":"2.0","error":{"code":-32603,"message":"internal error"}}
```

猜测是 BSC 公共节点不支持 archive node，访问老数据报的错。

### 使用 alchemy

设不设置 BLOCK_NUM 均能成功

### 使用 nodereal

设不设置 BLOCK_NUM 均有报错

报的错比较随机，形如

```
ProviderError: missing trie node 5c294222535a643fd62a3bb7d7543c55a498e29b197b76309e549c75ba67487a (path )
```

或

```
ProviderError: getDeleteStateObject (000000000000000000636f6e736f6c652e6c6f67) error: missing trie node c8ac9bb3e657d312f01b194fc49ec312c2548f329a5ad0aa535f1047924f2f01 (path )
```

## 参考

- https://hardhat.org/hardhat-network/guides/mainnet-forking.html
- https://github.com/NomicFoundation/hardhat/issues/1236