## Install the Ubuntu Advanced Packaging Tool
  ```
  sudo apt install build-essential
  ```
## At a minimum, you need the following packages before you install Rust:
```
  clang curl git make
  ````
## Install required packages and Rust
```
sudo apt install --assume-yes git clang curl libssl-dev protobuf-compiler
```

## Download the rustup installation program and use it to install Rust by running the following command:
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## Update your current shell to include Cargo by running the following command:
```
source $HOME/.cargo/env
```

## Verify your installation by running the following command:
```
rustc --version
```
## Configure the Rust toolchain to default to the latest stable version by running the following commands:
```
rustup default stable
rustup update
```
## Add the nightly release and the nightly WebAssembly (wasm) targets to your development environment by running the following commands:
```
rustup update nightly
rustup target add wasm32-unknown-unknown --toolchain nightly
```
## Verify the configuration of your development environment by running the following command:
```
rustup show
rustup +nightly show
```

## The command displays output similar to the following:
```
# rustup show

active toolchain
----------------

stable-x86_64-unknown-linux-gnu (default)
rustc 1.62.1 (e092d0b6b 2022-07-16)

# rustup +nightly show

active toolchain
----------------

nightly-x86_64-unknown-linux-gnu (overridden by +toolchain on the command line)
rustc 1.65.0-nightly (34a6cae28 2022-08-09)
```
## Compile a Substrate node Clone the node template repository by running the following command:
```
git clone https://github.com/mitun567/Argochain.git
```
## Change to the root of the node template directory by running the following command:
```
cd Argochain/
```
## Compile the node template by running the following command:
```
cargo build --release
```
## Run the testnode
```
  nohup ./target/release/frontier-template-node \
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
	--rpc-cors all &
```
## How to stop and Restart
show port stat: 
```
netstat -tulup
```
Show specific process based on port: 
```
lsof -i :<port number>
EX: lsof -i :30333
```
Show process based on Process iD: 
```
process -p <PID>
EX: process -p 152436
```
Kill process on running specific port 
```
lsof -ti : <port number> | xargs kill 
EX: lsof -ti :30333 | xargs kill
```
Purge the chain
Restart with Run the Test Node Command

