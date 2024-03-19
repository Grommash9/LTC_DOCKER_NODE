# Litecoin Node Docker Container

This Docker container runs a Litecoin node, allowing you to participate in the Litecoin network.

## Building the Container

To build the container, run the following command in the directory containing the Dockerfile:

```
docker build -t litecoin-node .
```

## Running the Container

To run the container, use the following command:


```
docker run -d -p 9333:9333 -p 9332:9332 -p 19332:19332 -p 19335:19335 -v litecoin-data:/litecoin -e TESTNET=1 --name litecoin-node litecoin-node
```

This command does the following:

- `-d`: Runs the container in detached mode (in the background).
- `-p`: Exposes the necessary ports for the Litecoin node (9333, 9332, 19332, 19335).
- `-v`: Mounts a volume named `litecoin-data` to the `/litecoin` directory in the container to persist the Litecoin data.
- `-e TESTNET=0`: Sets the environment variable `TESTNET` to `0`, configuring the node to run on the mainnet. Set it to `1` for testnet.
- `--name`: Assigns a name to the container for easy reference.
- `litecoin-node`: Specifies the name of the Docker image to use.

The container will start the Litecoin node and begin syncing with the network. You can access the node's JSON-RPC interface using the exposed ports.

To stop the container, run:

```
docker stop litecoin-node
```

