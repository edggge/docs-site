# BEP2E Contract Interface

```
  function totalSupply() external view returns (uint256);

  function decimals() external view returns (uint256);

  function symbol() external view returns (string memory);

  function getOwner() external view returns (address);

  function balanceOf(address account) external view returns (uint256);

  function transfer(address recipient, uint256 amount) external returns (bool);

  function allowance(address _owner, address spender) external view returns (uint256);

  function approve(address spender, uint256 amount) external returns (bool);

  function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);

  event Transfer(address indexed from, address indexed to, uint256 value);

  event Approval(address indexed owner, address indexed spender, uint256 value);
```

BEP2E Smart Contract ABI: [ABI.json](BEP2E.json)

You can follow the steps below to interact with the smart contract by using Web3 library and NodeJS.


## Connect to Binance Smart Chain's public RPC endpoint

```JavaScript
const Web3 = require('web3');

const web3 = new Web3('https://data-seed-prebsc-1-s1.binance.org:8545');
```

## Create a wallet

```javascript
web3.eth.accounts.create([entropy]);

```
Output:
```bash
web3.eth.accounts.create();
{
  address: '0x926605D0729a968266f1BB299d8Df0471C4F5367',
  privateKey: '0x6b4618539d95f205f33e916e89404b301dde545c0c4acc181fd0c0b42708bad3',
  signTransaction: [Function: signTransaction],
  sign: [Function: sign],
  encrypt: [Function: encrypt]
}

```

## Recover a wallet

```javascript

const account = web3.eth.accounts.privateKeyToAccount("0xe500f5754d761d74c3eb6c2566f4c568b81379bf5ce9c1ecd475d40efe23c577")

```


## Check balance

```javascript
web3.eth.getBalance(holder).then(console.log);

```

Output:

The balance will be bumped by e18 for BNB.

```
6249621999900000000
```

## Create transaction

**Parameters**

* Object - The transaction object to send:
* from - String|Number: The address for the sending account. Uses the web3.eth.defaultAccount property, if not specified. Or an address or index of a local wallet in web3.eth.accounts.wallet.
* to - String: (optional) The destination address of the message, left undefined for a contract-creation transaction.
* value - Number|String|BN|BigNumber: (optional) The value transferred for the transaction in wei, also the endowment if it’s a contract-creation transaction.
* gas - Number: (optional, default: To-Be-Determined) The amount of gas to use for the transaction (unused gas is refunded).
* gasPrice - Number|String|BN|BigNumber: (optional) The price of gas for this transaction in wei, defaults to web3.eth.gasPrice.
* data - String: (optional) Either a ABI byte string containing the data of the function call on a contract, or in the case of a contract-creation transaction the initialisation code.
* nonce - Number: (optional) Integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.

```Javascript

	// // Make a transaction using the promise
	web3.eth.sendTransaction({
	    from: holder,
	    to: '0x0B75fbeB0BC7CC0e9F9880f78a245046eCBDBB0D',
	    value: '1000000000000000000',
	    gas: 5000000,
        gasPrice: 18e9,
	}, function(err, transactionHash) {
      if (err) {
        console.log(err);
        } else {
        console.log(transactionHash);
       }
    });
```

## Deploy BEP2E contract

```

```

