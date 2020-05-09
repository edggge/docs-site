# Tokenhub
```json
[
	{
		"inputs": [],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "constructor"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint256[]",
				"name": "amounts",
				"type": "uint256[]"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "expireTime",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "relayFee",
				"type": "uint256"
			}
		],
		"name": "LogBatchTransferOut",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address[]",
				"name": "recipientAddrs",
				"type": "address[]"
			},
			{
				"indexed": false,
				"internalType": "address[]",
				"name": "refundAddrs",
				"type": "address[]"
			}
		],
		"name": "LogBatchTransferOutAddrs",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			}
		],
		"name": "LogBindInvalidParameter",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			}
		],
		"name": "LogBindRejected",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "totalSupply",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "peggyAmount",
				"type": "uint256"
			}
		],
		"name": "LogBindRequest",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "totalSupply",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "peggyAmount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "decimals",
				"type": "uint256"
			}
		],
		"name": "LogBindSuccess",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			}
		],
		"name": "LogBindTimeout",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint16",
				"name": "reason",
				"type": "uint16"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "actualBalance",
				"type": "uint256"
			}
		],
		"name": "LogRefundFailureInsufficientBalance",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint16",
				"name": "reason",
				"type": "uint16"
			}
		],
		"name": "LogRefundFailureUnboundToken",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint16",
				"name": "reason",
				"type": "uint16"
			}
		],
		"name": "LogRefundFailureUnknownReason",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint16",
				"name": "reason",
				"type": "uint16"
			}
		],
		"name": "LogRefundSuccess",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "bep2TokenAmount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "actualBalance",
				"type": "uint256"
			}
		],
		"name": "LogTransferInFailureInsufficientBalance",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "bep2TokenAmount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "expireTime",
				"type": "uint256"
			}
		],
		"name": "LogTransferInFailureTimeout",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "bep2TokenAmount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			}
		],
		"name": "LogTransferInFailureUnboundToken",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "bep2TokenAmount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			}
		],
		"name": "LogTransferInFailureUnknownReason",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			}
		],
		"name": "LogTransferInSuccess",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "sequence",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "refundAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "expireTime",
				"type": "uint256"
			},
			{
				"indexed": false,
				"internalType": "uint256",
				"name": "relayFee",
				"type": "uint256"
			}
		],
		"name": "LogTransferOut",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "bytes",
				"name": "lowLevelData",
				"type": "bytes"
			}
		],
		"name": "LogUnexpectedFailureAssertionInBEP2E",
		"type": "event"
	},
	{
		"anonymous": false,
		"inputs": [
			{
				"indexed": false,
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"indexed": false,
				"internalType": "string",
				"name": "reason",
				"type": "string"
			}
		],
		"name": "LogUnexpectedRevertInBEP2E",
		"type": "event"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "BEP2_TOKEN_DECIMALS",
		"outputs": [
			{
				"internalType": "uint8",
				"name": "",
				"type": "uint8"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "BEP2_TOKEN_SYMBOL_FOR_BNB",
		"outputs": [
			{
				"internalType": "bytes32",
				"name": "",
				"type": "bytes32"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "BIND_CHANNEL_ID",
		"outputs": [
			{
				"internalType": "uint8",
				"name": "",
				"type": "uint8"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "GOV_HUB_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "INCENTIVIZE_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "LIGHT_CLIENT_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "MAXIMUM_BEP2E_SYMBOL_LEN",
		"outputs": [
			{
				"internalType": "uint8",
				"name": "",
				"type": "uint8"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "MAX_BEP2_TOTAL_SUPPLY",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "MAX_GAS_FOR_CALLING_BEP2E",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "MINIMUM_BEP2E_SYMBOL_LEN",
		"outputs": [
			{
				"internalType": "uint8",
				"name": "",
				"type": "uint8"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "REFUND_CHANNEL_ID",
		"outputs": [
			{
				"internalType": "uint8",
				"name": "",
				"type": "uint8"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "RELAYERHUB_CONTRACT_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "RELAYER_REWARD",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "SLASH_CONTRACT_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "SYSTEM_REWARD_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "TOKEN_HUB_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "TRANSFER_IN_CHANNEL_ID",
		"outputs": [
			{
				"internalType": "uint8",
				"name": "",
				"type": "uint8"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "VALIDATOR_CONTRACT_ADDR",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "bytes32",
				"name": "",
				"type": "bytes32"
			}
		],
		"name": "_bep2SymbolToContractAddr",
		"outputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"name": "_bep2eContractDecimals",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "_bindChannelSequence",
		"outputs": [
			{
				"internalType": "uint64",
				"name": "",
				"type": "uint64"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "bytes32",
				"name": "",
				"type": "bytes32"
			}
		],
		"name": "_bindPackageRecord",
		"outputs": [
			{
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			},
			{
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"internalType": "uint256",
				"name": "totalSupply",
				"type": "uint256"
			},
			{
				"internalType": "uint256",
				"name": "peggyAmount",
				"type": "uint256"
			},
			{
				"internalType": "uint8",
				"name": "bep2eDecimals",
				"type": "uint8"
			},
			{
				"internalType": "uint64",
				"name": "expireTime",
				"type": "uint64"
			},
			{
				"internalType": "uint256",
				"name": "relayFee",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "_bindResponseChannelSequence",
		"outputs": [
			{
				"internalType": "uint64",
				"name": "",
				"type": "uint64"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "address",
				"name": "",
				"type": "address"
			}
		],
		"name": "_contractAddrToBEP2Symbol",
		"outputs": [
			{
				"internalType": "bytes32",
				"name": "",
				"type": "bytes32"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "_refundChannelSequence",
		"outputs": [
			{
				"internalType": "uint64",
				"name": "",
				"type": "uint64"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "_transferInChannelSequence",
		"outputs": [
			{
				"internalType": "uint64",
				"name": "",
				"type": "uint64"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "_transferInFailureChannelSequence",
		"outputs": [
			{
				"internalType": "uint64",
				"name": "",
				"type": "uint64"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "_transferOutChannelSequence",
		"outputs": [
			{
				"internalType": "uint64",
				"name": "",
				"type": "uint64"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"internalType": "string",
				"name": "bep2Symbol",
				"type": "string"
			}
		],
		"name": "approveBind",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "address[]",
				"name": "recipientAddrs",
				"type": "address[]"
			},
			{
				"internalType": "uint256[]",
				"name": "amounts",
				"type": "uint256[]"
			},
			{
				"internalType": "address[]",
				"name": "refundAddrs",
				"type": "address[]"
			},
			{
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"internalType": "uint256",
				"name": "expireTime",
				"type": "uint256"
			},
			{
				"internalType": "uint256",
				"name": "relayFee",
				"type": "uint256"
			}
		],
		"name": "batchTransferOut",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": true,
		"stateMutability": "payable",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "string",
				"name": "symbol",
				"type": "string"
			}
		],
		"name": "bep2TokenSymbolConvert",
		"outputs": [
			{
				"internalType": "bytes32",
				"name": "",
				"type": "bytes32"
			}
		],
		"payable": false,
		"stateMutability": "pure",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "string",
				"name": "bep2eSymbol",
				"type": "string"
			},
			{
				"internalType": "bytes32",
				"name": "bep2TokenSymbol",
				"type": "bytes32"
			}
		],
		"name": "checkSymbol",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "pure",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [
			{
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"internalType": "uint256",
				"name": "bep2eTokenDecimals",
				"type": "uint256"
			}
		],
		"name": "convertToBep2Amount",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "pure",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "denominaroeHeaderRelayerSystemReward",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "string",
				"name": "bep2Symbol",
				"type": "string"
			}
		],
		"name": "expireBind",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "bytes",
				"name": "msgBytes",
				"type": "bytes"
			},
			{
				"internalType": "bytes",
				"name": "proof",
				"type": "bytes"
			},
			{
				"internalType": "uint64",
				"name": "height",
				"type": "uint64"
			},
			{
				"internalType": "uint64",
				"name": "packageSequence",
				"type": "uint64"
			}
		],
		"name": "handleBindPackage",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "bytes",
				"name": "msgBytes",
				"type": "bytes"
			},
			{
				"internalType": "bytes",
				"name": "proof",
				"type": "bytes"
			},
			{
				"internalType": "uint64",
				"name": "height",
				"type": "uint64"
			},
			{
				"internalType": "uint64",
				"name": "packageSequence",
				"type": "uint64"
			}
		],
		"name": "handleRefundPackage",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "bytes",
				"name": "msgBytes",
				"type": "bytes"
			},
			{
				"internalType": "bytes",
				"name": "proof",
				"type": "bytes"
			},
			{
				"internalType": "uint64",
				"name": "height",
				"type": "uint64"
			},
			{
				"internalType": "uint64",
				"name": "packageSequence",
				"type": "uint64"
			}
		],
		"name": "handleTransferInPackage",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "minimumRelayFee",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "moleculeHeaderRelayerSystemReward",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": true,
		"inputs": [],
		"name": "refundRelayReward",
		"outputs": [
			{
				"internalType": "uint256",
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"internalType": "string",
				"name": "bep2Symbol",
				"type": "string"
			}
		],
		"name": "rejectBind",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"internalType": "address",
				"name": "contractAddr",
				"type": "address"
			},
			{
				"internalType": "address",
				"name": "recipient",
				"type": "address"
			},
			{
				"internalType": "uint256",
				"name": "amount",
				"type": "uint256"
			},
			{
				"internalType": "uint256",
				"name": "expireTime",
				"type": "uint256"
			},
			{
				"internalType": "uint256",
				"name": "relayFee",
				"type": "uint256"
			}
		],
		"name": "transferOut",
		"outputs": [
			{
				"internalType": "bool",
				"name": "",
				"type": "bool"
			}
		],
		"payable": true,
		"stateMutability": "payable",
		"type": "function"
	}
]
```