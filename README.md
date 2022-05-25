# Axelar Local Development Example dApps

## Introduction

This repo provides the code for several example dapps in the [Axelar Local Development Environment](https://github.com/axelarnetwork/axelar-local-dev). It contains both the javascript and the Solidity code for each example. To try running them:

- Set up your system to run and deploy the dapps.
- Test and deploy each example.

## Setup

To manage your node programs, make sure that you have node.js and npm installed, run `node -v`. If you don’t have it, run
`npm update && npm install`.

1. Make sure all contracts are compiled by running `npm run build`.
2. On a separate terminal, run `node scripts/createLocal`. You’ll need to have this node running to deploy your app.
3. Make sure that the address we use for examples is funded on all five supported testnets. 
   a. Run `node/printBalances`.
   b. Look for `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`, the address we use to deploy and run all examples.

## Test and deploy each example

To test each example, run the code with any of its optional params. Then deploy the example.

### Call contract

1. To relay a message from source-chain to destination-chain, run:

`node scripts/test examples/call-contract ${local|testnet} ${source-chain} ${destination-chain} ${message}`

2. Run `yarn call-contract`

3. To deploy the dapp, run:

`node scripts/deploy examples/call-contract ${local|testnet}`

### Call contract with token

1. To send aUSDC from source-chain to destination-chain and distribute it equally among all accounts specified, run:

`node scripts/test examples/call-contract-with-token ${local|testnet} ${source-chain} ${destination-chain} ${amount} ${account1} ${account2}...`

2. To deploy the dapp, run:

`node scripts/deploy examples/call-contract-with-token ${local|testnet}`

### Cross chain token

1. To mint some token at source-chain and have it sent to destination-chain, run:

`node scripts/test examples/cross-chain-token ${local|testnet} ${source-chain} ${destination-chain} ${amount}`

2. To deploy the dapp, run:

`node scripts/deploy examples/cross-chain-token ${local|testnet}`

### Deposit address

1. To run on testnet, fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC and replace local with testnet.

2. To send aUSDC from the source to the destination, run:

`node scripts/test examples/deposit-address ${local|testnet} ${source-chain} ${destination-chain} ${amount}`

Deposit-address does not need deployment.

### Headers

1. To inform destination-chain of the last header of source-chain, run:

`node scripts/test examples/headers ${local|testnet} ${source-chain} ${destination-chain}`

2. To deploy the dapp, run:

`node scripts/deploy examples/headers ${local|testnet}`

### NFT linker

1. To send the NFT that was originally minted at source-chain to destination-chain, run:

`node scripts/test examples/nft-linker ${local|testnet} ${source-chain} ${destination-chain}`

You cannot send a duplicate NFT to a chain. The dapp fails when the NFT is already at the destination-chain.

2. To deploy the dapp, run:

`node scripts/deploy examples/nft-linker ${local|testnet}`

A single NFT is minted to the deployer (`0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`) on each chain.

### Nonced execution

1. To send a message from source-chain to destination-chain, run: 

`node scripts/test examples/nonced-execution ${local|testnet} ${source-chain} ${destination-chain} ${message}`

2. To deploy the dapp, run:

`node scripts/deploy examples/nonced-execution ${local|testnet}`

### Send ack

1. To send a message from source-chain to destination-chain, run:

`node scripts/test examples/send-ack ${local|testnet} ${source-chain} ${destination-chain} ${message}`

2. To deploy the dapp, run:

`node scripts/deploy examples/send-ack ${local|testnet}`

### Send token

1. To send aUSDC from the source to the destination, run:
 
`node scripts/test examples/send-token ${local|testnet} ${source-chain} ${destination-chain} ${amount}` 

2. To run on testnet, fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC and replace local with testnet. 

Deposit-address does not need deployment.

## Conclusion

xxxx


