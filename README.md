# Solana-metaplex-core-nft-staking
This project features an on-chain staking program for NFTs on Solana, built using the Anchor framework and adhering to the Metaplex Core standard. The staking system enables users to securely lock their NFTs and unstake them through Solana Web3 interactions.

## Contact me
If you need more technical support and development inquires, you can contact below.


## Overview

This repository provides:

- Anchor Rust Program: The staking and unstaking smart contract for NFTs.
- Web3 Integration: Scripts for interacting with the on-chain program using Solana Web3.js and Metaplex JS SDK.

## Project Structure

- /program: Contains the Anchor-based staking program in Rust.
- /cli: The command lines to stake and unstake NFTs.
- /lib: Custom Libraries to use project's cli using Solana and Metaplex libraries.

## Features
- NFT Staking: Lock up your NFTs and start earning staking rewards.
- NFT Unstaking: Unstake your NFTs once the staking period is over.

## Prerequisites
Before setting up this project, ensure the following dependencies are installed:

- Node.js (v16 or later)
- Anchor CLI (v0.24.2 or later)
- Solana CLI (v1.9.28 or later)
- Rust & Cargo (for building the on-chain program)
- Metaplex JS SDK
- Solana Web3.js

## Installation & Setup

### 1. Clone the repository
```
git clone https://github.com/sharp0904/Metaplex-nft-staking.git
cd Metaplex-nft-staking
```

### 2. Build the Solana Program
Navigate to the program folder and build the staking contract using Anchor.
```
cd program
anchor build
```

#### *important problem*
To build Solana program, you must to use correct dependencies collection.
Here are the correct dependencies for Solana Metaplex Core NFT Staking program.

```
anchor-lang = { version = "0.30.1", features = ["init-if-needed"] }
anchor-lang-idl = { version = "0.1.1", features = ["convert"] }
anchor-spl = "0.30.1"
bytemuck = "1.16.1"
mpl-core = { version = "0.8.0", features = ["anchor"] }
mpl-token-metadata = "4.1.2"
solana-program = "2.0.11"
toml_datetime = "0.6.6"
winnow = "0.6.13"
```

### 3. Deploy the Solana Program
After building the program, deploy it to Solana Devnet or your preferred network:
```
anchor deploy
```

After deployment, note the Program ID printed in the console as it will be required for Web3 interactions.

### 4. Configure Solana CLI
Set your Solana network to devnet or mainnet-beta and ensure you have a wallet configured:

```
solana config set --url https://api.devnet.solana.com
solana config set --keypair ~/.config/solana/id.json
```

### 5. Set Up Web3 Environment
Install the required dependencies for the Web3 interaction scripts:

```
npm install
or
yarn install
```

## Usage

### Init PDAs
```
yarn script init
```

### Staking NFTs via Web3
You can use the provided Web3 script to stake your NFTs on the Solana blockchain.

- Set Up Your Wallet: Make sure your wallet is funded with enough SOL for transaction fees.
- Run the Staking Script:
```
yarn script lock -t nft_type -m nft_mint
```
This command stakes the specified NFT in the program.

### Unstaking NFTs via Web3
Once the staking period is over, users can unstake their NFTs by running the unstaking script.

- Run the Unstaking Script:
```
yarn script unlock -t nft_type -m nft_mint -o nft_owner
```

## Anchor Program Structure
The Anchor Rust program is built around two key accounts:

- Staking Account: Holds user-specific data such as staked NFT details, stake start time, and reward accumulation.

### Core Program Functions
- Stake NFT: Initiates the staking of an NFT and creates a new staking account for the user.
- Unstake NFT: Unlocks the NFT from the staking account, allowing the user to reclaim their NFT and any associated rewards.


