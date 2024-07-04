
# Fabric Gateway 解释

## Fabric Gateway功能

Fabric Gateway (又名网关)管理以下事务步骤：

1. 评估交易提案。这将在单个对等点上调用智能合约（链码）函数并将结果返回给客户端。这通常用于查询账本的当前状态而不进行任何账本更新。网关将最好选择与网关对等点位于同一组织中的对等点，并选择账本区块高度最高的对等点。如果网关的组织中没有可用的对等点，则它将选择来自另一个组织的对等点。

2. 认可交易提案。这将收集足够的认可响应以满足组合签名策略（见下文），并将准备好的交易信封返回给客户端进行签名。

3. 提交交易。这将向排序服务发送已签名的交易信封，以提交到分类账。

4. 等待提交状态事件。这允许客户端等待交易提交到账本并获取提交（验证/无效）状态代码。

5. 接收链码事件。这将允许客户端应用程序在交易提交到分类账时响应智能合约函数发出的事件。

Fabric Gateway 客户端 API 将 Endorse/Submit/CommitStatus 操作合并为一个阻塞式**SubmitTransaction**函数，以支持使用一行代码提交事务。或者，可以调用各个操作来支持灵活的应用程序模式。

## Fabric Gateway API

Hyperledger Fabric目前支持三种语言的客户端应用程序开发：Go ，Java ，Node.js。这里只举例Go相关。

在GO官方文档可以看到在[fabric-samples](https://github.com/hyperledger/fabric-samples)存储库中提供了一些示例，展示了如何创建连接 Hyperledger Fabric 网络并与之交互的客户端应用程序：

[fabric-samples/asset-transfer-basic](https://github.com/hyperledger/fabric-samples/tree/main/asset-transfer-basic)为交易提交和评估的示例。
[fabric-samples/asset-transfer-events](https://github.com/hyperledger/fabric-samples/tree/main/asset-transfer-events)是链码事件的示例。
[fabric-samples/off_chain_data](https://github.com/hyperledger/fabric-samples/tree/main/off_chain_data)为区块事件的示例。

