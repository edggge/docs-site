# Build-in System Contract
## On-Chain Light Client
[introduction about on-chain light client verification algorithm]

The purpose of cross-chain interoperability is to enable one blockchain to function as a light-client of another. Since Binance Chain is using a classical Byzantine Fault Tolerant consensus algorithm, light-client verification is cheap and easy: all we have to do is check validator signatures on the latest block, and verify a Merkle proof of the state.

In Tendermint, validators agree on a block before processing it. This means that the signatures and state root for that block aren't included until the next block. Thus, each block contains a field called LastCommit, which contains the votes responsible for committing the previous block, and a field in the block header called AppHash, which refers to the Merkle root hash of the application after processing the transactions from the previous block. So, if we want to verify the AppHash from height H, we need the signatures from LastCommit at height H+1. (And remember that this AppHash only contains the results from all transactions up to and including block H-1)

Unlike Proof-of-Work, the light-client protocol does not need to download and check all the headers in the blockchain - the client can always jump straight to the latest header available, so long as the validator set has not changed much. If the validator set is changing, the client needs to track these changes, which requires downloading headers for each block in which there is a significant change. Here, we will assume the validator set is constant, and postpone handling validator set changes for another time.

Ethereum platform supports stateless precompiled contract implemented with golang and normal contract implemented with solidity. Comparing with normal contract, precompiled contracts are more efficient and costs less gas, but they are stateless. However, on-chain light client must be stateful. So here we will try to a mixed approach: precompiled implemented contract(stateless calculation, such as signature verification) and normal contract (store validator set and trusted appHash).


![img](https://lh5.googleusercontent.com/NgjBCXKChSKMrFWWWF2DGWLu32h_SAivQZabZqaiD68JOuynFDG7U5FHPwj6VXlMCwYpX6tWBqRtIAhJmP6bt9Htes5bxJQTw6dHD5R6n_P2BCB04Yh-ZAnzJm-aD8fydBYr2V88)

### Precompile Contract

#### Validate Tendermint Header

This contract implements tendermint header verification algorithm. The input parameters contain the trusted consensus state and a new tendermint header. The validation algorithm will verify the new tendermint header against the trusted consensus state. If the new header is valid, a new consensus state will be created and returned to caller. Otherwise, an error will be returned.

#### Validate Merkle Proof

This contract implements a [Tendermint merkle proof verification algorithm](https://github.com/tendermint/tendermint/blob/master/docs/architecture/adr-026-general-merkle-proof.md).

### Solidity Contract

#### Tendermint Light Client Contract

1. ConsensusState: The first consensus state will be written in the constructor. Once a new tendermint header is verified, a new consensus state will be created.
```golang
type ConsensusState struct {
  chainID                       string
  height                         int64
  appHash                    []byte
  curValidatorSetHash  []byte
  nextValidatorSet        *tmtypes.ValidatorSet
}
```
2. Tendermint Header: A relayer who want to sync new tendermint headers need to query BC to build this object. Then encode it to byte array and call syncTendermintHeader.
```golang
type Header struct {
    Header blockHeader
    Validator[] CurValidatorSet
    Validator[] NextValidatorSet
}
```
This contract implements the following four methods:

1. function **syncTendermintHeader**(byte[] header, uint64 height)
syncTendermintHeader gets nearest consensus state by height and call validateTendermintHeader in precompiled contract to verify the tendermint header. If the success, a new consensus state will be saved.

2. function **getAppHash**(uint64 height) returns(bytes32)
getAppHash provides a method to get the verified appHash at the specified height. Besides, If the header the specified height have not be verified, then zero value will be returned.

3. function **isHeaderSynced**(uint64 height) returns (bool)
isHeaderSynced provides a lower cost method to judge if the specified height has been synced.

4. function **getSubmitter**(uint64 height) returns (address)
getSubmitter provides a method to get the submitter address of the specified header.

#### Merkle Proof Verification Library
This library provides an util to to verify merkle proof from BC. Any contract which need to verify merkle proof just need to import this Library.

function **verifyMerkleProof**(int64 height, byte[] key, byte[] value, byte[] proof) bool

**verifyMerkleProof** reassembles user parameters and call the the above precompiled contract to validate the proof.

### Other Build-in System Contract

1. TokenHub Contract
This contract focuses on token binding and cross chain token transfer.

2. BscValidatorSet Contract
This contract focuses on handling staking change package from BC. It also provides the validatorset data query for BSC consensus engine.

3. RelayerHub Contract
This contract manages the authority of bsc-relayer. Someone who wants to run a bsc-relayer must call the contract to deposit some BNB to get the authorization.

4. Governance Contract
This contract handles governance packge from BC. A governance packge contains target contract address, parameter name and new parameter value. Once the package is verified, this contract will call the parameter update method of the target contract to update the parameter to new value.

