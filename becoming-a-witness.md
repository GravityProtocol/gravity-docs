# Becoming a witness

1. Сreate an account in the [web wallet](https://wallet.gravityprotocol.org) and copy the account name and the private active key from there

2. Pull the last docker build from hub.docker.com 
([see this tutorial](https://github.com/GravityProtocol/gravity-docs/blob/master/running%20node%20with%20docker.md))

3. Run the docker package in detached mode
```
docker-compose up -d
```
You can always look at its latest logs
```
docker-compose logs --tail 100
```
And stop it, if needed
```
docker-compose stop
```

4. Run the command line wallet connected to your node to create a witness
```
docker-compose exec gravity_node cli_wallet -w /var/lib/gravity/wallet.json
set_password somehardpassword
unlock somehardpassword
import_key "accountName like g9320b3400s1180y4450" privateKeyStartingWithZGV
upgrade_account "accountName like g9320b3400s1180y4450" true
create_witness "accountName like g9320b3400s1180y4450" "https://<url-to-proposal>" true
get_witness ""accountName like g9320b3400s1180y4450"
```
Copy the witness id and block_signing_key from get_witness  
Get the private signing key
```
get_private_key yourPublicSigningKey
```

5. Exit the cli_wallet with Ctrl+C, stop the node with ```docker-compose stop```, and open config.ini
```
nano data/config.ini
```
Add the witness id and the public and private signing keys
```
...
# ID of witness controlled by this node (e.g. "1.6.5", quotes are required, may specify multiple times)
witness-id = "1.6.*"

# Tuple of [PublicKey, WIF private key] (may specify multiple times)
private-key = ["ZGV...", "5..."]
...
```
Save the changes and exit

6. Run the node again
```
docker-compose up -d
```
7. Vote for yourself in the web wallet  
If your vote is not enough, ask others to vote for you  
If your witness gets enough votes, your node will start producing blocks  






