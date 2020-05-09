# Staking

## PoSA Consensus of Binance Smart Chain

[Binance Smart Chain](https://community.binance.org/topic/2686) is an innovative solution to bring programmability and interoperability to [Binance Chain](https://www.binance.org). Binance Smart Chain relies on a system of 21 validators with Proof of [Staked Authority (PoSA) consensus](../../smart-chain/guides/concepts/consensus.md) that can support short block time and lower fees. The most bonded validator candidates of staking will become validators and produce blocks. The double-sign detection and other slashing logic guarantee security, stability, and chain finality.

## Staking on Binance Chain

Ideally, Binance Smart Chain should build such staking and reward logic into the blockchain, and automatically distribute rewards as the blocking happens. [Cosmos Hub](https://hub.cosmos.network/), who also build on top of Tendermint consensus like Binance Chain, works in this way.

However, as BSC wants to remain compatible with Ethereum as much as possible. On the other side, Binance Chain already has a staking module and could be extended to support both BC and BSC. In this way, all the staking related operations are recorded in BC. Once there are any changes about BSC's validator set or voting power, the new message will be transferred to BSC through cross-chain communication.

## Staking Economics

1. The staking token is **[BNB](https://www.binance.com/cn/trade/BNB_USDT)**, as it is a native token on both blockchains anyway
2. The staking, i.e. token bond and delegation actions and records for BSC, happens on BC.
3. The BSC validator set is determined by its staking and delegation logic, via a staking module built on BC for BSC, and propagated every day UTC 00:00 from BC to BSC via Cross-Chain communication.
4. The reward distribution happens on BC around every day UTC 00:00.

## Ranking Algorithm

Validators are ranked by their power and operator address. The more its delegation tokens, the higher ranking is. If two validators get the same amount of delegated tokens, validator with smaller address bytes has higher ranking.


## Commands

### Create BSC Validator

#### Parameters for bsc-create-validator


| **parameter name**           | **example**                          | **comment**                                                  | **required** |
| ---------------------------- | ------------------------------------ | ------------------------------------------------------------ | ------------ |
| --chan-id                    | Binance-Chain-XXX                    | the chain id of binance  chain                               | Yes          |
| --from                       | bnb1xxx/tbnb1xxx                     | address of private key  with which to sign this tx, also be used as the validator operator address | Yes          |
| --address-delegator          | bnb1xxx/tbnb1xxx                     | optional, bech32 address  of the self-delegator. if not provided, --from address will be used as  self-delegator. | No           |
| --amount                     | 2000000000000:BNB  (means 20000 BNB) | self-delegation amount,  it has 8 decimal places             | Yes          |
| --moniker                    | myval1                               | validator name                                               | Yes          |
| --identity                   | xxx                                  | optional identity  signature (ex. UPort or Keybase)          | No           |
| --website                    | www.example.com                      | optional website                                             | No           |
| --details                    | some details                         | optional details                                             | No           |
| --commission-rate            | 80000000(that means 0.8  or 80%)     | The initial commission  rate percentage, it has 8 decimal places. | Yes          |
| --commission-max-rate        | 95000000  (0.95 or 95%)              | The maximum commission  rate percentage, it has 8 decimal places. | Yes          |
| --commission-max-change-rate | 3000000   (0.03 or 3%)               | The maximum commission  change rate percentage (per day)     | Yes          |
| --side-chain-id              | BSC-XXX                              | chain-id of the side  chain the validator belongs to         | Yes          |
| --side-cons-addr             | 0x1234abcd                           | consensus address of the  validator on side chain, please use hex format prefixed with 0x | Yes          |
| --side-fee-addr              | 0xabcd1234                           | address that validator  collects fee rewards on side chain, please use hex format prefixed with 0x | Yes          |
| --home                       | /path/to/cli_home                    | home directory of bnbcli  data and config, default to “~/.bnbcli” | No           |



#### Examples

1. If you want to create a validator with the same operator address and self-delegator address, you only need one signature for this transaction.

* Mainnet

```bash
bnbcli staking bsc-create-validator --chain-id Binance-Chain-Kongo --from bnb1tfh30c67mkzfz06as2hk0756mgdx8mgypu7ajl --amount 2000000000000:BNB --moniker bsc_v1 --identity "xxx" --website "[www.example.](http://www.binance.org)com" --details "bsc validator node 1" --commission-rate 80000000 --commission-max-rate 95000000 --commission-max-change-rate 3000000 --side-chain-id bsc-c1-abc --side-cons-addr 0x9B24Ee0BfBf708b541fB65b6087D6e991a0D11A8 --side-fee-addr 0x5885d2A27Bd4c6D111B83Bc3fC359eD951E8E6F8 --home ~/home_cli
```
* Testnet

2. If you want a separated self-delegator address, both `self-delegator` and `validator operator` need to sign this transaction. Here we need to use another two commands to support multiple signatures.

a. use the above commands appended with a parameter “**--generate-only**” and save the result to a file which would be used to be signed.

b. both validator operator(--from) and self-delegator(--address-delegator) use “**bnbcli sign**” command to sign the file from a).

c. use “**bnbcli broadcast**” to send the transaction from above to the blockchain nodes.



### Edit BSC Validator

#### Parameters for bsc-edit-validator

| **parameter name** | **example**                      | **comments**                                                 | **required** |
| ------------------ | -------------------------------- | ------------------------------------------------------------ | ------------ |
| --chan-id          | Binance-Chain-XXX                | the chain id of binance  chain                               | Yes          |
| --from             | bnb1xxx/tbnb1xxx                 | address of private key  with which to sign this tx, that also indicate the validator that you want to  edit. | Yes          |
| --side-chain-id    | BSC-XXX                          | chain-id of the side  chain the validator belongs to         | Yes          |
| --moniker          | myval1                           | validator name (default  "[do-not-modify]")                  | No           |
| --identity         | xxx                              | optional identity  signature (ex. UPort or Keybase) (default "[do-not-modify]") | No           |
| --website          | www.example.com                  | optional website (default  "[do-not-modify]")                | No           |
| --details          | some details                     | optional details (default  "[do-not-modify]")                | No           |
| --commission-rate  | 80000000(that means 0.8  or 80%) | The new commission rate  percentage                          | No           |
| --side-fee-addr    | 0xabcd1234                       | address that validator  collects fee rewards on side chain, please use hex format prefixed with 0x. | No           |



#### Examples

* Mainnet

```bash
bnbcli staking bsc-edit-validator --chain-id Binance-Chain-Kongo --side-chain-id bsc-c1-abc --moniker bsc_v1_new --from bnb1tfh30c67mkzfz06as2hk0756mgdx8mgypu7ajl --home ~/home_cli
```
* Testnet


### Delegate BNB

#### Parameters for staking bsc-delegate

| **parameter name** | **example**              | **comments**                                                 | **required** |
| ------------------ | ------------------------ | ------------------------------------------------------------ | ------------ |
| --chan-id          | Binance-Chain-XXX        | the chain id of binance  chain                               | Yes          |
| --from             | bnb1xxx/tbnb1xxx         | address of private key  with which to sign this tx, that is also the delegator address | Yes          |
| --side-chain-id    | BSC-XXX                  | chain-id of the side  chain the validator belongs to         | Yes          |
| --validator        | bva1xxx                  | bech32 address of the  validator, starts with “bva”          | Yes          |
| --amount           | 1000000000:BNB  (10 BNB) | delegation amount, it has  8 decimal places                  | Yes          |



#### Examples

* Mainnet

```bash
bnbcli staking bsc-delegate --chain-id Binance-Chain-Kongo --side-chain-id bsc-c1-abc --from bnb1tfh30c67mkzfz06as2hk0756mgdx8mgypu7ajl --validator bva1tfh30c67mkzfz06as2hk0756mgdx8mgypqldvm --amount 1000000000:BNB --home ~/home_cli
```
* Testnet


### Redelegate BNB

#### Parameters for staking bsc-redelegate

| **parameter name**      | **example**              | **comments**                                                 | **required** |
| ----------------------- | ------------------------ | ------------------------------------------------------------ | ------------ |
| --chan-id               | Binance-Chain-XXX        | the chain id of binance  chain                               | Yes          |
| --from                  | bnb1xxx/tbnb1xxx         | address of private key  with which to sign this tx, that is also the delegator address | Yes          |
| --side-chain-id         | BSC-XXX                  | chain-id of the side  chain the validator belongs to         | Yes          |
| --addr-validator-source | bva1xxx                  | bech32 address of the  source validator, starts with “bva”   | Yes          |
| --addr-validator-dest   | bva1yyy                  | bech32 address of the  destination validator, starts with “bva” | Yes          |
| --amount                | 1000000000:BNB  (10 BNB) | delegation amount, it has  8 decimal places                  | Yes          |

#### Examples

* Mainnet

```bash
bnbcli staking bsc-redelegate --chain-id Binance-Chain-Kongo --side-chain-id bsc-c1-abc --from bnb1tfh30c67mkzfz06as2hk0756mgdx8mgypu7ajl --addr-validator-source bva1tfh30c67mkzfz06as2hk0756mgdx8mgypqldvm --addr-validator-dest bva1jam9wn8drs97mskmwg7jwm09kuy5yjumvvx6r2 --amount1000000000:BNB --home ~/home_cli
```


### Undelegate BNB

#### Parameters for staking bsc-unbond

| **parameter name** | **example**              | **comments**                                                 | **required** |
| ------------------ | ------------------------ | ------------------------------------------------------------ | ------------ |
| --chan-id          | Binance-Chain-XXX        | the chain id of binance  chain                               | Yes          |
| --from             | bnb1xxx/tbnb1xxx         | address of private key  with which to sign this tx, that is also the delegator address | Yes          |
| --side-chain-id    | BSC-XXX                  | chain-id of the side  chain the validator belongs to         | Yes          |
| --validator        | bva1xxx                  | bech32 address of the  validator, starts with “bva”          | Yes          |
| --amount           | 1000000000:BNB  (10 BNB) | delegation amount, it has  8 decimal places                  | Yes          |

#### Examples

* Mainnet

```bash
bnbcli staking bsc-unbond --chain-id Binance-Chain-Kongo --side-chain-id bsc-c1-abc --from bnb1tfh30c67mkzfz06as2hk0756mgdx8mgypu7ajl --validator bva1tfh30c67mkzfz06as2hk0756mgdx8mgypqldvm --amount 1000000000:BNB --home ~/home_cli
```


### Query side chain vaildator by operator

#### Parameters for staking side-validator --help**

| **parameter name** | **example**       | **comments**                                         | **required** |
| ------------------ | ----------------- | ---------------------------------------------------- | ------------ |
| --chan-id          | Binance-Chain-XXX | the chain id of binance  chain                       | Yes          |
| --side-chain-id    | BSC-XXX           | chain-id of the side  chain the validator belongs to | Yes          |

#### Examples

* Mainnet

```bash
bnbcli staking side-validator bva1hz5sg3u0v4gq2veyw5355z7qx6y7uuqhcuzf3f  --side-chain-id bsc --chain-id=Binance-Chain-Kongo --home ~/home_cli
```

### Query side chain delegation by delegator and operator

#### Parameters for staking side-delegation

| **parameter name** | **example**       | **comments**                                         | **required** |
| ------------------ | ----------------- | ---------------------------------------------------- | ------------ |
| --chan-id          | Binance-Chain-XXX | the chain id of binance  chain                       | Yes          |
| --side-chain-id    | BSC-XXX           | chain-id of the side  chain the validator belongs to | Yes          |

#### Examples

* Mainnet
bash
```bash
bnbcli staking side-delegation bnb1hz5sg3u0v4gq2veyw5355z7qx6y7uuqhcqre0d bva1hz5sg3u0v4gq2veyw5355z7qx6y7uuqhcuzf3f --chain-id=Binance-Chain-Kongo --side-chain-id bsc --home ~/home_cli
```


### Query side chain delegations by delegator

#### Parameters for staking side-delegations

| **parameter name** | **example**       | **comments**                                         | **required** |
| ------------------ | ----------------- | ---------------------------------------------------- | ------------ |
| --chan-id          | Binance-Chain-XXX | the chain id of binance  chain                       | Yes          |
| --side-chain-id    | BSC-XXX           | chain-id of the side  chain the validator belongs to | Yes          |

#### Examples

* Mainnet

```bash
bnbcli staking side-delegations bnb1hz5sg3u0v4gq2veyw5355z7qx6y7uuqhcqre0d --side-chain-id bsc --node=0.0.0.0:26657 --chain-id=Binance-Chain-Kongo --trust-node
```