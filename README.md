# Axelar Local Development Example dApps

## Introduction

This repo provides the code for several example dApps in the [Axelar Local Development Environment](https://github.com/axelarnetwork/axelar-local-dev). It contains both the JavaScript and the smart contract code (.sol files) for each example. To try them out:

- Set up your system.
- Test and deploy each example.

Note: You may see example folders in this repo that are not described below. They are either placeholders for future apps, such as the `temp` folder, or they are dApps in progress and we'll add a description when they're finished.

## Setup

1. You'll need to have node.js installed to run network dApps. To make sure you have it installed, run `node -v`. If no version is returned, run
`npm update && npm install`.

2. To clone this repo, run `git clone https://github.com/axelarnetwork/axelar-local-gmp-examples.git`. 
3. To make sure all contracts are compiled, run `npm run build`. 

\[Editor: I get "Missing script 'build' " error]

4. To run a local node, open a separate terminal and run `node scripts/createLocal`. You’ll need to have this node running to deploy the dApps. 

\[Editor: 

1. Do I have the introductory phrase above right: we're establishing the user as a node and running a daemon in the background, yes? 

2. When I run this code, I get "Cannot find module" error. When I add axelar-local-gmp-examples to the path (i.e., run: `node axelar-local-gmp-examples/scripts/createLocal`), I get "Cannot find @axelar-network/axelar-local-dev module" error]

5. Make sure that the address we use for examples is funded on all five supported testnets. 

\[Editor: What are the five supported testnets? Will that be clear when I get the above running?]

   a. Run `node/printBalances`. 

\[Editor: Suspicioua syntax. Do you mean `node axelar-local-gmp-examples/scripts/checkBalances`? If not, what?]

   b. Look for `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`, the address we use to deploy and run all examples.

## Test and deploy each example

For each example, enter:

- `local` or `testnet` (for both the test and the deploy steps) 

\[Editor: Should they run local for everything, except `deposit-address` and `send-token`? If not, what are the criteria for choosing?]

- `source-chain` and `destination-chain` 

\[Editor: Such as? What's the correct way to identify each? Explained somewhere?]

- variables such as `message`, `amount`, and `account` 

\[Editor: What is the expected syntax: message: "message"?, amount: whole numbers?, account: how are accounts identified..."string of numbers"?]

and run the test and deploy.

### Call contract

1. To relay a message from source-chain to destination-chain, run:

`node scripts/test examples/call-contract [<local|testnet>] [<source-chain>] [<destination-chain>] [<message>]`

2. To share your code cross-chain, run `yarn call-contract`. 

\[Editor: Is that the right characterizzation of what yarn is doing? If not, what is it doing and why don't we need one for any of the others?]

3. To deploy the dApp, run::

`node scripts/deploy examples/call-contract [<local|testnet>]`

### Call contract with token

1. To send aUSDC from source-chain to destination-chain and distribute it equally among all accounts specified, run:

`node scripts/test examples/call-contract-with-token [<local|testnet>] [<source-chain>] [<destination-chain>] [<amount>] [<account>] [<account2>]...`

2. To deploy the dApp, run:

`node scripts/deploy examples/call-contract-with-token [<local|testnet>]`

### Cross chain token

1. To mint some token at source-chain and have it sent to destination-chain, run:

`node scripts/test examples/cross-chain-token [<local|testnet>] [<source-chain>] [<destination-chain>] [<amount>]`

2. To deploy the dApp, run:

`node scripts/deploy examples/cross-chain-token [<local|testnet>]`

### Deposit address

1. To run on testnet, fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC and replace local with testnet.

2. To send aUSDC from the source to the destination, run:

`node scripts/test examples/deposit-address [<local|testnet>] [<source-chain>] [<destination-chain>] [<amount>]`

`Deposit-address` is a simple send transaction. There is no smart contract to deploy.

### Headers

1. To inform destination-chain of the last header of source-chain, run:

`node scripts/test examples/headers [<local|testnet>] [<source-chain>] [<destination-chain>]`

2. To deploy the dApp, run:

`node scripts/deploy examples/headers [<local|testnet>]`

### NFT linker

1. To send the NFT that was originally minted at source-chain to destination-chain, run:

`node scripts/test examples/nft-linker [<local|testnet>] [<source-chain>] [<destination-chain>]`

You cannot send a duplicate NFT to a chain. The dApp fails when the NFT is already at the destination-chain.

2. To deploy the dApp, run:

`node scripts/deploy examples/nft-linker [<local|testnet>]`

A single NFT is minted to the deployer (`0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`) on each chain.

### Nonced execution

1. To send a message from source-chain to destination-chain, run: 

`node scripts/test examples/nonced-execution [<local|testnet>] [<source-chain>] [<destination-chain>] [<message>]`

2. To deploy the dApp, run:

`node scripts/deploy examples/nonced-execution [<local|testnet>]`

### Send ack

1. To send a message from source-chain to destination-chain, run:

`node scripts/test examples/send-ack [<local|testnet>] [<source-chain>] [<destination-chain>] [<message>]`

2. To deploy the dApp, run:

`node scripts/deploy examples/send-ack [<local|testnet>]`

### Send token

1. To send aUSDC from the source to the destination, run:
 
`node scripts/test examples/send-token [<local|testnet>] [<source-chain>] [<destination-chain>] [<amount>]` 

2. To run on testnet, fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC and replace local with testnet. 

`Send-token` is a simple send transaction. There is no smart contract to deploy.

## Conclusion

With each example that you try, look for confirmation in the terminal output.


