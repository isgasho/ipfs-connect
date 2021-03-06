# ipfs-connector

Using the IPFS to transfer files between computers can be slow because it can take time to locate a path between the two computers on the IPFS network. This makes it faster by lowering the barrier towards making sure your computers are in each other's swarm.

First run the IPFS daemon on your computers

```
$ ipfs daemon
```

Then get `ipfs-connect` using `go`:

```
$ go get github.com/schollz/ipfs-connect
```

Then connect the two computers. On the first computer type:

```
$ ipfs-connect mycomps
your id: jkljl88-ji98-449-a0e1-c87a04802922
add another computer to your swarm by running

ipfs-connect mycomps
```

And then on the other computer type

```
$ ipfs-connect mycomps
```

And then, voila! Your computers will be swarmed together as long as the IP addresses don't change. Now you can share files via IPFS between two computers without waiting.

## How does it work?

This uses a simple rendezvous server: [schollz/duct](https://github.com/schollz/duct) which is a ephemeral MPMC pubsub. Both computers connect to the duct tape server and listen for a payload about their IPFS addresses. Once they receive the addresses they connect to them via the `ipfs swarm connect` command.

## License 

MIT
