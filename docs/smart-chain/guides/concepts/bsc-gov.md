# Governance of BSC

## Motivation

There are many system parameters to control the behavior of the BSC:

a. All these parameters of BSC system contracts should be flexible: slashing threshold, cross-chain transfer fees, relayer reward amount

b. BC parameters

All these smart-contract parameters will be determined by BSC Validator Set together through a proposal-vote process based on their staking. Such the process will be carried on BC, and the new parameter values will be picked up by corresponding system contracts via a cross-chain communication.

## Design Principles

**For BC:**

a. Codebase reuse: Reuse most of the structure of proposal and vote, and the logic about propose and vote.

b. Available at once: The cross-chain package should be available once the proposal passed.

**For BSC:**

a.  Uniform interface. The contracts who are interested in these parameters only need to implement the same interface.

b. Extensible. When adding a new system contract, there is no need to modify any other contracts.

c.  Failure toleration. Validators could vote to skip false proposals and go on.

d. Multiplexing. Now we have only parameters gov, but in the future, there will be more governance functions.

### Workflow

![img](https://lh6.googleusercontent.com/BfhfTNpitqKUEJ_k9NxvH-HcZNNrm3ebX7t8AmZi1YnjHBoP2rrrkqehjDqxhw82iBIW9McCSG1b4SaVYHDQdw4FrsSTgr9u244dVHkbBYhnl-0e1Fz3Ubc0wxMoGMkNzwQq-w78)


### Fee Table

| Msg type                   | Fee         | Fee For                      |
| -------------------------- | ----------- | ---------------------------- |
| MsgSideChainSubmitProposal | 10 BNBs     | Proposer                     |
| MsgSideChainDeposit        | 0.00125 BNB | Proposer                     |
| MsgSideChainVote           | 1 BNB       | Proposer                     |
| Relayer reward             | 0.05 BNB    | come from system reward pool |



