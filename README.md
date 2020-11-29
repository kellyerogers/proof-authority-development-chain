# proof-authority-development-chain
A custom development chain, with documentation for others on how to start it using the pre-configured nodes and accounts.

# How to Start the Network
The network setup for this blockchain is named thissucks (a name chosen after 11 previous attempts to spin up a working blockchain that I could successfully run a transaction on; of course this time, it worked!). You can see all the information regarding the setup of this network below for reference.
<code>
Please specify a network name to administer (no spaces, hyphens or capital letters please)
> thissucks

Sweet, you can set this via --network=thissucks next time!

INFO [11-25|22:34:06.898] Administering Ethereum network           name=thissucks
WARN [11-25|22:34:06.901] No previous configurations found         path=/Users/kellyerogers/.puppeth/thissucks

What would you like to do? (default = stats)
 1. Show network stats
 2. Configure new genesis
 3. Track new remote server
 4. Deploy network components
> 2

What would you like to do? (default = create)
 1. Create new genesis from scratch
 2. Import already existing genesis
> 1

Which consensus engine to use? (default = clique)
 1. Ethash - proof-of-work
 2. Clique - proof-of-authority
> 2

How many seconds should blocks take? (default = 15)
> 

Which accounts are allowed to seal? (mandatory at least one)
> 0xB23A872E68A9Af470ccB41099310FC1C09F2a268
> 0xD13f6209A3e0c52Fc49f945c3587B145FDeEE4fC
> 0x

Which accounts should be pre-funded? (advisable at least one)
> 0xB23A872E68A9Af470ccB41099310FC1C09F2a268
> 0xD13f6209A3e0c52Fc49f945c3587B145FDeEE4fC
> 0x

Should the precompile-addresses (0x1 .. 0xff) be pre-funded with 1 wei? (advisable yes)
> no

Specify your chain/network ID if you want an explicit one (default = random)
> 888
INFO [11-25|22:36:10.312] Configured new genesis block 

What would you like to do? (default = stats)
 1. Show network stats
 2. Manage existing genesis
 3. Track new remote server
 4. Deploy network components
> 2

 1. Modify existing configurations
 2. Export genesis configurations
 3. Remove genesis configuration
> 2

Which folder to save the genesis specs into? (default = current)
  Will create thissucks.json, thissucks-aleth.json, thissucks-harmony.json, thissucks-parity.json
> 
INFO [11-25|22:36:27.544] Saved native genesis chain spec          path=thissucks.json
ERROR[11-25|22:36:27.549] Failed to create Aleth chain spec        err="unsupported consensus engine"
ERROR[11-25|22:36:27.550] Failed to create Parity chain spec       err="unsupported consensus engine"
INFO [11-25|22:36:27.551] Saved genesis chain spec                 client=harmony path=thissucks-harmony.json

What would you like to do? (default = stats)
 1. Show network stats
 2. Manage existing genesis
 3. Track new remote server
 4. Deploy network components
> ^C
</code>

There are two accounts for two nodes, that are in the network with a separate datadir for each, using geth.
- node1z
- node2z

## Steps for starting the chain
1. Using ternminal, go into, the <code>Blockchain-Tools</code> directory in this repository.

2. To kickoff node1z, go ahead and use the following command:
<code>./geth --networkid 888 --datadir node1z --port 30310 --password password.txt --unlock "0xB23A872E68A9Af470ccB41099310FC1C09F2a268" --mine --rpc --miner.threads 1 --allow-insecure-unlock</code>

3. To kickoff node2z, go ahead and use the following commend:
<code>./geth --networkid 888 --datadir node2z --unlock "0xD13f6209A3e0c52Fc49f945c3587B145FDeEE4fC" --mine --port 30311 --password password.txt --bootnodes "enode://5876c84d1e0b5181f4e17a7ec7ae77084cc65dbe91141c3ad6aa397e14c1002e75d2d3f1b0c642eeecd6f040f3c266525479312bf9c7246bbbba1fa79d4cbb0e@127.0.0.1:30310"</code>

Note: In both instances above, you should start to see the node run, and see the this line appear <code> Starting peer-to-peer node </code> in the scrolling list in terminal.

4. You should now see both nodes producing new blocks. Congrats you are now running both nodes on the thissucks network. 

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

