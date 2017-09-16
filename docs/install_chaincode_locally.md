# Install and Instantiate Chaincode w/Local Hyperledger Fabric

### Setup
We need some marbles dependencies in order to run the install/instantiate scripts.
Install marbles npm dependencies by navigating back to the root of the marble directory and entering these commands. 
If you already ran these commands, it's safe to run them again.

```bash
cd marbles
npm install
```

### Get Crypto Material
**Important Step!** The install and instantiate operations require an admin certificate and private key. 
If these files are not found you will be unable to run either operation.

**Choose 1 option below to create these files:**

- **Option 1:** :lollipop: Use the prebaked crypto for a locally hosted Hyperledger Fabric Network. These certificates are already created for you. So you are already done! Note that these files only work on a Fabric network built from the `fabric-samples` repo. If that is what you are using, skip to the next section.
- **Option 2:** Create the certificate and public key files manually - [instructions](https://console.bluemix.net/docs/services/blockchain/v10_application.html#generating-the-client-side-certificates)
	- You need to add the private key and signed certificate files to this folder: `<marbles root>/config/crypto/`

### Install chaincode
With that done, we need to get the chaincode onto the peer's filesystem. 
Remember chaincode defines what marbles (assets) are and has our business  logic for our marble transactions. 
For reference the marbles chaincode can be found in this directory `<marbles root>/chaincode/src/`. 
There are several files, which is fine since our script will send the directory. 

The script we will use is `install_chaincode.js` in the `scripts` folder. 
It will read in our marbles config file and the blockchain creds file. 
You can change the marbles chaincode ID or version by editing your creds file. 
Open the config file readme below if you would like to edit these files and want more information.
If you are okay with the defaults, then simply leave these files alone and run the command below.

- [Configuration and Credential File Help](./config_file.md)

Install the marbles chaincode source files with the commands below: 

```bash
cd ./scripts
node install_chaincode.js
```

**Output:**
```bash
info: Using default config file marbles_local.json
info: Loaded config file /home/slim/marbles/config/marbles_local.json
info: Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json
---------------------------------------
info: Lets install some chaincode - marbles v4
---------------------------------------
info: First we enroll
info: [fcw] Going to enroll with admin cert!  peer_urls=[grpc://localhost:7051], channel_id=mychannel, uuid=marbles-Docker Compose Network-mychannel-fabric-peer-org1, orderer_url=grpc://localhost:7050, msp_id=Org1MSP
debug: added peer grpc://localhost:7051
debug: [fcw] Successfully got enrollment marbles-Docker Compose Network-mychannel-fabric-peer-org1
---------------------------------------
info: Now we install
---------------------------------------
debug: [fcw] Installing Chaincode
debug: [fcw] Sending install req targets=[grpc.primary_user_agent=grpc-node/1.2.4, _url=grpc://localhost:7051, addr=localhost:7051, , _request_timeout=90000, , _name=null], chaincodePath=marbles, chaincodeId=marbles, chaincodeVersion=v4
info: [packager/Golang.js]: packaging GOLANG from marbles
debug: [fcw] Successfully obtained transaction endorsement
---------------------------------------
info: Install done. Errors: nope
---------------------------------------
```

### Instantiate chaincode
Next we need to instantiate the chaincode. 
This will have the peer spin up the marbles chaincode for your channel `mychannel`. 
Once this is complete we are ready to use the blockchain network to record our marble activities. 
Use the commands below:

```bash
node instantiate_chaincode.js
```

**Output:**
```
info: Using default config file marbles_local.json
info: Loaded config file /home/slim/marbles/config/marbles_local.json
info: Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json
---------------------------------------
info: Lets instantiate some chaincode - marbles v4
---------------------------------------
warn: Note: the chaincode should have been installed before running this script
info: First we enroll
info: [fcw] Going to enroll with admin cert!  peer_urls=[grpc://localhost:7051], channel_id=mychannel, uuid=marbles-Docker Compose Network-mychannel-fabric-peer-org1, orderer_url=grpc://localhost:7050, msp_id=Org1MSP
debug: added peer grpc://localhost:7051
debug: [fcw] Successfully got enrollment marbles-Docker Compose Network-mychannel-fabric-peer-org1
---------------------------------------
info: Now we instantiate
---------------------------------------
debug: [fcw] Instantiating Chaincode peer_urls=[grpc://localhost:7051], channel_id=mychannel, chaincode_id=marbles, chaincode_version=v4, cc_args=[12345], ssl-target-name-override=null, pem=null
debug: [fcw] Sending instantiate req targets=[grpc.primary_user_agent=grpc-node/1.2.4, _url=grpc://localhost:7051, addr=localhost:7051, , _request_timeout=90000, , _name=null], chaincodeId=marbles, chaincodeVersion=v4, fcn=init, args=[12345], 0=8, 1=31, 2=74, 3=112, 4=55, 5=221, 6=13, 7=88, 8=176, 9=251, 10=169, 11=29, 12=143, 13=114, 14=207, 15=208, 16=127, 17=137, 18=93, 19=58, 20=197, 21=49, 22=188, 23=12, _transaction_id=8919996c9ab114ca9fa9b731487185b1c32bafb5b148a6a731eef4419775a660
debug: [fcw] Successfully obtained transaction endorsement
debug: [fcw] Successfully ordered instantiate endorsement.
---------------------------------------
info: Instantiate done. Errors: nope
---------------------------------------
```


### Finish Up

Congrats! The network is all setup and marbles chaincode is running. 

- Continue where you left off in the [tutorial](../README.md#hostmarbles).