# Estuary

> An experimental ipfs node

## Building

Requirements:
- go (1.15 or higher)
- [jq](https://stedolan.github.io/jq/)
- [hwloc](https://www.open-mpi.org/projects/hwloc/)
- opencl

1. Run `make clean all` inside the estuary directory

## Running

To run locally in a 'dev' environment, first run:
```
./estuary setup
```

Save the auth token that this outputs, you will need it for interacting with
and controlling the node.

NOTE: if you want to use a different database than a sqlite instance stored in your local directory, you will need to configure that with the `--database` flag, passed before the setup command: `./estuary --database=XXXXX setup`

Once you have the setup complete, choose an appropriate directory for estuary to keep its data, and use it as your datadir flag when running estuary.
You will also need to tell estuary where it can access a lotus gateway api, we recommend using:
```
export FULLNODE_API_INFO=wss://api.chain.love
```

Then run:

```
./estuary --datadir=/path/to/storage --database=IF-YOU-NEED-THIS --logging
```

## Systemd

The Makefile has a target that will install a generic but workable systemd service for estuary.

Run `make install-estuary-service` on the machine you wish to run estuary on.

Make sure to follow the instructions output by the `make` command as configuration is required before the service can run succesfully.

