# ETH-Testnet-Blockchain
Ethereum testnet blockchain using Puppeth and Geth

## Overview ##
In order to set up a testnet using the files in this repo, you will need to use the following skills/tools:

- Puppeth, to generate your genesis block.

- Geth, a command-line tool, to create keys, initialize nodes, and connect the nodes together.

- The Clique Proof of Authority (PoA) consensus algorithm.

- MyCrypto wallet and custom network configuration.

## Create the Blockchain ##
Create accounts for two (or more) nodes for the network with a separate datadir for each using geth.

Run puppeth, name your network, and select the option to configure a new genesis block.

Choose the Clique (Proof of Authority) consensus algorithm.

Paste both account addresses from the first step one at a time into the list of accounts to seal.

Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.

You can choose no for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.

Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.

Export genesis configurations. This will fail to create two of the files, but you only need poachain.json. You can delete the poachain-harmony.json file.

Initialize each node with the new poachain.json with geth.

Run the first node, unlock the account, enable mining, and the RPC flag. Only one node needs RPC enabled.

Set a different peer port for the second node and use the first node's enode address as the bootnode flag. Be sure to unlock the account and enable mining on the second node.

You should now see both nodes producing new blocks, congratulations!

## Send a Test Transaction ##
Use the MyCrypto GUI wallet to connect to the node with the exposed RPC port.

You will need to use a custom network, and include the chain ID, and use ETH as the currency.

Import the keystore file from the node1/keystore directory into MyCrypto. This will import the private key.

Send a transaction from the node1 account to the node2 account.

Copy the transaction hash and paste it into the "TX Status" section of the app, or click "TX Status" in the popup.

Celebrate, you just created a blockchain and sent a transaction!