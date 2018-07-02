# Resyncing the node

## Witnesses:

**1\. To avoid missing the blocks, witnesses have to use the [backup node](https://github.com/GravityProtocol/gravity-docs/blob/master/running-backup-node.md)**  
Make sure that your backup node is running.

**2\. In the cli_wallet change your witness signing key to backup key**
```
update_witness g1234r1234v1234z1234 "my url" ZGV...backupSigningPublicKey true
```
Make sure that block production continued from your witness

**3\. Restart the main node**  
docker:
```
docker-compose down
docker-compose up -d
```
without docker:
```
Ctrl+C
./witness_node --data-dir=data --resync-blockchain
```
Wait for synchronization after update

**4\. Switch your witness back to its main signing key**
```
update_witness g1234r1234v1234z1234 "my url" ZGV...mainSigningPublicKey true
```
Make sure that block production continued from your witness

**5\. Restart the backup node the same way as the main**
  
  
  
## Non-witnesses:

**1\. Restart the node**  
docker:
```
docker-compose down
docker-compose up -d
```
without docker:
```
Ctrl+C
./witness_node --data-dir=data --resync-blockchain
```
Wait for synchronization after update
