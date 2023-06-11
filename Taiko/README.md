
# TAIKO ALPHA-3 TESTNET

## Hardware Requirements
### Recommended:
|  Komponen |  Persyaratan Minimum |
| ------------ | ------------ |
| CPU  | 4-core|
| RAM | 16GB+ RAM |
| Penyimpanan  | 1TB of free space (SSD) |

## Update & Install depencies
```
cd $HOME
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential git wget npm jq make gcc tmux -y
```

## Clean Docker (Optional)
DO NOT DO THIS IF YOU ALREADY HAVE RUNNING DOCKER!!! IT WILL REMOVE DOCKER COMPLETELY AND CAUSE ERROR!
```
apt purge docker docker-engine docker.io containerd docker-compose -y
```

## Install Docker
```
rm /usr/bin/docker-compose /usr/local/bin/docker-compose
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
systemctl restart docker
curl -SL https://github.com/docker/compose/releases/download/v2.18.1/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
systemctl start docker
gpasswd -a $USER docker
```

## Create user for Taiko
```
sudo adduser taiko
echo "taiko ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
sudo su - taiko
```

## Clone Binary
```
git clone https://github.com/taikoxyz/simple-taiko-node.git
cd simple-taiko-node
cp .env.sample .env
```

Edit .env
```
nano .env
```

Edit:
- L1_ENDPOINT_HTTP:
- L1_ENDPOINT_WS:

You can find this using Alchemy or Infura by creating API on Sepolia ETH Testnet

You can also set the port to whatever you like

- Change this settings if you want to change the port the node running on (OPTIONAL)
```
# Exposed ports
PORT_L2_EXECTION_ENGINE_HTTP=8545
PORT_L2_EXECTION_ENGINE_WS=8546
PORT_L2_EXECTION_ENGINE_METRICS=6060
PORT_L2_EXECTION_ENGINE_P2P=30303
PORT_ZKEVM_CHAIN_PROVER_RPCD=9000
PORT_PROMETHEUS=9090
PORT_GRAFANA=3000
```
## Start Prover
Requirements:
- Must have a balance of ETH on Sepolia, Faucet List : https://taiko.xyz/docs/guides/receive-tokens
- Node set up
- Should have at least 8/16 core CPU and 32GB of RAM

### Guide
```
cd simple-taiko-node
nano .env
```
- Set ENABLE_PROVER to true (replacing the default false with true).
- Set L1_PROVER_PRIVATE_KEY to that of your wallet’s private key; it will need some ETH on Sepolia to prove blocks

### Logs 
```
docker compose logs -f
```

Proposer logs
```
docker compose logs -f taiko_client_proposer
```
## Start a Proposer if you have TTKO if not , just skip

Requirements:
- Must have a balance of ETH and TTKO on Sepolia,Faucet List : https://taiko.xyz/docs/guides/receive-tokens
- Node set up

## Guide
Go to https://sepolia.etherscan.io/address/0x6375394335f34848b850114b66A49D6F47f2cdA8#writeProxyContract Click Connect to Web3

## Enter Deposit
Click depositTaikoToken and enter the amount of TTKO you would like to deposit followed by 8 zeroes.

Example 1 TTKO = 100000000 (8 Zeros)

click Write

## Edit .env
```
cd simple-taiko-node
nano .env
```
- Set ENABLE_PROPOSER to true (replacing the default false with true).
- Set L1_PROPOSER_PRIVATE_KEY to that of your wallet’s private key; it will need some TTKO on Sepolia to propose blocks
- Set L2_SUGGESTED_FEE_RECIPIENT to the recipient of L2 ETH rewards.

## Logs
Docker Logs
```
docker compose logs -f
```
Proposer Logs
```
docker compose logs -f taiko_client_proposer
```
- After finished setting up for Prover or Proposer, Start your node

## Start Node
Start Node
```
docker compose up
```
Start in the background (Recommended)
```
docker compose up -d
```
## More Commands
Stop Node
```
docker compose down
```
Remove Node
```
docker compose down -v
rm -f .env
```
Update Node (if any)
```
docker compose pull
```
## Monitoring
To Monitor your hardware usage and node go to :
```
http://localhost:3000/d/L2ExecutionEngine/l2-execution-engine-overview
```
Change localhost to your node ip if you are using VPS

