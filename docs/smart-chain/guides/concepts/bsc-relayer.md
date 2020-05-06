# BSC Relayer
Relayers are responsible to submit Cross-Chain Communication Packages between the two blockchains. Due to the heterogeneous parallel chain structure, two different types of Relayers are created.

Relayers for BC-to-BSC communication referred to as **BSC Relayers** are a standalone process that can be run by anyone, and anywhere, except that Relayers must register themselves onto BSC and deposit a certain amount of BNB. Only relaying requests from the registered Relayers will be accepted by BSC.

## Monitor and Parse IBC Event
As a BSC relayer, it must have proper configurations on the following three items:

| Name | Type | Description |
| ---- | ---- | ----------- |
|    srcIBCChainID  |   uint16   |      IBCChainID of BC, the value is 1 for testnet       |
|destIBCChainID|uint16|IBCChainID of BSC, the value is 2 for testnet|
|destChainName|string|name of BSC, the value is “bsc”|

BSC relayer should try get all block result and pick out the event whose event type is “IBCPackage” from endBlock event table. Mark the block height as **H**. If there is no ibc event, then just skip this block. This is an example of ibc event.

```json
{ "type": "IBCPackage",
"attributes":
 [{    "key": "IBCPackageInfo",
       "value": "bsc::2::8::19"   }]
}

```

BSC relayer should iterate all the attributes and parse the attribute value:

1. Split the value with “::” and get a 4-length string array
2. Follow the following table to parse the 4 elements:

|IndexDesription|Type|Example Value|
| ---- | ---- | ----------- |
|0|destination chain name|string|bsc|
|1|IBCChainId of destination chain |int16|2|
|2|channel id|int8|8|
|3|sequenceu|int64|19|

3. Filter out all attributes with mismatched destIBCChainID and destChainName.

## Query BC Header and IBC Store
### Query BC Header at Height
```golang
type Header struct {
  tmtypes.SignedHeader
  ValidatorSet     *tmtypes.ValidatorSet `json:"validator_set"`
  NextValidatorSet *tmtypes.ValidatorSet `json:"next_validator_set"`
}
```

Call the following rpc methods to build the above Header object:

|Name|Method|
| ---- | ---- |
|tmtypes.SignedHeader|{rpc}/commit?height=**H**|
|ValidatorSet|{rpc}/validators?height=**H**|
|NextValidatorSet|{rpc}/validators?height=**H+1**|

Encode the Header object to a byte array:

1. Import cdc from tendermint crypto:https://github.com/tendermint/tendermint/blob/master/crypto/encoding/amino/amino.go
2. Call MarshalBinaryLengthPrefixed to encode header struct:
```golang
func (h *Header) EncodeHeader() ([]byte, error) {
		bz, err := cdc.MarshalBinaryLengthPrefixed(h)
		if err != nil {
			return nil, err
			}
		return bz, nil
	}
```

### Query Package With Proof
1. Specify the height as H
2. Query path: /store/ibc/key
3. Follow the talble to build a 14-length byte array as query key:

|Name|Length|Value|
| ---- | ---- | ------ |
|prefix|1 bytes|0x00|
|ibcChainID of souceChain|2 bytes|srcIBCChainID in configration|
|ibcChainID of destChain|2 bytes|destIBCChainID in configration|
|channelID|1 bytes|channelID in attribute value|
|sequence|8 bytes|sequence in attribute value|

4. The query result should contains non-empty package bytes and merkle proof byte.

## Call Build-In System Contract

### Sync BC Header
* function **syncTendermintHeader**(bytes calldata header, uint64 height)
Call syncTendermintHeader of TendermintLightClient contract to sync BC header. The contract address is 0x0000000000000000000000000000000000001003. The “header” should be the encoding result of Header struct and the height should be **H + 1**

### Deliver Cross Chain Package
Follow this table to get build-in system contract address and method name:

|ChannelID|Desription|contract address|Methods|
| ---- | ---- | ----------- |----|
|1|bind channel|0x0000000000000000000000000000000000001004|handleBindPackage|
|2|transfer channel|0x0000000000000000000000000000000000001004|handleTransferInPackage|
|3|refund channel|0x0000000000000000000000000000000000001004|handleRefundPackage|
|8|staking channel|0x0000000000000000000000000000000000001000|handlePackage|

All above methods shares the same parameter table:


|Parameter Name|Type|Value|
| ---- | ---- | ----------- |
|msgBytes|[]byte|package bytes|
|proof|[]byte|merkle proof bytes|
|height|uint64|**H + 1**|
|packageSequence|uint64|sequence from attribution value|

## Incentives Mechanism
