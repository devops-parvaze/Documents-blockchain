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



./target/release/argochain build-spec --disable-default-bootnode --chain local > customSpec.json

./target/release/argochain build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json

=========================================================================================================================

Validator 1

./target/release/argochain key insert --base-path /tmp/node01 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x7ae27e518f00149afd165556e16a9481e8863255d193ff477e85ef234d71351d \
  --password-interactive \
  --key-type babe

# Key password: prg@12345

./target/release/argochain key insert --base-path /tmp/node01 \
  --chain customSpecRaw.json \
  --scheme Ed25519 \
  --suri 0x69ee05fcb57b435274f2059fae4f7137af04aa2c44c1f4ef3f40764d4b07d1ea \
  --password-interactive \
  --key-type gran


# Key password: prg@12345

./target/release/argochain key insert --base-path /tmp/node01 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x98bf81a45cbaebd4d67e29ba8b7020a34aeb1948e5e9f95fb0319cff2c833c2e \
  --password-interactive \
  --key-type imon

# Key password: prg@12345

./target/release/argochain key insert --base-path /tmp/node01 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x943b5383c7283486f545951c008df74877d00b32397005725e0b5a6459a5b15f \
  --password-interactive \
  --key-type audi

# Key password: prg@12345


## Start the node from below command with your modifications

./target/release/argochain \
  --base-path /tmp/node01 \
  --chain customSpecRaw.json \
  --port 30333 \
  --rpc-port 9945 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode01 \
  --password-interactive

Local ID: 12D3KooWD2gJpHTGU6EAwNap7Sc1mBDfkhL7jseoqt8uQ8hZtSr5

==========================================================================================

Validator 2

./target/release/argochain key insert --base-path /tmp/node02 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x94449c12bbc88976523cc7e05260ddab11b4e6d147e0b307eb0fdbce87abca57 \
  --password-interactive \
  --key-type babe

# Key password: prg@12345

./target/release/argochain key insert --base-path /tmp/node02 \
  --chain customSpecRaw.json \
  --scheme Ed25519 \
  --suri 0xed2f47402aa399ada0f6592e0158d0e03d2006e392d7f1811acf1918cf974775 \
  --password-interactive \
  --key-type gran

# Key password: prg@12345

./target/release/argochain key insert --base-path /tmp/node02 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x487fcfb14065024f5b7305d824ec32a6abd9d8618eaac2f603373164b7d3f101 \
  --password-interactive \
  --key-type imon

# Key password: prg@12345

./target/release/argochain key insert --base-path /tmp/node02 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x04cac9b1caa5a9ed406f6ddca0739f2693a78934414b555618df1ee9b6b68833 \
  --password-interactive \
  --key-type audi

# Key password: prg@12345

## Start the node from below command with your modifications

./target/release/argochain \
  --base-path /tmp/node02 \
  --chain customSpecRaw.json \
  --port 30334 \
  --rpc-port 9946 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode02 \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWD2gJpHTGU6EAwNap7Sc1mBDfkhL7jseoqt8uQ8hZtSr5

==========================================================================================================

Validator 3

./target/release/argochain key insert --base-path /tmp/node03 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x02aa2b9e764a0d5d0e16dec316ea9225307c6ff071d2eb0efde0b34d0e007b35 \
  --password-interactive \
  --key-type babe

./target/release/argochain key insert --base-path /tmp/node03 \
  --chain customSpecRaw.json \
  --scheme Ed25519 \
  --suri 0x864cf32b202a45624a430257a0ab6aa2fe019eef02a76335bd3c8c2489c41424 \
  --password-interactive \
  --key-type gran

./target/release/argochain key insert --base-path /tmp/node03 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x78aade2f6c62d199f72ad16c2ea01fb1c2fdd44fdd41fec968cce873088d3942 \
  --password-interactive \
  --key-type imon

./target/release/argochain key insert --base-path /tmp/node03 \
  --chain customSpecRaw.json \
  --scheme Sr25519 \
  --suri 0x727811cac07909a614a661d0b94e83c2bf12ef63ab234e0943f85c939c808f55 \
  --password-interactive \
  --key-type audi

## Start the node from below command with your modifications

./target/release/argochain \
  --base-path /tmp/node03 \
  --chain customSpecRaw.json \
  --port 30335 \
  --rpc-port 9947 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode03 \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWD2gJpHTGU6EAwNap7Sc1mBDfkhL7jseoqt8uQ8hZtSr5


