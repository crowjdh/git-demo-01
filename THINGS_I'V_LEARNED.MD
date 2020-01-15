# Ethereum
## Overview
- Blickchain
  - What it is: Hash-based growing list of blocks, commonly implemented using merkle-tree
  - Why: Data integrity, no double-spending, no central point of failure
  - How: Using public-private cryptography. Using public key as an identity of asset owner and private key as a proof of ownership(right to do action on the asset)
- EVM
  - Public blockchain-based distributed computing platform using smart contract.
- Solidity and smart contract

### Tools
- Ganache, dev env EVM
- Truffle, dev env framework
- Web3, Ethereum api for Javascript

## References
- https://github.com/crowjdh/dapp-tutorial
- https://web3js.readthedocs.io/

# BigchainDB
## Overview
Database backed by MongoDB, communicate between nodes using Tendermint. Application comminucates with BigchainDB using BigchainDB Driver which then propagated to MongoDB.
## 

## References
- https://github.com/crowjdh/bigchaindb-network
- https://www.bigchaindb.com
- https://github.com/bigchaindb/bigchaindb
- https://github.com/tendermint/tendermint/blob/master/docs/networks/docker-compose.md
- http://docs.bigchaindb.com/projects/server/en/latest/simple-deployment-template/index.html
- https://docs.bigchaindb.com/projects/js-driver/en/latest/index.html

# Swarm
## Overview
TODO: Describe purpose, usage and workflow
Used to deploy and manage services on distributed hosts.
- Setup for dev env
  - docker machine
- Jargons
  ### Node
  A Docker daemon. Multiple nodes could run on single physical host(using virtualization or what not), or on physically distributed hosts.
  ### Service
  Same as service we use inside docker compose file format. Equivalent to a container without using scaling(typical way to think what service is), but multiple containers spawned from same service are considered to be a same service.
  ### Stack
  Group of services. You can think this as a whole application afchitecture, taking scaling into consideration.
  ### Manager node
  Nodes which manages worker nodes in swarm and manages stacks. It can also be a worker node at the same time.
  ### Worker node
  Pretty much what it says.

- Commands
  - docker node: Manage nodes in swarm
    - ls: List nodes
    - ps: List processes running on certain node. Current node by default.
    - update
      - --availability: active/pause/drain(See [here](https://docs.docker.com/engine/swarm/manage-nodes/#list-nodes))
      - --role: Manager/Worker
  - docker service: Manage a service in swarm
    - ls: List services running on swarm(not a current host)
    - ps: List the tasks of one or more services
    - update: Update a single service. Useful for updating a service with newer image.
    - rollback: Revert changes to a service's configuration
    - scale: Scale one or multiple replicated services
  - docker stack
    - deploy: Deploy a new stack or update an existing stack
    - ls: List stacks
    - ps: List the tasks in the stack
    - rm: Remove one or more stacks
    - services: List the services in the stack

## Stack, Service and container
<table>
    <thead>
        <tr>
            <th colspan=2></th>
            <th><i>dist-web</i> Stack</th>
            <th>Node</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4>Services</td>
            <td>Curl service</td>
            <td>dist-web_curl.1</td>
            <td>host3</td>
        </tr>
        <tr>
            <td rowspan=3>Web services</td>
            <td>dist-web_web.1</td>
            <td>host3</td>
        </tr>
        <tr>
            <td>dist-web_web.2</td>
            <td>host2</td>
        </tr>
        <tr>
            <td>dist-web_web.3</td>
            <td>host1</td>
        </tr>
    </tbody>
</table>

## Ingress routing mash
<img src="https://docs.docker.com/engine/swarm/images/ingress-routing-mesh.png"/>

## References
- https://github.com/crowjdh/simple-swarm-webserver
- https://docs.docker.com/engine/swarm/
