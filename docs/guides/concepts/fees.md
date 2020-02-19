---
id: fees
title: Fees
---

- [ ] https://docs.binance.org/trading-spec.html (see fees)

**BNB** is the native token on Binance Chain, thus users are charged BNB for sending transactions.

### Trading Fees on DEX

Trading fees are subject to complex logic that may mean that individual trades are not charged exactly by the rates below, but between them instead; this is due to the block-based matching engine in use on the DEX.

The current fee for trades, applied on the settled amounts, is as follows:

Transaction Type | Pay in non-BNB Asset | Pay in BNB
-- | -- | --
Trade | 0.1% | 0.04%

Trading fee can be queried at [here](https://dex.binance.org/api/v1/fees?format=amino). It's under the "params/DexFeeParam/".  "FeeRate" and "FeeRateNative" are both under unit of 10^-6.

### Fix Fee Table

The difference between Binance Chain and Ethereum is that there is no notion of `gas`. As a result,
fees for the rest transactions are fixed. The details are showned in the table below:
<!--END_DOCUSAURUS_CODE_TABS-->

<!--DOCUSAURUS_CODE_TABS-->
<!--Mainnet-->
Transaction Type | Pay in Non-BNB Asset | Pay in BNB | Exchange (DEX) Related
-- | -- | -- | --
New Order | 0 | 0 | Y
Cancel (No Fill) | Equivalent 0.00025 BNB | 0.00005 BNB | Y
Order Expire (No Fill) | Equivalent 0.00025 BNB | 0.00005 BNB | Y
IOC (No Fill) | Equivalent 0.0001 BNB | 0.000025 BNB | Y
Transfer | N/A | 0.000375 BNB | N
Multi-send | N/A | 0.0003 BNB | N
Issue Asset | N/A | 500 BNB | N
Mint Asset | N/A | 5 BNB | N
Burn Asset | N/A | 0.5 BNB | N
Freeze/Unfreeze Asset | N/A | 0.005 BNB | N
Lock/unlock/relock Asset | N/A | 0.01 BNB | N
List Asset | N/A | 1000 BNB | N
Submit List Proposal | N/A | 5 BNB | N
Submit Delist Proposal | N/A | 1000 BNB | N
Deposit | N/A | 0.000625 BNB | N
Enable Memo Check | N/A | 1 BNB | N
Disable Memo Check | N/A | 1 BNB | N
HTLT | N/A | 0.000375 BNB | N
depositHTLT | N/A | 0.000375 BNB | N
claimHTLT | N/A | 0.000375 BNB | N
refundHTLT | N/A | 0.000375 BNB | N
<!--Testnet-->
Transaction Type | Pay in Non-BNB Asset | Pay in BNB | Exchange (DEX) Related
-- | -- | -- | --
New Order | 0 | 0 | Y
Cancel (No Fill) | Equivalent 0.00025 BNB | 0.00005 BNB | Y
Order Expire (No Fill) | Equivalent 0.00025 BNB | 0.00005 BNB | Y
IOC (No Fill) | Equivalent 0.0001 BNB | 0.000025 BNB | Y
Transfer | N/A | 0.000375 BNB | N
Multi-send | N/A | 0.0003 BNB | N
Issue Asset | N/A | 500 BNB | N
Mint Asset | N/A | 5 BNB | N
Burn Asset | N/A | 0.5 BNB | N
Freeze/Unfreeze Asset | N/A | 0.005 BNB | N
Lock/unlock/relock Asset | N/A | 0.01 BNB | N
List Asset | N/A | 1000 BNB | N
Submit List Proposal | N/A | 5 BNB | N
Submit Delist Proposal | N/A | 1000 BNB | N
Deposit | N/A | 0.000625 BNB | N
Enable Memo Check | N/A | 1 BNB | N
Disable Memo Check | N/A | 1 BNB | N
HTLT | N/A | 0.000375 BNB | N
depositHTLT | N/A |  0.000375 BNB | Y
claimHTLT | N/A |  0.000375 BNB | Y
refundHTLT | N/A |  0.000375 BNB | Y

<!--END_DOCUSAURUS_CODE_TABS-->

### How to calculate multisend fee
`bnbcli`  offers you a multi-send command to transfer multiple tokens to multiple people. 20% discount is available for `multi-send` transactions. For now, `multi-send` transaction will send some tokens from one address to multiple output addresses. If the count of output address is bigger than the threshold, currently it's 2, then the total transaction fee is  0.001 BNB per token per address.
For example, if you send 3 ABC token,1 SAT token and 1 ABC to 3 different addresses.

```json
[
   {
      "to":"bnb1g5p04snezgpky203fq6da9qyjsy2k9kzr5yuhl",
      "amount":"100000000:BNB,100000000:ABC"
   },
   {
      "to":"bnb1l86xty0m55ryct9pnypz6chvtsmpyewmhrqwxw",
      "amount":"100000000:BNB"
   },
   {
      "to":"bnb1l86xty0maxdgst9pnypz6chvtsmpydkjflfioe",
      "amount":"100000000:BNB,100000000:SAT"
   }
]
```
You will pay on mainnet/testnet

```
0.0003 BNB * 5 = 0.0015 BNB
```

## How to query fees in every block

The rewards for Binance Chain validators are displayed in explorer. For example: in block [59947302](https://explorer.binance.org/block/59947302), validator [bnb1tpagqqqx36gq09kzw4f5a3a9sk3tq54dpl5ldn](https://explorer.binance.org/address/bnb1tpagqqqx36gq09kzw4f5a3a9sk3tq54dpl5ldn) get `0.00005 BNB` as rewards.

If you have a fullnode running, you can also get the rewards details exported. To achieve this, you need to set `publishBlockFee` to be true in your `app.toml`. To receive rewards stream, there aretwo options `publishKafka` and `publishLocal`

```toml
# Whether we want publish block fee changes
publishBlockFee = true
blockFeeTopic = "accounts"
blockFeeKafka = "127.0.0.1:9092"
# Global setting
publicationChannelSize = "10000"
publishKafka = false
publishLocal = true
```

The rewards history are saved under `{fullnode home}/marketdata/marketdata.json`. For example,

> Note: Quantities here are expressed without decimals, i.e. shifted by 10^8

```json
{"Height":59947302,"Fee":"BNB:5000","Validators":["bnb1tpagqqqx36gq09kzw4f5a3a9sk3tq54dpl5ldn"]}
{"Height":59947303,"Fee":"BNB:5000","Validators":["bnb1y888axmhzz6yjj464syfy68mkhzy9phlv8fzac"]}
{"Height":59947304,"Fee":"BNB:5000","Validators":["bnb19klje94mnu53wj7pmrk0zmtpwgr0uz8th0fcvw"]}
{"Height":59947305,"Fee":"BNB:21364","Validators":["bnb19hunw9ps8n9tkrp2j64jvheezgqmfc2eyrxd7a"]}
{"Height":59947306,"Fee":"","Validators":[]}
...
{"Height":59947480,"Fee":"BUSD-BD1:1486828;XRP-BF2:3311258","Validators":["bnb19klje94mnu53wj7pmrk0zmtpwgr0uz8th0fcvw"]}
...
```
Trading fees can be charged in different BEP2 tokens,
