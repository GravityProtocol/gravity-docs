# Connecting a node to the testnet

1. Create a folder to run a testnet node and copy the application folder witness_node
```
mkdir ~/gravity_testnet
cd ~/gravity_testnet
cp -r ~/gravity-core/programs/witness_node .
cd witness_node
```

2. Run the node for the first time to create data directory
```
./witness_node --data-dir=data
```

3. Stop the node pressing Ctrl+C and open config.ini
```
nano data/config.ini
```

4. Add the seed nodes

```
...
# P2P nodes to connect to on startup (may specify multiple times)
seed-node = testnet-seed-0.gravityprotocol.org:10111
seed-node = testnet-seed-1.gravityprotocol.org:4623
seed-node = testnet-seed-2.gravityprotocol.org:4623
seed-node = testnet-seed-3.gravityprotocol.org:4623
seed-node = testnet-seed-4.gravityprotocol.org:4623
seed-node = testnet-seed-5.gravityprotocol.org:4623
seed-node = testnet-seed-6.gravityprotocol.org:4623
seed-node = testnet-seed-7.gravityprotocol.org:4623
seed-node = testnet-seed-8.gravityprotocol.org:4623
...
```

Save changes and exit

5. Run the node again
```
./witness_node --data-dir=data
```

Node will start synchronization with the network, it can take from several minutes to several hours depending on the current blockchain length
```
Chain ID is ab5071857c28ddbc872d0ca508725fa3006ea7bdfda10f707433021f570fc27e
Got block: #10000 time: 2018-04-03T03:14:35 latency: 645591253 ms from: init4  irreversible: 9797 (-203)
Got block: #20000 time: 2018-04-03T20:05:55 latency: 584914289 ms from: init1  irreversible: 19992 (-8)
Got block: #30000 time: 2018-04-04T10:06:55 latency: 534457595 ms from: init8  irreversible: 29991 (-9)
Got block: #40000 time: 2018-04-05T00:01:00 latency: 484494127 ms from: init3  irreversible: 39990 (-10)
...
```

When the node is synchronized it starts receiving new blocks in real time
```
...
Got block: #100000 time: 2018-04-08T16:28:10 latency: 166993438 ms from: init5  irreversible: 99992 (-8)
Got block: #110000 time: 2018-04-09T09:01:40 latency: 107566426 ms from: init8  irreversible: 109992 (-8)
Got block: #120000 time: 2018-04-10T01:48:35 latency: 47332734 ms from: init5  irreversible: 119992 (-8)
Got block: #127774 time: 2018-04-10T15:00:40 latency: 120 ms from: init4  irreversible: 127766 (-8)
Got block: #127775 time: 2018-04-10T15:00:45 latency: 112 ms from: init0  irreversible: 127767 (-8)
Got block: #127776 time: 2018-04-10T15:00:50 latency: 6 ms from: init9  irreversible: 127768 (-8)
Got block: #127777 time: 2018-04-10T15:01:05 latency: 123 ms from: init0  irreversible: 127769 (-8)
...
```
