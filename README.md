# fabric-blockchain-explorer
Note: You must complete Lab #1, Lab #2 and Lab #3 first which will include the required binary files.

Important: This requires the test network to be up and running with some transactions submitted.

## Install and make sure you have a private admin key available for the blockchain explorer

Log into Ubuntu and issue the following commands
```
cd ~
```
```
git clone https://github.com/lley154/fabric-blockchain-explorer.git
```
```
cd fabric-blockchain-explorer/
```
```
mkdir wallet
```
```
sudo cp -r ../fabric-samples/test-network/organizations/ . ## copying crypto material, but only do this for a lab env
```
```
sudo chmod a+rwx -R organizations ## only required for lab env
```
Set the paths in the .env file to point to your home directory
```
echo "FABRIC_CRYPTO_PATH=$HOME/fabric-blockchain-explorer/organizations" >> .env
echo "WALLET_PATH=$HOME/fabric-blockchain-explorer/wallet" >> .env  
```
Copy the generated private key for admin in org1 to priv_sk

```
cd ~/fabric-blockchain-explorer/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/keystore/
```
```
sudo cp *_sk priv_sk
```
```
cd ~/fabric-blockchain-explorer
```
Now bring up docker images for postgresDB and explorer UI
```
docker compose up
```
The explorer (and postgressDB) docker images should run and there should not be any errors in the logging output.  You should see near the end of the output something like:
```
...
explorer.mynetwork.com      | [2024-02-13T15:34:54.340] [INFO] main - Please open web browser to access ：http://localhost:8080/
explorer.mynetwork.com      | [2024-02-13T15:34:54.341] [INFO] main - pid is 19
```


Next, log into the server using a new terminal window to set up port forwarding to access the blockchain explorer UI using port 8080.

ssh usage
```
ssh -L local_port:destination_server_ip:remote_port ssh_server_hostname
```
For example
```
ssh -i lab2.pem -L 8080:ec2-54-91-100-220.compute-1.amazonaws.com:8080 ubuntu@ec2-54-91-100-220.compute-1.amazonaws.com
```
Now use a browser on your local machine and access the Hyperledger Blockchain Explorer UI
```
http://localhost:8080/
user: exploreradmin
pass: exploreradminpw
```

Response times may be slow, so please wait for pages or links to load. A browser page refresh may also be required. You will see logging info messages when you try to access the explorer. If you encounter errors, please continue to submit with screen shots of the errors to receive full marks.

To shutdown the block exporer, use 'control c' command to stop the block exprorer process.



