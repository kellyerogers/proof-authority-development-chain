# proof-authority-development-chain
A custom development chain, with documentation for others on how to start it using the pre-configured nodes and accounts.

# How to Start the Network
1. There are two accounts for two nodes for the network with a separate datadir for each using geth.
2. Using ternminal go into, the <code>Proof-of-Authority-Development-Chain</code> directory
3. Start node 1 using the following command:
> <code>./geth --datadir node1 --mine --minerthreads 1</code>

Note: You should start to see the node run and see the this line appear <code> Starting peer-to-peer node </code> in the scrolling list in terminal.
4. Now you are ready to start node 2. Start node 2 using the following command:
> <code>./geth --datadir node2 --port 30304 --rpc --bootnodes "enode://ba768f71128c600c6dda023c719f5962c859a6aaf91281e7a0003c39739901e064b0facb2d33598f7c59d0de6f4246090425ef223f6c4578deb471380b6e7884@127.0.0.1:30303"</code>
5. You should now see both nodes producing new blocks.

# How to send/receive a transaction
1. Open My Crypto Wallet
2. You are going to need to setup a network to run the transaction on
3. In the bottom left corner of your MyCrypto GUI you are going to see "Change Network" with an arrow.
