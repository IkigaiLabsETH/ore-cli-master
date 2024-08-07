# ORE CLI

A command line interface for ORE cryptocurrency mining.

## Install

To install the CLI, use [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html):

```sh
cargo install ore-cli
```

## Build

To build the codebase from scratch, checkout the repo and use cargo to build:

```sh
cargo build --release
```

## Help

You can use the `-h` flag on any command to pull up a help menu with documentation:

```sh
ore -h
```

# Ore Miner

<p align="center">
  <img src="img/Screenshot_23.png" alt="ore">
  <img src="img/dog-destroy.gif"
</p>

This repository is made for $ORE mining purpose on CLI with bash script. $ORE is a mineable token on  Solana blockchain that uses a novel proof-of-work algorithm to guarantee casual miners can never be starved out from earning rewards. You can mine it using your computer or through your phone (anywhere). You can checkout more about token explanation in their [X](https://twitter.com/OreSupply/status/1775176540340547818) and [website](https://ore.supply/).

## How to Start

Here is step by step how to mine $ORE in your computer using terminal (either powershell or WSL terminal it's up to you) or using termux on your phone. You can also run this on cloud-hosted service such as VPS, but make sure your VPS is allowed to do cryptocurrency mining activity.

### 0. Make folder first
Use command below before installing Rust if you use cloud-hosted environment. If you are using local environment, you can skip this part.
```
mkdir -p /home/<your-cloud-environment>/.config/fish/conf.d/
```

### 1. Install Rust and Cargo:
Install Rust and Cargo through curl command line. You can see details about its installation on [here](https://www.rust-lang.org/tools/install).
```
curl https://sh.rustup.rs -sSf | sh
```

### 2. Install Solana CLI, then export PATH to verify your Solana CLI:
After installed Rust and Cargo, install Solana CLI with command below. Dont forget to export the path or restart the terminal after installing Solana CLI.
```
sh -c "$(curl -sSfL https://release.solana.com/v1.18.4/install)"

export PATH="/home/<path>/.local/share/solana/install/active_release/bin:$PATH"
```

### 3. Create a new solana wallet:
Create a new solana wallet on your CLI. Alternatively, if you want to import solana wallet you can use `solana-keygen recover` instead.
```
solana-keygen new
```
### 4. Find your Solana address and send 0.01 SOL on your address:
Assuming 0.01 SOL is enough and optimal for mining later on. You can deposit more SOL if you want.
```
solana-keygen pubkey
```

### 4. Add $ORE contract address to the wallet:
Add $ORE token on your solana CLI, it will cost SOL gasfee.
```
spl-token create-account oreoN2tQbHXVaZsr3pf66A48miqcBXCDJozganhEJgz
```

### 6. Install the Ore CLI:
There is plenty way to install Ore CLI. 
```
cargo install ore-cli
```
You can also clone the source and build from it.
```
git clone https://github.com/HardhatChad/ore-cli.git
cd ore-cli
cargo build --release
```

### 7. Choosing RPC
You can use different Solana RPC endpoints such as Alchemy, Helius, or Solana Mainnet RPC. Here is the list of RPC examples you can use
- https://api.mainnet-beta.solana.com
- [Alchemy](https://www.alchemy.com/solana)
- [Helius](https://www.helius.dev/)
- [Triton](https://triton.one/)
- [Syndica](https://syndica.io/)
- [QuickNode](https://www.quicknode.com/docs/solana)
- [Ankr](https://www.ankr.com/rpc/solana/)
- [GetBlock](https://getblock.io/nodes/sol/)
- [Chainstack](https://chainstack.com/build-better-with-solana/)
- [Blockdaemon](https://www.blockdaemon.com/protocols/solana)
- [OMNIA](https://omniatech.io/pages/solana-rpc/)
- [Hello Moon](https://www.hellomoon.io/developers)
- [EXTR](https://extrnode.com/solana/)
- [Ironforge](https://ore.supply/settings)

### 8. Clone My Repo
Clone my github repo and go the repo folder
```
git clone https://github.com/0xrsydn/ore-miner.git
cd ore-miner
```

### 9. Configure The Script
You should configure and modify the script (oreminer.sh) first such as adding rpc endpoints, adding public key path, configure cpu threads, etc. You could also create a lot of oreminer bash scripts with different rpc endpoints and configurations. After finishing your configuration, make the script executable:
```
chmod +x oreminer.sh claimbalance.sh unclaimedbalance.sh
```

### 10. Run The Script
Stay in that folder and execute oreminer.sh and watch your machine mine ORE for you automatically:
```
./oreminer.sh
```

### 11. Additional information
You can checkout other bash scripts such as claimbalance.sh for claim $ORE, unclaimedbalance.sh for checking unclaimed balance, and checkore.sh to check your $ORE balance. 


## Acknowledgements

Big thanks for [@fear-rush](https://github.com/fear-rush) for insight and optimization for running the mining script. Also thanks for [Little Things](https://t.me/yourlittlething) and its member for great alpha!

## Contribution

Feel free to contribute to the ore-miner script or build on top of it to make it more efficient, run smoothly, or resolve any issues.

## Setting Up CLI for Mining $ORE on a VPS
For those looking to run their mining operations continuously, setting up on a Virtual Private Server (VPS) is advisable. This ensures your mining doesn’t get interrupted by local hardware limitations or connectivity issues.

### VPS Preparation
Install the Solana CLI on your VPS with the command provided by Solana’s release page. I recommend the Vultr VPS. It costs $7.20 and runs perfectly. Make sure to choose a Linux VPS and the “Cloud Compute – shared CPU”. Make sure the Ubuntu version in 22.04 LTS too.


### Remote Server Access
Next, to connect to and manage your VPS, mobaxterm.mobatek.net is the tool of choice. It simplifies remote server management, allowing you to access your VPS files and terminal seamlessly. With MobaXterm installed, initiate a new session and input your VPS’s IP address provided by Vultr. Log in as root using the password Vultr supplies, granting you full access to the server.

### Installing Rust
Rust is a prerequisite for many Solana and blockchain-related tools due to its performance and safety. Install Rust on your server with the following command:

curl https://sh.rustup.rs -sSf | sh

### Installing Solana CLI
The Solana CLI is your gateway to interacting with the Solana blockchain. Install it using the command:

sh -c "$(curl -sSfL https://release.solana.com/v1.18.4/install)"

### Re-Login
After installing the Solana CLI, you’ll need to log out of your VPS and log back in to refresh your session and apply the new settings. Simply close the MobaXterm window and reconnect.

### Creating a New Solana Key
To interact with the Solana blockchain, you’ll need a keypair. Create one with solana-keygen new. Choose a unique string as suggested, although the string itself isn’t used in the key generation process.

### Accessing Your Secret Key
Navigate to the .config/solana folder and open the id.json file. This file contains your secret key, which can be imported into Solana wallets like Phantom or Backpack, providing access to your private key.

### Funding Your Wallet
Before starting to mine, you’ll need some SOL in your wallet to cover the transaction fees associated with mining. Send between 0.05 to 0.1 SOL to your wallet to ensure you’re covered.

### Installing the ORE CLI
The ORE CLI is the core mining software for $ORE. Install it with the command:

cargo install ore-cli
This step may take a few minutes, so now’s a good time for a coffee break!

### Managing Crashes with PM2
To ensure your mining operation runs smoothly without interruptions, use PM2, a process manager for Node.js. Install PM2 globally with:

npm install pm2 -g

### Configuring Your Miner
Create a .json file named mine.json with the following configuration to set up your miner. This file will include necessary details like the RPC endpoint and your keypair file.

{
  "name": "ore_miner",
  "script": "ore",
  "args": ["--rpc", "https://api.mainnet-beta.solana.com", "--keypair", "PATH_TO_YOUR_KEYPAIR", "--other", "args"]
}
Adjust the "args" as needed to match your setup.

### Starting the Miner
With everything set up, start your miner using PM2:

pm2 start mine.json
To monitor your mining operation, pm2 logs will display real-time logs.

### Managing Your Mining Rewards
Finally, to check your balance and claim your mined $ORE, use the following commands:

To view rewards: ore --keypair /root/.config/solana/id.json rewards
To claim rewards: ore --keypair /root/.config/solana/id.json claim <amount>
This guide should have equipped you with all the necessary steps to start CLI mining $ORE on Solana. Remember, the blockchain and crypto mining landscapes are always evolving, so stay engaged with the community for the latest


