### Guide use snapshot Nolus

## Install dependencies
```
sudo apt update
sudo apt install lz4 -y
```
## Stop Nolus node
```
sudo systemctl stop nolusd
sudo systemctl disable nolusd
nolusd tendermint unsafe-reset-all --home $HOME/.nolus --keep-addr-book
```


## Download Nolus snapshot
```
wget -O wget -O nolus-snapshot-20230307.tar.lz4 https://snapshot.nolus.trnodes.my.id/nolus/nolus-snapshot-20230307.tar.lz4 --inet4-only
lz4 -c -d nolus-snapshot-20230307.tar.lz4 | tar -x -C $HOME/.nolus
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```

## Restart Nolus node and see the log
```
sudo systemctl restart nolusd
sudo journalctl -u nolusd -f --no-hostname -o cat
```
