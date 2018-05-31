# Updating the node (docker)

**Non-witnesses:**

1\. Enter the folder containing the node
```
cd gravity-testnet-docker
```

2\. Stop the node
```
docker-compose down
```

3\. Pull the changes from github
```
git pull origin
```

4\. Pull the new version package from hub.docker
```
docker-compose pull
```

5\. Start the node
```
docker-compose up -d
```


**Witnesses:**

To avoid missing the blocks, witnesses have to use the backup node

1\. Run the cli_wallet and generate the backup signing keys, private and public:
```
docker-compose exec gravity_node cli_wallet -w /var/lib/gravity/wallet.json
unlock myPassword
suggest_brain_key
```

2\. Deploy the backup node on the backup machine, following instructions from [docker tutorial](https://github.com/GravityProtocol/gravity-docs/blob/master/running%20node%20with%20docker.md)

3\. Edit the config.ini
```
sudo nano data/config.ini
```
Add your witness id and the backup signing keys pair
```
...
# ID of witness controlled by this node (e.g. "1.6.5", quotes are required, may specify multiple times)
witness-id = "1.6.*"
# Tuple of [PublicKey, WIF private key] (may specify multiple times)
private-key = ["ZGV...backupSigningPublicKey","5...backupSigningPrivateKey"]
...
```
4\. Restart the backup node
```
docker-compose down
docker-compose up -d
```
Make sure that your backup node have synchronized

5\. In the cli_wallet change your witness signing key to backup key
```
update_witness g1234r1234v1234z1234 "my url" ZGV...backupSigningPublicKey true
```
Make sure that block production continued from your witness

6\. Update your main node in the same way as the non-witnesses
Wait for synchronization after update

7\. Switch your witness back to its main witness key
```
update_witness g1234r1234v1234z1234 "my url" ZGV...mainSigningPublicKey true
```
Make sure that block production continued from your witness
