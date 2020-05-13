# Cross-chain Communication

## How much is cross-chain transfer fee?

The total cost of transfer from BC to BSC is composed of 2 parts:

* Fee for `bnbcli bridge transfer-out` 0.01BNB,  pay validators on Binance Chain

* Fee for BSC-relayers 0.01BNB. it will cover the fees of calling TokenHub Contract on BSC.

The total cost of transfer from BSC to BC is composed of 2 parts:

* Fee for Oracle-relayers 0.02BNB, pay for BSC relayers

* Call TokenHub Contract: You need to pay BNB for calling smart-contract on BSC, this transaction is metered by gas, which is a global parameter. At the moment, you need to pay about ~ 0.001BNB.

## What's is an Oracle relayer?

Relayer transport packages of Block Header and Merkle Proof verification to let BC validators verify the block transactions and even the state value .

## What's an oracle?

The execution of the transanction wil emit Events, and such events can be observed and packaged in certain “Oracle” onto BC.

## Which wallet support cross-chain transfer?

You need to use [MyEtherWallet]() to call contracts and use `bnbcli` for complementry commands