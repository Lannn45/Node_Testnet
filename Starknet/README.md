
## Starknet

|  Komponen |  Persyaratan Minimum |
| ------------ | ------------ |
| CPU  | 4-core|
| RAM | 8GB RAM |
| Penyimpanan  | 100GB of storage (SSD or NVME) |

## 1. Registrasi Alchemy
## 2. Membuat App
  - Pilih Ethereum Mainnet
  - Masuk ke App
  - Pilih View Key
  - Semua data disimpan ke Notepad
## 3. Install Docker
 ```
sudo apt update -y && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt install docker-ce
```
## 4. Install Alat
```
sudo apt-get install -y pkg-config curl git build-essential libssl-dev screen
```
## 5. Download Bahan
```
git clone --branch v0.4.0 https://github.com/eqlabs/pathfinder.git
```
## 6. Start
```
mkdir -p $HOME/pathfinder
docker run -d \
  --rm \
  -p 9545:9545 \
  --user "$(id -u):$(id -g)" \
  -e RUST_LOG=info \
  --name starknet \
  -e PATHFINDER_ETHEREUM_API_URL="XXXXXXXXXXXXX" \
  -v $HOME/pathfinder:/usr/share/pathfinder/data \
  eqlabs/pathfinder
```
XXXXXXXXXXXX  diganti dengan link HTTPS mu dari alchemy

## 7. Cek Logs
```
docker logs -f starknet
```
## 8. Done
