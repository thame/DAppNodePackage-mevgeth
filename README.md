# MEV-Geth DAppNode package

[![MEV-geth]](https://github.com/flashbots/mev-geth)

You can use this package without installing it in your DAppNode following these instructions:

## Extra options

You can edit the `docker-compose.yml` and add extra options, such as:
```
 - EXTRA_OPTS=--wsapi db,eth,net,ssh,miner,web3,personal,admin,txpool
```

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details
