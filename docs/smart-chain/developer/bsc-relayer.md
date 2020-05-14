# BSC Relayer Guides

## Download Binary
The codebase will be open-sourced soon. For now, download bsc-relayer binary from this url: <https://github.com/binance-chain/smart-chain-binary>

## Get Example Config File
Get example config from this url: https://github.com/binance-chain/bsc-relayer-config/blob/master/bsc/testnet/config.json

Edit`config.json` and fill your BSC private key to bsc_config.private_key, example private key: AFD8C5D83F148065176268A9D1EE375A10CEE1E74D15985D4CC63E467EC34DA5

## Prepare Fund
2.	Transfer enough BNB to your account:
i.	100:BNB for relayer register
ii.	More than 50:BNB for transaction fee
Now the bsc-relayer is not fully prepared. Some features like db persistence, alert, prometheus monitor are still under development. So please don’t modify the configuration about db_config, alert_config, instrumentation_config, admin_config
Start Relayer
Start Locally:
./bsc-relayer --config-type local --config-path config.json
Dynamic Cross Chain Protocol Configuration
1.	Edit config.json and change “cross_chain_config.protocol_config_type” to “remote”. Then relayer will dynamically sync cross chain protocol configuration from this repository: https://github.com/binance-chain/bsc-relayer-config.git
2.	Start relayer
./bsc-relayer --config-type local --config-path config.json
Import Config File From AWS Secret Manager
1.	Save the above config file to aws secret manager
2.	Start relayer
	./bsc-relayer --config-type aws --aws-region {awsRegion} --aws-secret-key {awsSecretKey}
Import BSC Private Key From AWS Secret Manager
1.	Save your bsc private key to aws secret manager
2.	Edit config.json
a.	change bsc_config.key_type to aws_private_key
b.	Fill  {awsRegion} to bsc_config.aws_region
c.	Fill {awsSecretKey} to bsc_config.aws_secret_name

