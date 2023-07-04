---
description: >-
  BusinessShop native bridge is used to relay the BusinessShop native token between BusinessShop and
  Ethereum networks
---

# BusinessShop: Ethereum ↔ BusinessShop

BusinessShop native bridge between Ethereum and BusinessShop is used to relay the BusinessShop native token from BusinessShop to Ethereum network

## Architecture Overview

The BusinessShop bridged is based on POA's bridge implementation, it is used to transfer BusinessShop tokens between the BusinessShop chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's BusinessShop or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of BusinessShop tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the BusinessShop chain on Ethereum**

Each cycle the total block reward distributed on BusinessShop chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on BusinessShop chain, waiting for all bridge validators on BusinessShop chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the BusinessShop network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://bspexplorer.com/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0x2cefeD419aa09923e79dd7F17E5d3A617Fef0BBc](https://bspexplorer.com/address/0x2cefeD419aa09923e79dd7F17E5d3A617Fef0BBc/transactions)

BusinessShop token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On BusinessShop you send native BusinessShop token to the home bridge contract. Then you receive an equal amount of the BusinessShop token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the BusinessShop token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the BusinessShop native token, sent from the home bridge contract.

#### 

