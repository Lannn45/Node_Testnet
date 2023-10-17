
# Single Proc

Install Docker

Docker 
```
sudo apt-get update && sudo apt install git -y && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

Install NodeJS
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
source ~/.bashrc
nvm install 18
nvm use 18
```

Install Subsquid CLI
```
npm install --global @subsquid/cli@latest
```

Create Folder & init
```
mkdir proc
cd proc
sqd init single-proc -t https://github.com/subsquid-quests/single-chain-squid
cd single-proc
```

Key Subsquid

https://app.subsquid.io/quests

Start Docker

```
docker compose up -d
```

Build

```
npm ci
sqd build
```

Run
```
sqd run .
```