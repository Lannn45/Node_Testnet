## Check or Monitor

### Check the latest TX on chain with the testnet RPC
```
curl --location --request POST https://fullnode.testnet.sui.io:443 \
  --header 'Content-Type: application/json' \
  --data-raw '{ "jsonrpc":"2.0", "method":"sui_getTotalTransactionNumber","id":1}'
``` 
### Check the latest TX on your node:
```
curl --location --request POST http://127.0.0.1:9000/ \
  --header 'Content-Type: application/json' \
  --data-raw '{ "jsonrpc":"2.0", "method":"sui_getTotalTransactionNumber","id":1}' 
```
### To check TPS on your node in Testnet:
```
wget -O $HOME/check_testnet_tps.sh https://raw.githubusercontent.com/bartosian/sui_helpers/main/check_testnet_tps.sh && chmod +x $HOME/check_testnet_tps.sh && $HOME/check_testnet_tps.sh
```
### to run it again:
```
$HOME/check_testnet_tps.sh
```