# Host Marbles Locally:

### <a name="runlocal"></a>Run Marbles
 Finally lets install marble's npm dependencies.

1. Open a command prompt/terminal and navigate to the marbles directory.
1. In the command prompt/terminal type:
	
		> cd marbles
		> npm install gulp -g
		> npm install

1. Next up, pick the command that matches your setup. This will run marbles.

- **Option 1:** :lollipop: If you are using a local network use this command:
	> gulp marbles_local


- **Option 2:** If you are using a bluemix network, use this command:
	> gulp marbles_tls

1. If all goes well you should see this message in the console:

- **Output:**
```
[19:57:11] Using gulpfile ~/marbles/gulpfile.js
[19:57:11] Starting 'env_local'...
[19:57:11] Finished 'env_local' after 103 μs
[19:57:11] Starting 'build-sass'...
[19:57:11] Finished 'build-sass' after 12 ms
[19:57:11] Starting 'watch-sass'...
[19:57:11] Finished 'watch-sass' after 22 ms
[19:57:11] Starting 'watch-server'...
[19:57:11] Finished 'watch-server' after 9.53 ms
[19:57:11] Starting 'server'...
info: Checking credentials file is done
info: Loaded config file /home/slim/marbles/config/marbles_local.json
info: Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json
[19:57:12] Starting 'build-sass'...
[19:57:12] Finished 'build-sass' after 5.88 ms
info: Loaded config file /home/slim/marbles/config/marbles_local.json
info: Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json
debug: cache busting hash js 1505563033127 css 1505563033127
Loaded config file /home/slim/marbles/config/marbles_local.json
Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json


----------------------------------- Server Up - localhost:3001 -----------------------------------
------------------------------------------ Websocket Up ------------------------------------------


info: Using settings in marbles_local.json to see if we have launch marbles before...
info: [fcw] Going to enroll peer_urls=[grpc://localhost:7051], channel_id=mychannel, uuid=marbles-Docker Compose Network-mychannel-fabric-peer-org1, ca_url=http://localhost:7054, orderer_url=grpc://localhost:7050, enroll_id=PeerAdmin, enroll_secret=-, msp_id=Org1MSP, kvs_path=/home/slim/marbles/config/crypto/prebaked/
info: [fcw] Successfully loaded enrollment from persistence
debug: added peer grpc://localhost:7051
debug: [fcw] Successfully got enrollment marbles-Docker Compose Network-mychannel-fabric-peer-org1
info: Success enrolling admin
debug: Checking if chaincode is already instantiated or not

info: Checking for chaincode...
debug: [fcw] Querying Chaincode: read()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read, args=[selftest], txId=null
debug: [fcw] Peer Query Response - len: 5 type: number
debug: [fcw] Successful query transaction.

----------------------------- Chaincode found on channel "mychannel" -----------------------------


info: Checking chaincode and ui compatibility...
debug: [fcw] Querying Chaincode: read()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read, args=[marbles_ui], txId=null
warn: [fcw] warning - query resp is not json, might be okay: string 4.0.0
debug: [fcw] Successful query transaction.
info: Chaincode version is good
info: Checking ledger for marble owners listed in the config file

info: Fetching EVERYTHING...
debug: [fcw] Querying Chaincode: read_everything()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read_everything, args=[], txId=null
debug: [fcw] Peer Query Response - len: 30 type: object
debug: [fcw] Successful query transaction.
debug: Looking for marble owner: amy
debug: Did not find marble username: amy
info: We need to make marble owners

info: Detected that we have NOT launched successfully yet
debug: Open your browser to http://localhost:3001 and login as "admin" to initiate startup
```

* Go to your browser at the url specified in the console and login. You do not need to enter a password or change the prefilled username of `admin`.

![](/doc_images/local-login.png)
	

**Next the set up panel should pop up. Ideally it will walk itself through the 4 stages of initial setup.**
	
* 1 Check Configuration Files: 
	* The first step was to check your config JSON files for easy to make mistakes. 
	* The file that was checked can be found in /config/marbles_local.json.

![](/doc_images/step1.png)

* 2 Enrolling Admin: 
	* Next up, we attempted to enroll you as your company's admin. 
	* This step contacted your Certificate Authority (CA) and fed it the enrollID and enrollSecret from your creds file. 

![](/doc_images/step2.png)
		
* 3 Finding Chaincode: 
	* Now we needed to locate the chaincode on your channel. 
	* Your creds file says to check the channel mychannel  for the chaincode named marbles.

![](/doc_images/step3.png)

* 4 Create Assets: 
	* Almost there! As a marbles trading company you may bring new marble owners onboard. 
	* These marble owners represent your user base. This step will create the marble owners and 3 marbles per owner.

![](/doc_images/step4.png)
        


* Your marbles application is ready to use!

![](/doc_images/step5.png)

**Final result:**

```
------------------------------------------ All Done ------------------------------------------

debug: [ws] broadcasting to clients.  1 app_state
debug: [fcw] Querying Channel Stats

info: New block detected! 6 low=6, high=0, unsigned=true, currentBlockHash=861220013062696518000000460086020021044905800009100020009805588000000078578009604809411900005968270, previousBlockHash=861220013062696518000000460086020021044905800009100020009805588000000078578009604809411900005968270
debug: [checking] there are new things, sending to all clients
debug: [ws] broadcasting to clients.  1 block

info: Fetching EVERYTHING...
debug: [fcw] Querying Chaincode: read_everything()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read_everything, args=[], txId=null
debug: [fcw] Peer Query Response - len: 1769 type: object
debug: [fcw] Successful query transaction.

debug: [checking] number of owners: 3
debug: [checking] number of marbles: 9
debug: [checking] there are new things, sending to all clients
debug: [ws] broadcasting to clients.  1 everything

```
		
* Marbles is all setup! Now [continue the tutorial](../README.md#use).

* Rerun Marbles

    > gulp marbles_local	  
    
**Output:**
```
[21:39:13] Using gulpfile ~/marbles/gulpfile.js
[21:39:13] Starting 'env_local'...
[21:39:13] Finished 'env_local' after 117 μs
[21:39:13] Starting 'build-sass'...
[21:39:13] Finished 'build-sass' after 19 ms
[21:39:13] Starting 'watch-sass'...
[21:39:13] Finished 'watch-sass' after 20 ms
[21:39:13] Starting 'watch-server'...
[21:39:13] Finished 'watch-server' after 13 ms
[21:39:13] Starting 'server'...
info: Checking credentials file is done
info: Loaded config file /home/slim/marbles/config/marbles_local.json
info: Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json
info: Loaded config file /home/slim/marbles/config/marbles_local.json
info: Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json
debug: cache busting hash js 1505569154658 css 1505569154658
Loaded config file /home/slim/marbles/config/marbles_local.json
Loaded creds file /home/slim/marbles/config/blockchain_creds_local.json


----------------------------------- Server Up - localhost:3001 -----------------------------------
------------------------------------------ Websocket Up ------------------------------------------


info: Using settings in marbles_local.json to see if we have launch marbles before...
info: [fcw] Going to enroll peer_urls=[grpc://localhost:7051], channel_id=mychannel, uuid=marbles-Docker Compose Network-mychannel-fabric-peer-org1, ca_url=http://localhost:7054, orderer_url=grpc://localhost:7050, enroll_id=PeerAdmin, enroll_secret=-, msp_id=Org1MSP, kvs_path=/home/slim/marbles/config/crypto/prebaked/
info: [fcw] Successfully loaded enrollment from persistence
debug: added peer grpc://localhost:7051
debug: [fcw] Successfully got enrollment marbles-Docker Compose Network-mychannel-fabric-peer-org1
info: Success enrolling admin
debug: Checking if chaincode is already instantiated or not

info: Checking for chaincode...
debug: [fcw] Querying Chaincode: read()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read, args=[selftest], txId=null
debug: [fcw] Peer Query Response - len: 5 type: number
debug: [fcw] Successful query transaction.

----------------------------- Chaincode found on channel "mychannel" -----------------------------


info: Checking chaincode and ui compatibility...
debug: [fcw] Querying Chaincode: read()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read, args=[marbles_ui], txId=null
warn: [fcw] warning - query resp is not json, might be okay: string 4.0.0
debug: [fcw] Successful query transaction.
info: Chaincode version is good
info: Checking ledger for marble owners listed in the config file

info: Fetching EVERYTHING...
debug: [fcw] Querying Chaincode: read_everything()
debug: [fcw] Sending query req: chaincodeId=marbles, fcn=read_everything, args=[], txId=null
debug: [fcw] Peer Query Response - len: 1769 type: object
debug: [fcw] Successful query transaction.
debug: Looking for marble owner: amy
debug: Looking for marble owner: alice
debug: Looking for marble owner: ava
info: Everything is in place
debug: Detected that we have launched successfully before
debug: Welcome back - Initiating start up

```
