# 概述

目前，FISCO BCOS平台支持Solidity和Precompiled两种类型的智能合约，同时，提供交互式控制台工具（Console）,方便开发者与链进行交互，部署、调用智能合约。 

这里只讲solidity智能合约。

## Solidity智能合约特征

- solidity智能合约是一种静态编程语言，支持面向对象的编程，包括继承、库以及复杂的用户关系定义类型等功能。

- 合约可以定义事件（event）。应用程序可以通过以太坊客户端的RPC接口订阅和监听这些事件。事件在合约中可被继承。当他们被调用时，会使参数被存储到交易的日志中。 这些日志与地址相关联，被并入区块链中，只要区块可以访问就一直存在。 日志和事件在合约内不可直接被访问。

- 需要支付Gas费。一经创建，每笔交易都收取一定数量的 gas ，必须由原始交易发起人（ tx.orgin ）支付。 EVM 执行交易时，gas 将按特定规则逐渐耗尽。 无论执行到什么位置，一旦 gas 被耗尽（比如降为负值），将会触发一个 out-of-gas 异常。当前调用帧（call frame）所做的所有状态修改都将被回滚。一个好的合约开发者需要优化合约来减少gas费的燃烧。

- modifier（修改器）。solidity智能合约可以使用modifier来对某个函数执行前进行自动检查，例如：
``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ExampleContract {//创建一个mapping实现地址和年龄的对应关系
    mapping(address => uint) public userAge;

    // 设置modifier来检查年龄
    modifier checkAge(address _user) {
        require(userAge[_user] >= 18, "User must be at least 18 years old");
        _;
    }

    // 在buy函数后需要检查用户年龄
    function buy() public checkAge(msg.sender) {
    }

    function setAge(uint _age) public {
        userAge[msg.sender] = _age;
    }
}
```

## solidity语法

这里不讲了，详情可参考[Solidity 中文文档](https://learnblockchain.cn/docs/solidity/index.html)





