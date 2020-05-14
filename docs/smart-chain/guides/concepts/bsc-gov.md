# Governance of BSC

## Motivation

There are many system parameters to control the behavior of the BSC:

**a.**     **slashing threshold, cross-chain transfer fees, relater reward amount etc. All these parameters are all in system contracts and should be flexible.**

**b.**     **params on BBC.**

All these parameters will be determined by BSC Validator Set together through a proposal-vote process based on their staking. Such the process will be carried on BC, and the new parameter values will be picked up by corresponding system contracts via a cross-chain communication.

## Design Principles

For BC:

a.  Code reuse. Reuse most of the structure of proposal and vote, and the logic about propose and vote.

b. Available at once. The cross chain package should be available once the proposal passed.

For BSC:

a.  Uniform interface. The contracts who are interested with these parameters only need implement thea same interface.

b. Extensible. When add new system contract, there is no need to modify any other contracts.

c.  Failure toleration. Can skip false proposal and go on.

d. Multiplexing. Now we have only parameters gov, but in future we may have be more gov func.

### Workflow

 

![img](https://lh6.googleusercontent.com/BfhfTNpitqKUEJ_k9NxvH-HcZNNrm3ebX7t8AmZi1YnjHBoP2rrrkqehjDqxhw82iBIW9McCSG1b4SaVYHDQdw4FrsSTgr9u244dVHkbBYhnl-0e1Fz3Ubc0wxMoGMkNzwQq-w78)


### Fee 

| Msg type                   | Fee         | Fee For                      |
| -------------------------- | ----------- | ---------------------------- |
| MsgSideChainSubmitProposal | 10 BNBs     | Proposer                     |
| MsgSideChainDeposit        | 0.00125 BNB | Proposer                     |
| MsgSideChainVote           | 1 BNB       | Proposer                     |
| Relayer reward             | 0.05 BNB    | come from system reward pool |

 

 