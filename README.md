# Axelar Local Development Example dApps

## Introduction

This repo provides the code for several example dApps in the [Axelar Local Development Environment](https://github.com/axelarnetwork/axelar-local-dev). It contains both the JavaScript and the smart contract code (.sol files) for each example. To try them out:

- Set up your system.
- Deploy each example to your emulated EVM chains and test them locally. 

\[Editor: I see from the Getting started that they are deploying virtually first, so I just changed the steps around. Correct?]

Note: You may see example folders in this repo that are not described below. They are either placeholders for future apps, such as the `temp` folder, or they are dApps in progress and we'll add a description when they're finished.

## Setup

1. You'll need to have node.js installed to run network dApps. To make sure you have it installed, run `node -v`. If no version is returned, run
`npm update && npm install`.

2. Clone the repo with `git clone https://github.com/axelarnetwork/axelar-local-gmp-examples.git` and `cd axelar-local-gmp-examples`. 

\[Editor: Admittedly, the above could get old if it was repeated ad infinitum, but maybe it could be stated somewhere early in the doc.]

3. To make sure all contracts are compiled, run `npm run build`. 

\[Editor: I get "rm -rf build && waffle....sh: waffle command not found"]

4. To run a local node, open a separate terminal and run `node scripts/createLocal`. You’ll need to have this node running to deploy the dApps. 

\[Editor: 

- Do I have the introductory phrase above right ("To run a local node"): we're establishing the user as a node and running a daemon in the background, yes? 

- When I run this code, I get "Cannot find module" error. When I add axelar-local-gmp-examples to the path (i.e., run: `node axelar-local-gmp-examples/scripts/createLocal`), I get "Cannot find @axelar-network/axelar-local-dev module" error]

5. To make sure that the address we use for examples is funded on all five supported testnets: 

\[Editor: What are the five supported testnets? Will that be clear when I get the above running?]

   a. Run `node/printBalances`. 

\[Editor: Suspicioua syntax. Do you mean `node scripts/checkBalances`? If not, what?]

   b. Look for `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`, the address we use to deploy and run all examples.

## Deploy and test each example

For each example, enter:

- `local` or `testnet` (for both the test and the deploy steps) 

\[Editor: Should they run local for everything, except `deposit-address` and `send-token`? (If so, I could enter for them and point out to use testnet only for transactions.) If not, what are the criteria for choosing? Is there a default?]

- `source-chain` and `destination-chain` 

\[Editor: Such as? What's the correct way to identify each? Explained somewhere? What are the defaults?]

- variables such as `message`, `amount`, and `account` 

\[Editor: What is the expected syntax: message: "message"?, amount: whole numbers?, account: how are accounts identified..."string of numbers"? What are the defaults?]

\[Editor: In regard to this phrase: "All params are optional and have default values and can be ommited." How can you relay a message without a message, source, or destination? These must be required. I think the writer means it in the sense that it's optional for the user to enter a value bc there are defaults. In API, the convention is to call variables with default values "required". Please confirm and I'll find a way to reword this.]

and run the test and deploy.

### Call contract

This dApp relays a message from source-chain to destination-chain.

1. To deploy the dApp, run::

`node scripts/deploy examples/call-contract [<local|testnet>]`

2. To test it, run:

`node scripts/test examples/call-contract [<local|testnet>] [<source-chain>] [<destination-chain>] [<message>]`

3. To share your code cross-chain, run `yarn call-contract`. 

\[Editor: Is that the right characterizzation of what `yarn` is doing? If not, what is it doing and why don't we need one for any of the others? End of questions.]

### Call contract with token

This dApp sends aUSDC from source-chain to destination-chain and distributes it equally among all accounts specified.

1. To deploy the dApp, run:

`node scripts/deploy examples/call-contract-with-token [<local|testnet>]`

2. To test it, run:

`node scripts/test examples/call-contract-with-token [<local|testnet>] [<source-chain>] [<destination-chain>] [<amount>] [<account>] [<account2>]...`

### Cross chain token

This dApp mints some token at source-chain and has it sent to destination-chain.

1. To deploy the dApp, run:

`node scripts/deploy examples/cross-chain-token [<local|testnet>]`

2. To test it, run:

`node scripts/test examples/cross-chain-token [<local|testnet>] [<source-chain>] [<destination-chain>] [<amount>]`

### Deposit address

This dApp sends aUSDC from source-chain to destination-chain. Run it on testnet. To test it:

1. Fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC.

2. Run:

`node scripts/test examples/deposit-address [<testnet>] [<source-chain>] [<destination-chain>] [<amount>]`

Deposit-address is a simple send transaction. There is no smart contract to deploy.

### Headers

This dApp informs destination-chain of the last header of source-chain.

1. To deploy the dApp, run:

`node scripts/deploy examples/headers [<local|testnet>]`

2. To test it, run:

`node scripts/test examples/headers [<local|testnet>] [<source-chain>] [<destination-chain>]`

### NFT linker

This dApp sends the NFT that was originally minted at source-chain to destination-chain.

1. To deploy the dApp, run:

`node scripts/deploy examples/nft-linker [<local|testnet>]`

A single NFT is minted to the deployer (`0xBa86A5719722B02a5D5e388999C25f3333c7A9fb`) on each chain.

2. To test it, run:

`node scripts/test examples/nft-linker [<local|testnet>] [<source-chain>] [<destination-chain>]`

You cannot send a duplicate NFT to a chain. The dApp fails when the NFT is already at the destination-chain.

### Nonced execution

This dApp sends a message from source-chain to destination-chain.

1. To deploy the dApp, run:

`node scripts/deploy examples/nonced-execution [<local|testnet>]`
 
2. To test it, run: 

`node scripts/test examples/nonced-execution [<local|testnet>] [<source-chain>] [<destination-chain>] [<message>]`

### Send ack

This dApp sends a message from source-chain to destination-chain.

1. To deploy the dApp, run:

`node scripts/deploy examples/send-ack [<local|testnet>]`

2. To tst it, run:

`node scripts/test examples/send-ack [<local|testnet>] [<source-chain>] [<destination-chain>] [<message>]`

### Send token

This dApp sends aUSDC from the source to the destination. Run it on testnet. To test it:

1. Fund `0xBa86A5719722B02a5D5e388999C25f3333c7A9fb` with aUSDC.

2. Run:
 
`node scripts/test examples/send-token [<testnet>] [<source-chain>] [<destination-chain>] [<amount>]`

Send-token is a simple send transaction. There is no smart contract to deploy.

## Conclusion

With each example that you try, look for confirmation in the terminal output.


