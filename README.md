# Axelar Local Development Example dApps

## Introduction

This repo provides the code for several example dApps in the [Axelar Local Development Environment](https://github.com/axelarnetwork/axelar-local-dev). It contains both the JavaScript and the Solidity code for each example. To try them out:

- Set up your system.
- Test and deploy each example.

Note: You may see example folders in this repo that are not described below. They are either placeholders for ideas for the future, such as the `temp` folder, or they are dApps in progress and we'll add a description when they're finished.

## Setup

1. To manage your node programs, make sure that you have node.js and npm installed by running `node -v`. If no version is returned, run
`npm update && npm install`.

2. To clone this repo, run `git clone https://github.com/axelarnetwork/axelar-local-gmp-examples.git`.
3. To make sure all contracts are compiled, run `npm run build`.
4. On a separate terminal, run `node scripts/createLocal`. You’ll need to have this node running to deploy the dApps.
5. Make sure that the address we use for examples is funded on all five supported testnets. 

   a. Run `node/printBalances`.

   b. Look for `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`, the address we use to deploy and run all examples.

## Test and deploy each example

For each example, enter `local` or `testnet` (for both the test and the deploy steps), the `source-chain` and the `destination-chain`, and variables such as `message`, `amount`, and `account`.

### Call contract

1. To relay a message from source-chain to destination-chain, run:

`node scripts/test examples/call-contract [<local|testnet>] ${source-chain} ${destination-chain} ${message}`

2. Run `yarn call-contract`.

3. To deploy the dApp, run::

`node scripts/deploy examples/call-contract [<local|testnet>]`

### Call contract with token

1. To send aUSDC from source-chain to destination-chain and distribute it equally among all accounts specified, run:

`node scripts/test examples/call-contract-with-token [<local|testnet>] ${source-chain} ${destination-chain} ${amount} ${account1} ${account2}...`

2. To deploy the dApp, run:

`node scripts/deploy examples/call-contract-with-token [<local|testnet>]`

### Cross chain token

1. To mint some token at source-chain and have it sent to destination-chain, run:

`node scripts/test examples/cross-chain-token [<local|testnet>] ${source-chain} ${destination-chain} ${amount}`

2. To deploy the dApp, run:

`node scripts/deploy examples/cross-chain-token [<local|testnet>]`

### Deposit address

1. To run on testnet, fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC and replace local with testnet.

2. To send aUSDC from the source to the destination, run:

`node scripts/test examples/deposit-address [<local|testnet>] ${source-chain} ${destination-chain} ${amount}`

`Deposit-address` is a transaction. There is no smart contract to deploy.

### Headers

1. To inform destination-chain of the last header of source-chain, run:

`node scripts/test examples/headers [<local|testnet>] ${source-chain} ${destination-chain}`

2. To deploy the dApp, run:

`node scripts/deploy examples/headers [<local|testnet>]`

### NFT linker

1. To send the NFT that was originally minted at source-chain to destination-chain, run:

`node scripts/test examples/nft-linker [<local|testnet>] ${source-chain} ${destination-chain}`

You cannot send a duplicate NFT to a chain. The dApp fails when the NFT is already at the destination-chain.

2. To deploy the dApp, run:

`node scripts/deploy examples/nft-linker [<local|testnet>]`

A single NFT is minted to the deployer (`0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`) on each chain.

### Nonced execution

1. To send a message from source-chain to destination-chain, run: 

`node scripts/test examples/nonced-execution [<local|testnet>] ${source-chain} ${destination-chain} ${message}`

2. To deploy the dApp, run:

`node scripts/deploy examples/nonced-execution [<local|testnet>]`

### Send ack

1. To send a message from source-chain to destination-chain, run:

`node scripts/test examples/send-ack [<local|testnet>] ${source-chain} ${destination-chain} ${message}`

2. To deploy the dApp, run:

`node scripts/deploy examples/send-ack [<local|testnet>]`

### Send token

1. To send aUSDC from the source to the destination, run:
 
`node scripts/test examples/send-token [<local|testnet>] ${source-chain} ${destination-chain} ${amount}` 

2. To run on testnet, fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC and replace local with testnet. 

`Send-token` is a transaction. There is no smart contract to deploy.

## Conclusion

With each example that you try, look for confirmation in the terminal output.


