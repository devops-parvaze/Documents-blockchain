# Testnet

## Connect To AWS Ubuntu Machine

>Connect :: `ssh -i "test-svr-apm.pem" ubuntu@ec2-13-232-199-113.ap-south-1.compute.amazonaws.com`

---

## Clone the Repo
> `git clone --branch https://github.com/polkadot-evm/frontier.git`
>>cd frontier
>>cargo check
>>cargo build
---

## Purge the chain

#### Alice
* `./target/release/frontier-template-node purge-chain --base-path /tmp/alice --chain local` 
---
#### Bob
* `./target/release/frontier-template-node purge-chain --base-path /tmp/bob --chain local`
----
#### Charlie
* `./target/release/frontier-template-node purge-chain --base-path /tmp/charlie --chain local`
----

## Run the testnode

*   ./target/release/frontier-template-node \
	--base-path /tmp/alice \
	--chain local \
	--alice \
	--port 30333 \
	--ws-port 9944 \
	--rpc-port 9933 \
	--node-key 0000000000000000000000000000000000000000000000000000000000000001 \
	--validator \
	--unsafe-rpc-external \
	--unsafe-ws-external \
	--rpc-cors all

----
`--base-path` Specifies the directory for storing all of the data related to this chain.

`--chain local` Specifies the chain specification to use. Valid predefined chain specifications include `local`, `development`, and `staging`.

`--alice` Adds the predefined keys for the alice account to the node's keystore.

`--port 30333` Specifies the port to listen on for peer-to-peer (p2p) traffic

`--rpc-port 9933` Specifies the port on which the server will listen for incoming JSON-RPC traffic via WebSocket and HTTP

`--node-key <key>` Specifies the Ed25519 secret key to use for libp2p networking.

`--validator` Specifies that this node participates in block production and finalization for the network.

`--unsafe-rpc-external` This tag allows external RPC (Remote Procedure Call) connections to your node without enforcing any restrictions

`--unsafe-ws-external` This tag allows external WebSocket connections to your node without restrictions.

`--rpc-cors all` This tag specifies the Cross-Origin Resource Sharing (CORS) policy for the RPC interface

---

*   ./target/release/frontier-template-node \
	--base-path /tmp/bob \
	--chain local \
	--bob \
	--port 30334 \
	--ws-port 9945 \
	--rpc-port 9934 \
	--validator \
	--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp \
	--unsafe-rpc-external \
	--unsafe-ws-external \
	--rpc-cors all

`--bootnodes` The `--bootnodes` option in the command you provided specifies the initial set of bootstrap nodes that your Substrate node will connect to when it starts up

`bootstrap nodes` Provide initial data and help new nodes to synchronize with network.

`Check out Local node identity for -> 12D3KooWGN6mZyMfYSi7wZRfD3JNFYwusnzDa74PWCeW8UNr3Ta2`

---

*   ./target/release/frontier-template-node \
	--base-path /tmp/charlie \
	--chain local \
	--charlie \
	--port 30335 \
	--ws-port 9946 \
	--rpc-port 9935 \
	--validator \
	--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp \
	--unsafe-rpc-external \
	--unsafe-ws-external \
	--rpc-cors all


## Connect To Polkadot Substrate Portal

* Go to `https://polkadot.js.org/apps/#/explorer`
* Select Custom Endpoint -> `ws://13.232.199.113:9944`
* Save and Switch
  
----
  
## Connect To Metamask

* Open Metamask
*  Go to `setting` -> `Networks` -> `Add a Network`
1. Network Name -> `Local Testnet`
2. New RPC URL  -> `http://13.232.199.113:9933`
3. Chain ID -> `42`
4. Currency symbol -> `UNIT`

* Click On `Save`
* Switch to `Local Testnet` in Metamask

  ---


## Add Account and Fund the Account

* Go to `Polkadot Substrate Portal` 
* Click On `Accounts` -> `Address Book` -> `Add contract`
* Copy & Pase `Metamask Account Address` and `add a name`
* Click on `send`
* Give `amount` then `make transfer`

---


## Deploy a `Smart Contract` to our Blockchain

* Go  to -> `https://remix.ethereum.org/`
* Create a `test contract`
  
  
  ```sol
  // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.23;
    contract Test{
        function see()public pure returns (string memory){
            return "Devolved AI";
        }
    }
* Change the `ENVIRONMENT` to `Injected Provider - Metamask` 
* `Deploy` -> `Confirm`

###### _you have successfully deployed a smart contract to test net blockchain_ 