# DatAI
Secure and Private Decentralised Data storage for AI and other usage secured by crypto economic security of ETH PoS
through Eigen Layer

# DatAI Architecture

![image](https://github.com/akshayynft/DatAI/assets/32410489/7aac4ba6-aae3-4c89-8123-d26fa8ea9ac6)

**Several key components:**

**Peer-to-Peer Network:** Utilizes libp2p (or other need to
research) for decentralized communication between nodes.

**Storage Nodes:** Nodes that store data are incentivized using
ETH or Storage Points redeemable with ETH or its smaller
denominations like wei or gwei via Eigen Layer.

**Smart Contracts:** Deployed on Ethereum, these
handle file registration, proof of storage, retrieval requests,
and incentive distribution.

**Client Interface:** A user-friendly frontend built with React.js
for file upload and retrieval.

**Storage Mechanism:**
Users upload files, which are then split into parts/shards and
distributed across storage nodes.

Each shard is associated with a unique cryptographic hash to
ensure data integrity and privacy.

Storage nodes commit to storing these shards and provide
regular proofs of storage.

**Retrieval Mechanism:**
Users request files using the unique hash associated with
their data.
The system retrieves and reassembles the shards from
various nodes to reconstruct the original file.

**Incentive Mechanism:**
Storage providers are rewarded with ETH or points
redeemable with ETH based on the amount of data they store
and their uptime.

Malicious activity or downtime results in slashing of staked
ETH via Eigen Layer, ensuring reliability and trustworthiness
of storage nodes.

## Quick Start

### Dependencies

1. [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
2. [Foundry](https://getfoundry.sh/)
3. [Docker](https://www.docker.com/get-started/)
    3.1 Make sure Docker is running


Following NodeJS packages:
1. tcs
2. ethers

### Steps

#### Typescript

1. Run `yarn install`
2. Run `make start-chain-with-contracts-deployed`
    * This will build the contracts, start an Anvil chain, deploy the contracts to it, and leaves the chain running in the current terminal
3. Open new terminal tab and run `make start-operator`
    * This will compile the AVS software and start monitering new tasks
4. Open new terminal tab and run `make spam-tasks` (Optional)
    * This will spam the AVS with random names every 15 seconds

#### Rust lang


##### Anvil 

1. Run `make start-chain-with-contracts-deployed`
    * This will build the contracts, start an Anvil chain, deploy the contracts to it, and leaves the chain running in the current terminal

2. Run `make start-rust-operator`

3. Run `make spam-rust-tasks`

Tests are supported in anvil only . Make sure to run the 1st command before running the  tests:

```
cargo test --workspace
```


##### Holesky Testnet

| Contract Name               | Holesky Address                                   |
| -------------               | -------------                                     |
| Hello World Service Manager | [0x3361953F4a9628672dCBcDb29e91735fb1985390](https://holesky.etherscan.io/address/0x3361953F4a9628672dCBcDb29e91735fb1985390)    |
| Delegation Manager          | [0xA44151489861Fe9e3055d95adC98FbD462B948e7](https://holesky.etherscan.io/address/0xA44151489861Fe9e3055d95adC98FbD462B948e7)                                           |
| Avs Directory               | [0x055733000064333CaDDbC92763c58BF0192fFeBf](https://holesky.etherscan.io/address/0x055733000064333CaDDbC92763c58BF0192fFeBf)      |

You don't need to run any script for holesky testnet.

1. Use the HOLESKY_ namespace env parameters in the code , instead of normal parameters.

2. Run `make start-rust-operator`

3. Run `make spam-rust-tasks `


## Extensions

- Operator needs a minimum stake amount to make submissions
- Add another strategy to the AVS
- Operator must respond within a certain number of blocks

## Deployment on Holesky

To deploy the Hello World AVS contracts to the Holesky network, follow these steps:

1. Ensure you have the necessary RPC URL and private key for the Holesky network.
2. Run the deployment script using Foundry:
    ```bash
    forge script script/HoleskyDeployer.s.sol:HoleskyDeployer --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast -vvvv
    ```
    Replace `$RPC_URL` with your Holesky RPC URL and `$PRIVATE_KEY` with your private key.

## Adding a New Strategy

To add a new strategy to the Hello World AVS, follow the guide provided in [`AddNewStrategy.md`](https://github.com/Layr-Labs/hello-world-avs/blob/master/AddNewStrategy.md). This guide walks you through the necessary steps to add and whitelist a new strategy for the AVS.
