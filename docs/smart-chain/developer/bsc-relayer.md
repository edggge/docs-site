# BSC Relayer Guides

## Download Binary
The codebase will be open-sourced soon. For now, download bsc-relayer binary from this url: <https://github.com/binance-chain/smart-chain-binary>

## Get Example Config File
Get example config from this url: <https://github.com/binance-chain/bsc-relayer-config/blob/master/bsc/testnet/config.json>

Edit`config.json` and fill your BSC private key to bsc_config.private_key, example private key: `AFD8C5D83F148065176268A9D1EE375A10CEE1E74D15985D4CC63E467EC34DA5`

## Prepare Fund

Transfer enough BNB to your account:
1.	100:BNB for relayer register
2.	More than 50:BNB for transaction fee

Currently the bsc-relayer code is not fully prepared. Some features like db persistence, alert, prometheus monitor are still under development. So please don’t modify the configuration about db_config, alert_config, instrumentation_config, admin_config

## Start Relayer

1. Start Locally:
```shell script
./bsc-relayer --config-type local --config-path config.json
```

2. Dynamic Sync Cross Chain Protocol Configuration from <https://github.com/binance-chain/bsc-relayer-config.git>

    1.	Edit config.json and change “cross_chain_config.protocol_config_type” to “remote”. Then relayer will dynamically sync cross chain protocol configuration from this repository: https://github.com/binance-chain/bsc-relayer-config.git
    2.	Start relayer
    ```shell script
   ./bsc-relayer --config-type local --config-path config.json
    ````

3. Import Config File From AWS Secret Manager

    1.	Save the above config file to aws secret manager
    2.	Start relayer
	```shell script
    ./bsc-relayer --config-type aws --aws-region {awsRegion} --aws-secret-key {awsSecretKey}
	```

4. Import BSC Private Key From AWS Secret Manager

    1. Save your bsc private key to aws secret manager
    2. Edit config.json
    3. Change bsc_config.key_type to aws_private_key
    4. Fill  {awsRegion} to bsc_config.aws_region
    5. Fill {awsSecretKey} to bsc_config.aws_secret_name
