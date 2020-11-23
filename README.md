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
3. In the bottom left corner of your MyCrypto GUI you are going to see "Change Network" with an arrow. Click on it.
4. Now at the bottom of the column of names you will see <code>+ Add Custom Note</code>. Click it. You will a GUI pop up where you can configure this new network. In this case I called it it test net, and set it to the same chain id <code>333</code> that was used to setup the blockchain nodes above.
![Your Custom Network](setting-up-your-custom-network-testnet.png)

5. At this point if you want to replicate sending a transaction you will need to use your keystore files (they start with UTC) from your nodes you created above to open a wallet. From the Change Wallet main screen in MyCrypto select keystore file block.

![Keystore](use-mycrypto-gui-to-select-keystore-file.png)

Then click on "SELECT WALLET FILE" to unlock your keystore file. Go find your keystore file in your blockchain tooks folder that you saved everything to from part one. Use node 1 keystore.

![Keystore](use-the-keystore-file.png)

Once you open the wallet you can send a transaction from wallet 1 to wallet 2. Try to do this now by selecting the amount. Make sure you are on your custom network. If you don't have any money in any of your Ethereum accounts, you'll need to reach out for help on how to fix that. That was never made clear how exactly to get Ehtereum into the accounts to send a transaction - it was either there or it wasn't.

If there's Ethereum there go ahead and send a transaction. Every transaction will produce a hash. This hash can be entered into https://etherscan.io/ to see the status of the transaction.

