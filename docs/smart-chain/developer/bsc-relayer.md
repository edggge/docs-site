# BSC Relayer Guides

## Download Binary
The codebase will be open-sourced soon. For now, download bsc-relayer binary from this url: <https://github.com/binance-chain/smart-chain-binary>

## Get Example Config File
Get example config from this url: <https://github.com/binance-chain/bsc-relayer-config/blob/master/bsc/testnet/config.json>

Edit`config.json` and fill your BSC private key to bsc_config.private_key, example private key: `AFD8C5D83F148065176268A9D1EE375A10CEE1E74D15985D4CC63E467EC34DA5`

## Prepare Fund

1. Make sure that you have enough BNB in your account. You can get from [faucet](https://testnet.binance.org/faucet-smart)

> If you haven't created your account yet, please follow these [guides](../wallet/metamask.md) to create one first.
* 100:BNB for relayer register
* More than 50BNB for transaction fee

!!! Tip
		Currently the bsc-relayer code is not fully prepared. Some features like `db persistence`, `alert`, `prometheus monitor` are still under development. So please don’t modify the configuration about db_config, alert_config, instrumentation_config, admin_config

## Start Relayer

1. Start Locally

```shell script
./bsc-relayer --config-type local --config-path config.json
```

2. Dynamic Sync Cross Chain Protocol Configuration from <https://github.com/binance-chain/bsc-relayer-config.git>

    * Edit config.json and change “cross_chain_config.protocol_config_type” to “remote”. Then relayer will dynamically sync cross chain protocol configuration from this repository: https://github.com/binance-chain/bsc-relayer-config.git
    * Start relayer
    ```shell script
   ./bsc-relayer --config-type local --config-path config.json
    ````
