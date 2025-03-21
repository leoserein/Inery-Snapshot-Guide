## QB Snapshot
- All Snapshot  : https://snapshot.node.sarjananode.studio/
- Snapshot file : https://snapshot.node.sarjananode.studio/qb/chaindata_latest.tar.lz4

## How to Use :
#### Stop Docker
```
cd $HOME/testnet-public-tools/testnet-validator && docker compose down
```

#### Remove old chaindata
```
cd /var/lib/docker/volumes/testnet-validator_testnet-validator-node-data/_data/geth && rm -rf chaindata && mkdir -p chaindata
```

#### Download Snapshot
```
curl -L https://snapshot.node.sarjananode.studio/qb/chaindata_latest.tar.lz4 | tar -Ilz4 -xf - -C /var/lib/docker/volumes/testnet-validator_testnet-validator-node-data/_data/geth
```

#### Start Node
```
cd $HOME/testnet-public-tools/testnet-validator && docker compose up -d
```

#### Check Logs

```
cd $HOME/testnet-public-tools/testnet-validator && docker compose logs -f
```

#### Check QStats
- https://stats.qtestnet.org/
