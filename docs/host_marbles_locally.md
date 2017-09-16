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

1. Go to your browser at the url specified in the console and login. You do not need to enter a password or change the prefilled username of `admin`.

![](/doc_images/local-login.png)
	

1. Next the set up panel should pop up. Ideally it will walk itself through the 4 stages of initial setup.
	
	1. Check Configuration Files: The first step was to check your config JSON files for easy to make mistakes. The file that was checked can be found in /config/marbles_local.json.

![Image of ellie](/doc_images/step1.png)

	1. Enrolling Admin: Next up, we attempted to enroll you as your company's admin. This step contacted your Certificate Authority (CA) and fed it the enrollID and enrollSecret from your creds file. 

![Image of ellie](/doc_images/step2.png)
		
	1. Finding Chaincode: Now we needed to locate the chaincode on your channel. Your creds file says to check the channel mychannel  for the chaincode named marbles.

![Image of ellie](/doc_images/step3.png)

	1. Create Assets:- Almost there! As a marbles trading company you may bring new marble owners onboard. These marble owners represent your user base. This step will create the marble owners and 3 marbles per owner.

![Image of ellie](/doc_images/step4.png)
        


1. Your marbles application is ready to use!

![Image of ellie](/doc_images/step5.png)
		
1. Marbles is all setup! Now [continue the tutorial](../README.md#use).
