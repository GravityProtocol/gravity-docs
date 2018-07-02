# Running the Backup Node (for Witnesses)

1\. Deploy the node on the backup machine , following instructions from [docker tutorial](https://github.com/GravityProtocol/gravity-docs/blob/master/running%20node%20with%20docker.md)

2\. Run the cli_wallet and generate the backup signing keys, private and public:
```
docker-compose exec gravity_node cli_wallet -w /var/lib/gravity/wallet.json
unlock myPassword
suggest_brain_key
```

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
