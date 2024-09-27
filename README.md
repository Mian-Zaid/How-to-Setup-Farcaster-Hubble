# How to Setup and Build Farcaster Hubble from Source
This Guide will teach us how to download, build, and run Farcaster Hubble.

## Prerequisites

You need to get your `ETH-mainnet-RPC-URL` & `Optimism-L2-RPC-URL` from [**Alchemy**](https://dashboard.alchemy.com/), and for `FID` you need to have a **Farcaster** Account setup via **Warpcast** or any other client.

---

Next, we must install a few prerequisite libraries to help us build the Hubble.

```
sudo apt update & sudo apt upgrade
```
#### Install Curl
```
sudo apt install curl -y
```

#### Install Node JS
```
curl -fsSL https://deb.nodesource.com/setup_current.x | sudo -E bash -

sudo apt install -y nodejs
```

#### Verify installation
```
node -v
```

#### Install Yarn
```
npm install --global yarn
```

```
yarn -v
```

#### Install Foundry
```
curl -L https://foundry.paradigm.xyz | bash
```

```
source ~/.bashrc
```

```
foundryup
```

#### Install Rust
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

```
source $HOME/.cargo/env
```

```
rustc --version
```

#### Install build-essential (which includes the GCC compiler and other development tools)
```
sudo apt install build-essential -y
```

#### Install Cmake
```
sudo apt install cmake -y
```

#### Install Libclang
```
sudo apt install -y libclang-dev
```

#### Install Llvm
```
sudo apt install -y llvm
```

#### Install Protobuf Compiler
Goto https://github.com/protocolbuffers/protobuf/releases and navigate the to latest release for Linux and copy it's link
```
curl -LO https://github.com/protocolbuffers/protobuf/releases/download/v28.2/protoc-28.2-linux-x86_64.zip
```

```
unzip protoc-28.2-linux-x86_64.zip -d $HOME/.local
```

```
export PATH="$PATH:$HOME/.local/bin"
```

```
protoc --version
```


## Download and Build the Hubble

Now after installing all the Prerequisites, it's time to Download & build the Farcaster Hubble.

```
git clone https://github.com/farcasterxyz/hub-monorepo.git
```

```
cd hub-monorepo
```

```
yarn install
```

```
yarn build
```

```
yarn test
```

## Running the Hubble
Now we have Hubble built and tested locally, Now it's time to Run it and Sync its data

```
cd apps/hubble
```

```
yarn identity create
```

Next, we need to connect with the Network type, either it's Mainnet or Testnet.

create env file

```
touch .env
```

open it using nano
```
nano .env
```

### Testnet

paste the following inside .env and save it
```
FC_NETWORK_ID=2
BOOTSTRAP_NODE=/dns/testnet1.farcaster.xyz/tcp/2282
```

### Mainnet

paste the following inside .env
```
FC_NETWORK_ID=1
BOOTSTRAP_NODE=/dns/hoyt.farcaster.xyz/tcp/2282
```

save the .env file

```
Press ctrl+o

Press enter

Press ctrl+x
```


Now it's time to Run the Hubble
### Testnet
```
yarn start --eth-mainnet-rpc-url <your ETH-mainnet-RPC-URL> --l2-rpc-url <your Optimism-L2-RPC-URL> --hub-operator-fid <your FID> -n 2 -b /dns/testnet1.farcaster.xyz/tcp/2282
```

### Mainnet
```
yarn start --eth-mainnet-rpc-url <your ETH-mainnet-RPC-URL> --l2-rpc-url <your Optimism-L2-RPC-URL> --hub-operator-fid <your FID> -n 1 -b /dns/hoyt.farcaster.xyz/tcp/2282
```

Now this process of syncing can take several hours depending on the Internet speed
