# Proof of Authority Development Chain


## Summary
____

This document contains all the required dependent binaries and wallet service information along with usage instructions 
for "rnet" private POA testnet creates. "rnet" private chain was setup by me to facilitate transactions between accounts.
Some of the key features of this private blockchain include

1. Available balance check for sealed node accounts
2. Creating transaction between node accounts
3. Checking transaction status
  
## Dependencies:

### 1. git-bash
For commandline execution

### 2. MyCrypto Desktop App
It is a free, open-source, client-side interface that allows you to interact directly with the blockchain to manage ethereum wallets and make transactions in the blockchain. 

### 3. Go Ethereum or geth toolchain
geth tool chain can be downloaded as a gzip file which will be used to setting up the private blockchain.


## About rnet chain

rnet private blockchain has been setup using geth tool. This blockchain is based on proof authority or Clique algorithm. Inorder to setup the private blockchain, two new accounts have been created using "geth new account--datadir node1/node2" commandline and password has been created for each of the node. The initial genesis file has been created using puppeth tool that comes with geth toolset where the above created accounts have been used as sealer accounts. The genesis file have been used to initialize two nodes using geth init command(eg: geth init --datadir node1/node2 rnet.json).

* After inititialization of nodes, one node1 has been used as the miner using geth command "./geth --datadir node1 --unlock "<node1 account address>" --mine --rpc --allow-insecure-unlock". mine flag enables mining and unlock flag unlocks the node1 account.

* A second  bootstrap node has been started by setting up  a different peer port  and by using the first node's enode address as the bootnode flag. The geth commandline params used for second node is "./geth --datadir node2 --unlock "0x3e55f11499F65b7D529F433aC86D0749C4D33160" --mine --port 30304 --bootnodes "<firstnode enode>" --ipcdisable --allow-insecure-unlock --syncmode "fast"
 
 * The blockchains external end poind details has been captured which is http://127.0.0.1:8545 which is used to by mycrypto wallet to interact with blockchain

 ### Mycrypto to rnet blockchain connection
 We have used mycrypto wallet to test our private blockchains. Below is the steps need to be followed to connect to blockchain from mycrypto wallet

 * On myCrypto wallet GUI go to change network select "Add custom Node" 
 * On setup your custom node dialogue provide node name as rnet select Network as custom currency as ETH chainID as 777(can be found in rnet) and URL as http://127.0.0.1:8545. Then click on save and use custom node.
 * After successful connection the balance(from mining) should show on the right.
 
 ### Sending transaction from node1 account to node2 account
* Import the keystore file from the node1/keystore directory into MyCrypto. This will import the private key.
* Copy to address as the node2 account address and select the amount of ETH to be transferred.
* Click send. On success copy transaction hash and go to mycrypto wallet "TX Status" section and to check the transaction details like status, blocknumber, hash etc.
