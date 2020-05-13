# Cross-chain Communication

## How much is cross-chain transfer fee?

The total cost of transfer from BC to BSC is composed of 2 parts:

* Fee for executing `bridge transfer-out` transaction is 0.01BNB,  pay validators on Binance Chain

* Fee for BSC-relayers 0.01BNB. it will cover the fees of calling TokenHub Contract on BSC.

The total cost of transfer from BSC to BC is composed of 2 parts:

* Fee for Oracle-relayers 0.02BNB, pay for BSC relayers

* Call TokenHub Contract: You need to pay BNB for calling smart-contract on BSC, this transaction is metered by gas, which is a global parameter. At the moment, you need to pay about ~ 0.001BNB.

## What's is a BSC relayer?

Relayer transport packages of Block Header and Merkle Proof verification to let BSC validators verify the block transactions and even the state value .


## What's is an Oracle relayer?

Oracle Relayer watches the state change of Binance Smart Chain. Once it catches Cross-Chain Communication Packages, it will submit to vote for the requests. After Oracle Relayers from ⅔ of the voting power of BC validators vote for the changes, the cross-chain actions will be performed. Only validators of Binance Chain are eligible to run Oracle relayers.


## What's an oracle?

In blockchain network, an oracle refers to the element that connects smart contracts with data from the outside world. In the network of Binance Smart Chain, the execution of the transanction wil emit Events, and such events can be packaged and relayed onto BC. In this way, BC will get updates about changes of BSC.

## Which wallet support cross-chain transfer?

You need to use [MyEtherWallet]() to call contracts and use  Binance Chain commandline client: `bnbcli`/ `tbnbcli` for complementry commands