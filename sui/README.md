## Run a Sui Full node
Sui Full nodes validate blockchain activities, including transactions, checkpoints, and epoch changes. Each Full node stores and services the queries for the blockchain state and history.

This role enables [ validators ](https://docs.sui.io/devnet/learn/architecture/validators) to focus on servicing and processing transactions. When a validator commits a new set of transactions (or a block of transactions), the validator pushes that block to all connected Full nodes that then service the queries from clients.

## Full node setup
# Hardware requirements
Suggested hardware requirements for running a Sui Full node:

- CPUs: 10 core 
- RAM: 32 GB 
- Storage: 1 TB 
We recommend running Sui Full nodes on Linux. Sui supports the Ubuntu and Debian distributions. You can also run a Sui Full node on macOS.

# These are steps to set up Testnet Node in Docker:

1. Install Linux dependencies.
```
sudo apt update \
&& apt-get install -y --no-install-recommends \
apt-transport-https \
ca-certificates \
curl \
software-properties-common
```
2. Install Docker.
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update \
sudo apt install docker-ce
```
3. Add your user to docker Group.
```
sudo usermod -aG docker ${USER}
```
4. Install Docker Compose.
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```
5. Create SUI directory.
```
mkdir -p $HOME/sui
cd $HOME/sui
```
6. Download fullnode.yaml.
```
wget -O $HOME/sui/fullnode-template.yaml https://github.com/MystenLabs/sui/raw/main/crates/sui-config/data/fullnode-template.yaml
```
7. Download genesis state file.
```
wget -O $HOME/sui/genesis.blob  https://github.com/MystenLabs/sui-genesis/raw/main/testnet/genesis.blob
```
8. Download docker-compose file and update Sui Node image in it:
```
IMAGE="mysten/sui-node:2d07756360c28e35d7c60816bb0f1ed94ccf356e"
wget -O $HOME/sui/docker-compose.yaml https://raw.githubusercontent.com/MystenLabs/sui/main/docker/fullnode/docker-compose.yaml
sed -i.bak "s|image:.*|image: $IMAGE|" $HOME/sui/docker-compose.yaml
```
9. Start SUI Full Node in the Docker container.
```
docker-compose up -d
```
10. Check logs from SUI Node container:
```
docker ps

docker logs -f <container id>
```