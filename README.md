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
cd $HOME/.nolus
rm -rf data
wget -O wget -O nolus-snapshot-20230307.tar.lz4 https://snapshot.nolus.trnodes.my.id/nolus/nolus-snapshot-20230307.tar.lz4 --inet4-only | lz4 -c -d | tar -x -C $HOME/.nolus
```

## Restart Nolus node and see the log
```
sudo systemctl restart nolusd
sudo journalctl -u nolusd -f --no-hostname -o cat
```
